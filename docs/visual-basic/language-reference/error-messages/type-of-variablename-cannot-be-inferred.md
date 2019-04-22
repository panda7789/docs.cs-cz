---
title: Typ '<variablename>' nelze odvodit, protože omezení cyklu a proměnnou kroku nelze rozšířit na stejný typ.
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: e90e881546c12df2c8b19ff03a4d4c7304c4596c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815872"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ '\<NázevProměnné >' nelze odvodit, protože omezení cyklu a klauzuli kroku nejde rozšířit na stejný typ.
Jste napsali `For...Next` smyčku, ve kterém kompilátor nemůže odvodit typ dat pro řídicí proměnná smyčky for vzhledem k tomu, že jsou splněny následující podmínky:  
  
-   Není zadaný datový typ řídicí proměnná smyčky s `As` klauzuli.  
  
-   Omezení cyklu a klauzuli kroku obsahovat aspoň dva datové typy.  
  
-   Neexistuje žádný standardní převod mezi datovými typy.  
  
 Proto kompilátor nelze odvodit datový typ řídicí proměnná smyčky.  
  
 V následujícím příkladu krok proměnná je znak, a omezení cyklu jsou obě celá čísla. Protože neexistuje žádný standardní převod mezi znaky a celá čísla, tato chyba se nahlásí.  
  
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
  
-   Změňte typy omezení cyklu a klauzuli kroku podle potřeby tak, aby aspoň jeden z nich je typ, který ostatní rozšířit na. V předchozím příkladu, změňte typ `stepVar` k `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —nebo—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Převést na odpovídající typy omezení cyklu a klauzuli kroku pomocí funkce pro explicitní převod. V předchozím příkladu platí `Val` funkce `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
