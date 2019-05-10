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
ms.openlocfilehash: 40605d4843bfccf9d2819b3ec6f2ef65f9e9cf9a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661317"
---
# <a name="optional-visual-basic"></a>Nepovinné (Visual Basic)
Určuje, že argumentu procedury může při volání procedury vynechat.  
  
## <a name="remarks"></a>Poznámky  
 Pro každý volitelný parametr musíte zadat konstantní výraz jako výchozí hodnota tohoto parametru. Pokud je výraz vyhodnocen [nic](../../../visual-basic/language-reference/nothing.md), je použita výchozí hodnota datového typu hodnoty jako výchozí hodnotu parametru.  
  
 Pokud seznam parametrů obsahuje volitelný parametr, každý parametr, která ji následuje musí být také volitelný.  
  
 `Optional` Modifikátor lze použít v těchto kontextech:  
  
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Při volání procedury s nebo bez něj volitelné parametry, můžete předat argumenty podle umístění nebo podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Proceduru s volitelnými parametry lze definovat také pomocí přetížení. Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze procedury, ten, který přijímá parametr a ten, který nepodporuje. Další informace najdete v tématu [přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje proceduru, která je volitelný parametr.  
  
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
 Následující příklad ukazuje, jak volání procedury s argumenty předány podle pozice a s argumenty předány podle názvu. Postup má dva volitelné parametry.  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
