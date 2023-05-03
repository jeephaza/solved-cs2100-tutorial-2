Download Link: https://assignmentchef.com/product/solved-cs2100-tutorial-2
<br>
<h1>D1. Exploration: C to MIPS</h1>




Go to this website <a href="https://godbolt.org/">https://godbolt.org/</a> and copy the C code below into the left box, and ensure that you choose “C” in the dropdown list in green in the screenshot after the C code, and choose MIPS gcc 5.4 (el) or MIPS gcc 5.4 in the dropdown list circled red. (do not choose MIPS64 gcc 5.4 or MIPS64 gcc 5.4 (el):

<table width="603">

 <tbody>

  <tr>

   <td width="603"><strong>int main(void) {    int a, b, c; </strong><strong>    a = 3;    b = 5;    c = a + b;    return 0; </strong><strong>} </strong></td>

  </tr>

 </tbody>

</table>




The following is extracted from the Assembly output.

<table width="607">

 <tbody>

  <tr>

   <td width="42">  </td>

   <td colspan="2" width="183">addiu $sp,$sp,-32 sw $fp,28($sp)</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">move</td>

   <td width="122">$fp,$sp</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">li</td>

   <td width="122">$2,3</td>

   <td width="61"> </td>

   <td width="321"># 0x3</td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">sw</td>

   <td width="122">$2,8($fp)</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">movz</td>

   <td width="122">$31,$31,$0</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">li</td>

   <td width="122">$2,5</td>

   <td width="61"> </td>

   <td width="321"># 0x5</td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">sw</td>

   <td width="122">$2,12($fp)</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">lw</td>

   <td width="122">$3,8($fp)</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">lw</td>

   <td width="122">$2,12($fp)</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42">  </td>

   <td width="61">nop addu</td>

   <td width="122">$2,$3,$2</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">sw</td>

   <td width="122">$2,16($fp)</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">move</td>

   <td width="122">$2,$0</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42"> </td>

   <td width="61">move</td>

   <td width="122">$sp,$fp</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

  <tr>

   <td width="42">    </td>

   <td colspan="2" width="183">lw      $fp,28($sp)addiu $sp,$sp,32j      $31nop</td>

   <td width="61"> </td>

   <td width="321"> </td>

  </tr>

 </tbody>

</table>

We covered <strong>sw</strong>, <strong>lw</strong> and <strong>j</strong> in lecture, but not the rest. Find out what they are. (Note: <strong>li</strong> will be used in the labs later and <strong>nop</strong> will be mentioned in the topic on Pipelining. <strong>move</strong>, like <strong>li</strong>, is a pseudoinstruction. <strong>$sp</strong>, <strong>$fp</strong>, <strong>movz</strong>,<strong> addiu</strong>, and <strong>addu</strong> are not in the syllabus.)




D2. For each of the following instructions, indicate if it is valid or not. If not, explain why and suggest a correction. Note that the | in (d) is the bitwise OR operation.

<ol>

 <li><strong>add $t1, $t2, $t3         </strong># $t3 = $t1 + $t2</li>

 <li><strong>addi $t1, $0, 0x25     </strong># $t1 = 0x25</li>

 <li><strong>subi $t2, $t1, 3     </strong># $t2 = $t1 – 3</li>

 <li><strong>ori $t3, $t4, 0xAC120000  </strong># $t3 = $t4 | 0xAC120000</li>

 <li><strong>sll $t5, $t2, 0x21        </strong># shift left $t2 33 bits and store in $t5</li>

</ol>







<h1>1.       Bitwise operations</h1>

Find out about the following bitwise operations in C and explain and illustrate each of them with an example.

|       (bitwise OR)

&amp;      (bitwise AND)

^      (bitwise XOR)

~       (one’s complement)

&lt;&lt;  (left shift)

&gt;&gt;  (right shift)

You may use the following code template for your illustration. Variables of the data type <strong>char</strong> take up 8 bits of memory.

<table width="621">

 <tbody>

  <tr>

   <td width="621"><strong>#include &lt;stdio.h&gt; </strong><strong> </strong><strong>typedef unsigned char byte_t; </strong><strong> </strong><strong>void printByte(byte_t); </strong><strong> </strong><strong>int main(void) {  byte_t a, b; </strong><strong> </strong><strong> a = 5;  b = 22; </strong><strong> printf(“a    = “); printByte(a);    printf(“
”);  printf(“b    = “); printByte(b);    printf(“
”);  printf(“a|b  = “); printByte(a|b);  printf(“
”);  return 0; </strong><strong>}  </strong><strong>void printByte(byte_t x) {  printf(“%c%c%c%c%c%c%c%c”,         (x &amp; 0x80 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x40 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x20 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x10 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x08 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x04 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x02 ? ‘1’: ‘0’), </strong><strong>        (x &amp; 0x01 ? ‘1’: ‘0’)); } </strong></td>

  </tr>

 </tbody>

