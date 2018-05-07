---
title: Typ &#39; &lt;NázevProměnné&gt; &#39; nelze odvodit, protože hranice smyčky a proměnná krok není rozšíří do stejného typu
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: d6fdd9445b5336773d150c643c7bf1ca58a0c87a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ &#39; &lt;NázevProměnné&gt; &#39; nelze odvodit, protože hranice smyčky a proměnná krok není rozšíří do stejného typu
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
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
