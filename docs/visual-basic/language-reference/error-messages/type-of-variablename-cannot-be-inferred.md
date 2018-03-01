---
title: "Typ & č. 39; &lt;NázevProměnné&gt;& č. 39; nelze odvodit, protože hranice smyčky a proměnná krok není rozšíří do stejného typu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ & č. 39; &lt;NázevProměnné&gt;& č. 39; nelze odvodit, protože hranice smyčky a proměnná krok není rozšíří do stejného typu
Jste napsali `For...Next` smyčky, ve kterém kompilátor nelze odvodit typ dat pro řídicí proměnná smyčky vzhledem k tomu, že jsou splněné následující podmínky:  
  
-   Datový typ řídicí proměnná smyčky není zadaný s `As` klauzule.  
  
-   Rozsah smyčky a proměnnou krok obsahovat aspoň dva datové typy.  
  
-   Neexistují žádné standardní převody mezi datovými typy.  
  
 Kompilátor proto nelze odvodit typ dat řídicí proměnná.  
  
 V následujícím příkladu proměnnou krok je znak a hranice smyčky jsou obě celých čísel. Protože neexistuje žádný standardní převod mezi znaky a celá čísla, tato chyba se nahlásí.  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **ID chyby:** BC30982  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Typy hranice smyčky a proměnná krok podle potřeby změňte tak, aby aspoň jeden z nich je typ, který ostatní rozšíří do. V předchozím příkladu změnit typ `stepVar` k `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —nebo—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Pomocí funkce pro explicitní převod můžete převést rozsah smyčky a proměnná krok na odpovídající typy. V předchozím příkladu platí `Val` funkci, aby se `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [Pro... Next – příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
