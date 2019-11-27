---
title: volitelná,
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: a16dae35bf4bc84d95501624c4f023f390a8dda8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351439"
---
# <a name="optional-visual-basic"></a>Nepovinné (Visual Basic)

Určuje, že při volání procedury lze argument procedury vynechat.

## <a name="remarks"></a>Poznámky

Pro každý volitelný parametr je nutné zadat konstantní výraz jako výchozí hodnotu tohoto parametru. Pokud je výraz vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md), je jako výchozí hodnota parametru použita výchozí hodnota datového typu value.

Pokud seznam parametrů obsahuje volitelný parametr, všechny parametry, které následují, musí být také volitelné.

V těchto kontextech lze použít modifikátor `Optional`:

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> Při volání procedury s nepovinnými parametry nebo bez nich můžete předat argumenty podle umístění nebo podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).

> [!NOTE]
> Můžete také definovat proceduru s nepovinnými parametry pomocí přetížení. Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze procedury, jednu, která přijímá parametr a druhý. Další informace najdete v tématu [přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).

## <a name="example"></a>Příklad

Následující příklad definuje proceduru, která má volitelný parametr.

```vb
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

Následující příklad ukazuje způsob volání procedury s argumenty předanými pozicí a s argumenty předanými názvem. Procedura má dva volitelné parametry.

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>Viz také:

- [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
