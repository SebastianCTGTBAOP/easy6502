---
layout: basic
---

<h2>Simulator</h2>

To use the disassembler, click **Assemble**, then **Disassemble**. [Back to Easy 6502](index.html).

{% include start.html %}
Initialise:
	ldx #$01
	stx $02
	define text_colour $02
	lda text_colour
	
	ldx #$00
	stx $00
	ldx #$02
	stx $01
	ldx #0

DrawText:
	jsr DrawA
	jsr DrawB
	jsr DrawC
	jsr DrawD
	jsr DrawE
	jsr DrawF
	jsr DrawG
	jsr SetLine2
	jsr DrawH
	jsr DrawI
	jsr DrawJ
	jsr DrawK
	jsr DrawA
	jsr DrawA
	jsr SetLine3
	jsr DrawA
	jsr DrawA
	jsr DrawA
	jsr DrawA
	jsr DrawA
	jsr DrawA
	jsr DrawA
	jsr SetLine4
	jsr DrawA
	jsr DrawA
	jsr DrawA
	jsr SetLine5
	jsr DrawA
	jsr DrawA
	jsr DrawA

	BRK

DrawA:
	jsr Draw3Dot
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw3Dot
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw2DotMSpace

	jsr ReadjustFor3

	rts

DrawB:
	jsr Draw3Dot
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw4Dot
	jsr CNewLine
	jsr Draw2DotM2Space
	jsr CNewLine
	jsr Draw4Dot
	
	jsr ReadjustFor4

	rts

DrawC:
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr Draw3Dot

	jsr ReadjustFor3

	rts

DrawD:
	jsr Draw4Dot
	jsr CNewLine
	jsr DrawSpaceDotSpaceDot
	jsr CNewLine
	jsr DrawSpaceDotSpaceDot
	jsr CNewLine
	jsr DrawSpaceDotSpaceDot
	jsr CNewLine
	jsr Draw4Dot

	jsr ReadjustFor4

	rts

DrawE:
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr Draw3Dot

	jsr ReadjustFor3

	rts

DrawF:
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawLeftDot

	jsr ReadjustFor3

	rts

DrawG:
	jsr Draw4Dot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawDotSpaceDotDot
	jsr CNewLine
	jsr Draw2DotM2Space
	jsr CNewLine
	jsr Draw4Dot

	jsr ReadjustFor4

	rts

DrawH:
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw3Dot
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw2DotMSpace

	jsr ReadjustFor3

	rts

DrawI:
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawMiddleDot
	jsr CNewLine
	jsr DrawMiddleDot
	jsr CNewLine
	jsr DrawMiddleDot
	jsr CNewLine
	jsr Draw3Dot

	jsr ReadjustFor3

	rts
DrawJ:
	jsr Draw3Dot
	jsr CNewLine
	jsr DrawMiddleDot
	jsr CNewLine
	jsr DrawMiddleDot
	jsr CNewLine
	jsr DrawMiddleDot
	jsr CNewLine
	jsr DrawDotDotSpace

	jsr ReadjustFor3

	rts
DrawK:
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr DrawDotDotSpace
	jsr CNewLine
	jsr Draw2DotMSpace
	jsr CNewLine
	jsr Draw2DotMSpace

	jsr ReadjustFor3

	rts

DrawL:
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr DrawLeftDot
	jsr CNewLine
	jsr Draw3Dot

	jsr ReadjustFor3

	rts

DrawM:
	rts
DrawN:
	rts
DrawN:
	rts
DrawO:
	rts
DrawP:
	rts
DrawQ:
	rts
DrawR:
	rts
DrawS:
	rts
DrawT:
	rts
DrawU:
	rts
DrawV:
	rts
DrawW:
	rts
DrawX:
	rts
DrawY:
	rts
DrawZ:
	rts

Draw3Dot:
	lda text_colour
	sta ($00,x)

	ldy $00	
	iny
	sty $00
	sta ($00,x)

	iny
	sty $00
	sta ($00,x)

	jsr DecrementYBy2
	clc

	rts

Draw4Dot:
	lda text_colour
	sta ($00,x)

	ldy $00	
	iny
	sty $00
	sta ($00,x)

	iny
	sty $00
	sta ($00,x)

	iny
	sty $00
	sta ($00,x)

	jsr DecrementYBy3
	clc

	rts

Draw2DotMSpace:
	lda text_colour
	sta ($00,x)

	ldy $00
	iny
	iny
	sty $00
	sta ($00,x)

	jsr DecrementYBy2
	clc
	
	rts

Draw2DotM2Space:
	lda text_colour
	sta ($00,x)

	ldy $00
	iny
	iny
	iny
	sty $00
	sta ($00,x)

	jsr DecrementYBy3
	clc
	
	rts

DrawLeftDot:
	lda text_colour
	sta ($00,x)
	clc

	rts

DrawSpaceDotSpaceDot:
	lda text_colour
	
	ldy $00
	iny
	sty $00
	sta ($00,x)

	iny
	iny
	sty $00
	sta ($00,x)

	jsr DecrementYBy3
	clc
	
	rts

DrawDotSpaceDotDot:
	lda text_colour
	
	sta ($00,x)

	ldy $00
	iny
	iny
	sty $00
	sta ($00,x)

	iny
	sty $00
	sta ($00,x)

	jsr DecrementYBy3
	clc
	
	rts

DrawDotDotSpace:
	lda text_colour
	
	sta ($00,x)

	ldy $00
	iny
	sty $00
	sta ($00,x)

	dey
	clc
	
	rts

DrawMiddleDot:
	lda text_colour
	
	ldy $00
	iny
	sty $00
	sta ($00,x)

	dey
	clc
	
	rts

DecrementYBy2:
	dey
	dey

	sty $00
	clc

	rts

DecrementYBy3:
	dey
	dey
	dey

	sty $00
	clc
	rts

CNewLine:
	clc
	tya
	adc #$20
	sta $00
	tay
	
	ora #%0001111
	cmp #%0001111
	beq SetNewSpaceForward
	clc

	lda text_colour
	ldx #0

	rts

SetNewSpaceForward:
	ldx $01
	inx
	stx $01
	ldx #0
	clc

	rts

ReadjustFor3:
	iny
	iny
	iny
	iny
	tya

	jsr Subtract

	tay
	sta $00

	ldx #0
	lda text_colour
	clc

	rts

ReadjustFor4:
	iny
	iny
	iny
	iny
	iny
	tya

	jsr Subtract

	tay
	sta $00

	ldx #0
	lda text_colour
	clc

	rts

Subtract:
	clc
    	sbc #$7f
	bcc ReturnToOldSpace

	ldx #0

	rts

ReturnToOldSpace:
	ldx $01
	dex
	stx $01
	ldx #0
	clc

	rts

SetLine2:
	ldx #$c0
	stx $00
	ldx #0
	clc

	rts

SetLine3:
	ldx #$03
	stx $01
	ldx #$80
	stx $00
	ldx #0
	clc

	rts

SetLine4:
	ldx #$04
	stx $01
	ldx #$40
	stx $00
	ldx #0
	clc

	rts

SetLine5:
	ldx #$05
	stx $01
	ldx #$00
	stx $00
	ldx #0
	clc
  dcb $d
{% include end.html %}
