---
title: "Nepovinné (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a>Nepovinné (Visual Basic)
Určuje, že při volání procedury lze vynechat argumentu procedury.  
  
## <a name="remarks"></a>Poznámky  
 Pro každý volitelný parametr je nutné určit konstantní výraz jako výchozí hodnota tohoto parametru. Pokud je výsledkem výrazu [nic](../../../visual-basic/language-reference/nothing.md), výchozí hodnota typu dat, hodnota se používá jako výchozí hodnota parametru.  
  
 Pokud seznam parametrů obsahuje volitelný parametr, musí být každý parametr, který následuje také volitelné.  
  
 `Optional` Modifikátor lze použít v těchto kontexty:  
  
-   [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
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
 [Volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
