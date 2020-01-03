.data
	message: .asciiz "Max is: "
	blank: .asciiz " "
	newLine: .asciiz "\n"
	fillArray: .word 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 # temp array that we will fill
	
	mdArray: .word 3, 8, 2, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 # 2d array hoolds all arrays
			 .word 5, 1, 2, 3, 4, 5, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 4, 6, 7, 2, 1, 7, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 1, 3, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 7, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 7, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 7, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 7, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 7, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
			 .word 7, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0

	.eqv size_col 21 # column 21
	.eqv size_row 10 # row 5
	.eqv total_data 210 # item number in 2d array 

.text
	main:
		addi $t0, $zero, 0 # i = 0
		addi $t1, $zero, 0 # j = 0
		addi $t2, $zero, 0 # flag = 0
		addi $t3, $zero, 0 # maxindex = 0
		la $s0, mdArray # int max = arr[0][0]
		lw $t4, ($s0) # int max = arr[0][0] 
		li $k0, 0
		li $s7, 0
	findmax:
		
		iffin: beq $s7, size_row, exitfin
		addi $s7, $s7, 1
		loop1: beq $t0, size_row, exit
		    	addi $t6, $s0, 84    
		    	lw $t7, ($t6)		    	 
			    slt $t8, $t4, $t7 # max < arr[i][0]
			   if: beq $t8, 1, changemax # max = arr1[i][0]
			   		bne $t8, 1, increasei # i++
			   		j loop1
		exit:
			li $v0, 4
			la $a0, newLine
			syscall
			li $t0, 0
			li $v0, 4
			la $a0, message
			syscall
	 		move $a0, $t4
	 		li $v0, 1 # print the max number
	 		syscall
	 		li $v0, 4
			la $a0, newLine
			syscall
			
	insertArray:
			addi $t5, $zero, 0
			la $s0, mdArray # address of mdArray
			la $s1, fillArray #address of fillarray
			mul $t9, $t9, 4
			addi $t9, $t9, 4 # fillArray[1]
			add $s1, $s1, $t9
			lw $t9, ($s1) # t9 = fillArray[1]
			la $s2, fillArray # address of fillarray
			lw $k1, ($s2) #k1 = fillarray[0]
			mul $t5, $t3, size_col
			mul $t5, $t5, 4
			addi $t5, $t5, 4  # 40
			add $s0, $s0, $t5 # address of mdarray+40
			lw $s3, ($s0) # s3 = mdArray [1][1]
			
	 		loop2: 	beq $t2, 20, exit2
	 				#bne $t2, 7, insertnumber
	 				la $s5, fillArray
					addi $s5, $s5, 4
					lw $t9, ($s5)
	 				 jal srchlp
	 				ifbeq:beq $t8, 1, increaset2
	 						beq $t8, 0,insertnumber 

	 		exit2:
	 			addi $t1, $zero, 0
	 			la $a3, fillArray
	 			loop3: beq $t1, size_col, exit3
	 				lw $a2, ($a3)
	 				move $a0, $a2
	 				li $v0, 1
	 				syscall
	 				li $v0, 4
	 				la $a0, blank
	 				syscall
	 				addi $a3, $a3, 4
	 				lw $a2, ($a3)
	 				addi $t1, $t1, 1
	 				j loop3
	 			exit3:
	 				la $s0, mdArray # address of mdArray
	 				mul $t5, $t3, size_col
					mul $t5, $t5, 4
					add $s0, $s0, $t5 # address of mdarray+40
					lw $s3, ($s0)
					addi $s3, $zero, 0
					sw $s3, ($s0)
					la $s0, mdArray
					lw $t4, ($s0) # int max = arr[0][0]
					li $t2, 0
					li $t3, 0
	 				j findmax
	 
	 increaset2:
	 		addi $t2, $t2, 1		
	 		addi $s0, $s0, 4
			lw $s3, ($s0)
	 		li $t8, 0
	 		j loop2
	 		
	 insertnumber:
	 		addi $s4, $s3, 0
			addi $t9, $s3, 0
			sw $t9 ($s5)
			addi $s1, $s1, 4 # fillArray[1]
			lw $t9, ($s1) # t9 = fillArray[1]
			addi $s0, $s0, 4
			lw $s3, ($s0)
			addi $t2, $t2, 1
			li $t8, 0
			ifk1: beq $s4, 0, dinc
					bne $s4, 0, inc
	
	dinc:
		j loop2
	inc:
		addi $k1, $k1, 1
		sw $k1, ($s2)
	 	j loop2
	
	srchlp:
		beq $t9, $zero, srchdn
		seq $k0, $t9, $s3
		bgt $k0, $zero, exitsrch
		addi $s5, $s5, 4
		lw $t9, ($s5)
		b srchlp
	srchdn:
		li $t8, 0	
		j ifbeq
	exitsrch:		
		li $t8, 1
		j ifbeq
		
	changemax:
			addi $t4, $t7, 0
			addi $t3, $t0, 1 # max = arr[i][0]
		  	addi $t0, $t0, 1 # i++
		  	addi $s0, $s0, 84
		  	j loop1
	increasei:
			addi $t0, $t0, 1 # i++
			addi $s0, $s0, 84
			j loop1  
		  
	exitfin:
		li $v0, 10
		syscall	  