</table>










<h1>2.       Swapping</h1>

We have discussed in lecture how to swap two variables in a function:

<table width="621">

 <tbody>

  <tr>

   <td width="621"><strong>void swap(int *a, int *b) { </strong><strong> int t = *a;  *a = *b; </strong><strong> *b = t; </strong><strong>} </strong></td>

  </tr>

 </tbody>

</table>

In the above code, a temporary variable <strong>t</strong> is used.

A possible alternative is to use some bitwise operator to perform the swap, <u>without using any</u> <u>temporary variable</u>. Write a function to do this.

<h1>3.      MIPS Bitwise Operations</h1>




Implement the following in MIPS assembly. Assume that variables <strong>a</strong>, <strong>b</strong> and <strong>c</strong> are mapped to registers $s0, $s1 and $s2 respectively. Each part is independent of all the other parts.  <strong>For bitwise instructions (e.g. and, or, andi, etc), </strong>any immediate values you use can only be shown in binary. This is optional for non-bitwise instructions (e.g. addi, etc).




Note that bit 31 is the most significant bit (MSB) on the left, and bit 0 is the least significant bit (LSB) on the right, i..e.:




<table width="576">

 <tbody>

  <tr>

   <td width="84">MSB</td>

   <td width="82"> </td>

   <td width="83"> </td>

   <td width="161"> </td>

   <td width="82"> </td>

   <td width="83">LSB</td>

  </tr>

  <tr>

   <td width="84">Bit 31</td>

   <td width="82">Bit 30</td>

   <td width="83">Bit 29</td>

   <td width="161">…</td>

   <td width="82">Bit 1</td>

   <td width="83">Bit 0</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<ol>

 <li>Set bits 2, 8, 9, 14 and 16 of <strong>b</strong> to 1. Leave all other bits unchanged.</li>

</ol>




<ol>

 <li>Copy over bits 1, 3 and 7 of <strong>b</strong> into <strong>a</strong>, without changing any other bits of <strong>a</strong>.</li>

</ol>




<ol>

 <li>Make bits 2, 4 and 8 of <strong>c</strong> the inverse of bits 1, 3 and 7 of <strong>b</strong> (i.e. if bit 1 of <strong>b</strong> is 0, then bit 2 of <strong>c</strong> should be 1; if bit 1 of <strong>b</strong> is 1, then bit 2 of <strong>c</strong> should be 0), without changing any other bits of <strong>c</strong>.</li>

</ol>







<h1>4.      MIPS Arithmetic</h1>

Write the following in MIPS Assembly, using as few instructions as possible. You may rewrite expressions to minimize the number of instructions used. In all parts you can assume that variables <strong>a</strong>, <strong>b</strong>, <strong>c</strong> and <strong>d</strong> are mapped to registers $s0, $s1, $s2 and $s3 respectively. Each part is independent of the others.




<ol>

 <li>c = a + b</li>

</ol>




<ol>

 <li>d = a + b – c</li>

</ol>




<ol>

 <li>c = 2b + (a – 2)</li>

</ol>




<ol>

 <li>d = 6a + 3(b – 2c)</li>

</ol>




<ol start="5">

 <li>[AY2013/14 Semester 2 Exam]</li>

</ol>

The mysterious MIPS code below assumes that <strong>$s0 is a 31-bit binary sequence</strong>, i.e. the MSB (most significant bit) of <strong>$s0</strong> is assumed to be zero at the start of the code.

<table width="527">

 <tbody>

  <tr>

   <td width="250"><strong>     add  $t0, $s0, $zero      lui  $t1, 0x8000 </strong><strong>lp:</strong><strong> beq  $t0, $zero, </strong><strong>e </strong><strong>     andi $t2, $t0, 1      beq  $t2, $zero, </strong><strong>s</strong><strong>      xor  $s0, $s0, $t1 </strong><strong>s:</strong><strong> srl  $t0, $t0, 1      j    </strong><strong>lp</strong> <strong>e:</strong></td>

   <td width="277"># make a copy of $s0 in $t0</td>

  </tr>

 </tbody>

</table>

<ol>

 <li>For each of the following initial values in register <strong>$s0</strong> at the beginning of the code, give the hexadecimal value of the content in register $<strong>s0</strong> at the end of the code.</li>

 <li>Decimal value <strong>31</strong>.            ii.         Hexadecimal value <strong>0x0AAAAAAA</strong>.</li>

</ol>




<ol>

 <li>Explain the purpose of the code in one sentence.</li>

</ol>








