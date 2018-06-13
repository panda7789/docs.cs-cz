---
title: Nepovinné (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: f88020c7407fb9c91e06bc2ee177773171e344fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599301"
---
# <a name="optional-visual-basic"></a>Nepovinné (Visual Basic)
Určuje, že při volání procedury lze vynechat argumentu procedury.  
  
## <a name="remarks"></a>Poznámky  
 Pro každý volitelný parametr je nutné určit konstantní výraz jako výchozí hodnota tohoto parametru. Pokud je výsledkem výrazu [nic](../../../visual-basic/language-reference/nothing.md), výchozí hodnota typu dat, hodnota se používá jako výchozí hodnota parametru.  
  
 Pokud seznam parametrů obsahuje volitelný parametr, musí být každý parametr, který následuje také volitelné.  
  
 `Optional` Modifikátor lze použít v těchto kontexty:  
  
-   [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Při volání procedury s nebo bez volitelné parametry, můžete předat argumentů podle pozice nebo podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Procedura se volitelné parametry můžete také definovat pomocí přetížení. Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze postup, který přijme parametr a ten, který není. Další informace najdete v tématu [přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje procedury, která je volitelný parametr.  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob volání procedury s argumenty předávané podle pozice a argumentů předaných podle názvu. Postup má dva volitelné parametry.  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
