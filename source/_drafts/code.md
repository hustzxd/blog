---
title: code
tags:
---
```python
 if autograd.is_training() and status == 0:
            # At the very first quantization step, we find an approximate optimal scale.
            with autograd.pause():
                zeros_delta = F.zeros_like(scale)
                for j in range(-2, 4):
                    div_factor = 2 ** j
                    for i in range(100):
                        now_error = l2_error(F, tran_weight, self.nbits, scale)
                        right_error = l2_error(F, tran_weight, self.nbits, \
                            scale + self.delta / div_factory)
                        g = F.greater(right_error - now_error, 0)
                        delta = F.where(g, zeros_delta + self.delta / div_factor,
                                        zeros_delta - self.delta / div_factor)
                        scale -= delta
                status += 1
```
```vb
'                             Online VB Compiler.
'                 Code, Compile, Run and Debug VB program online.
' Write your code in this editor and press "Run" button to execute it.


Module VBModule
    Sub Main()
        Dim str As String
        Dim i, length, left, right, mid, result As Integer
        length = 6
        Dim dst As Integer
        dst = Integer.Parse("5")
        Dim int_arr(length) As Integer 
        str = "1,2,3,4,5,6" 
        Dim str_arr = str.split(",")
        For i = 0 To (length - 1)
            int_arr(i) = Integer.Parse(str_arr(i))
        Next i
        left = 0
        right = length - 1
        mid = CInt((left + right) / 2)
        Console.WriteLine(int_arr(mid))
        result = -1

        While left <= right
            mid = (left + right) / 2
            If int_arr[mid] < dst Then
                left = mid + 1
            ElseIf int_arr[mid] > dst Then
                right = mid
            Else
                result = right
                ' Wend
            End If
        End While
        Console.WriteLine(result)
    End Sub
End Module
```
$$
\eta_t = \eta_{min} + \frac{1}{2}(\eta_{max} - \eta_{min})(1 +
        \cos(\frac{T_{cur}}{T_{max}}\pi))
$$
赵宪栋