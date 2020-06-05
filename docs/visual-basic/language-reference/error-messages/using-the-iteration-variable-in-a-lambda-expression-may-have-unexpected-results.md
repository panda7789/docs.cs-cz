---
title: Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: aa3e1d6281af22b301a4697b265ed3fbf23e3de4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373911"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
Použití proměnné iterace ve výrazu lambda může mít neočekávané výsledky. Místo toho vytvořte v rámci smyčky místní proměnnou a přiřaďte jí hodnotu proměnné iterace.  
  
 Toto upozornění se zobrazí, pokud použijete proměnnou iterace smyčky ve výrazu lambda, který je deklarován uvnitř smyčky. Například následující příklad způsobí, že se zobrazí upozornění.  
  
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
  
 `For`Smyčka vytvoří pole výrazů lambda, z nichž každá vrátí hodnotu proměnné iterace smyčky `i` . Pokud jsou výrazy lambda vyhodnocovány ve `For Each` smyčce, možná očekáváte, že se zobrazí 0, 1, 2, 3 a 4, po sobě jdoucí hodnoty `i` ve `For` smyčce. Místo toho se zobrazí poslední `i` zobrazená hodnota pětkrát:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42324  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přiřaďte hodnotu proměnné iterace místní proměnné a použijte místní proměnnou ve výrazu lambda.  
  
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

- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
