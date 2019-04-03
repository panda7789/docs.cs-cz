---
title: Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 618fc88a2ca92ec911a3fbd82de580403d924430
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841093"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
Použití proměnné iterace ve výrazu lambda může mít neočekávané výsledky. Místo toho vytvořte v cyklu lokální proměnnou a přiřaďte jí hodnotu proměnné iterace.  
  
 Toto upozornění se zobrazí při použití proměnné iterace smyčky ve výrazu lambda, který je deklarován uvnitř smyčky. Například následující příklad způsobí upozornění se zobrazí.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 Následující příklad ukazuje neočekávané výsledky, které mohou nastat.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 `For` Smyčky je vytvořeno pole výrazů lambda, z nichž každý vrátí hodnotu proměnné iterace smyčky `i`. Když jsou lambda výrazy vyhodnocovány v `For Each` smyčky, můžete očekávat, že naleznete v tématu 0, 1, 2, 3 a 4 zobrazí po sobě jdoucích hodnot `i` v `For` smyčky. Místo toho uvidíte konečná hodnota `i` zobrazí pětkrát:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42324  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přiřadit hodnotu proměnné iterace na místní proměnnou a použijte místní proměnnou ve výrazu lambda.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
