---
title: Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 7144a5fd4a197fddaf1ac4132df0ff70995ad067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594159"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
Použití proměnné iterace ve výrazu lambda může mít neočekávané výsledky. Místo toho vytvořte místní proměnné v rámci smyčky a přiřaďte ho hodnotu proměnné iterace.  
  
 Toto upozornění se zobrazí v případě použití proměnné iterace smyčky ve výrazu lambda, který je deklarován uvnitř smyčky. Například v následujícím příkladu způsobí, že se objeví upozornění.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 Následující příklad ukazuje neočekávané výsledky, které můžou nastat.  
  
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
  
 `For` Smyčky vytvoří pole výrazů lambda, z nichž každý vrátí hodnotu proměnné iterace smyčky `i`. V jsou-li výrazy lambda `For Each` smyčku, můžete očekávat, že najdete v části 0, 1, 2, 3 a 4 zobrazí, následných hodnoty `i` v `For` smyčky. Místo toho uvidíte konečná hodnota `i` zobrazí pětkrát:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42324  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přiřadit hodnotu proměnné iterace místní proměnné a pomocí místní proměnné ve výrazu lambda.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
