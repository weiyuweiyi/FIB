;# FIB
;The Fibonacci sequence is calculated in assembly language
data segment
	num db 5
	result db ?
data ends

code segment
main proc far
	assume cs:code,ds:data
start:
	mov ax,data
	mov ds,ax
	mov cl,num
	cmp cl,1
	jnz next
	mov result,1
	jmp exit
next:cmp cx,2
	jnz lp
	mov result,1
	jmp exit
lp:mov al,1
	mov bl,1
	call FIB
	mov result,bl
	mov ah,4ch
	int 21h
FIB proc near
	add al,bl
	xchg al,bl
	dec cl
	cmp cl,2
	jz exit
	call FIB
exit:ret
FIB endp
main endp
code ends
end start
