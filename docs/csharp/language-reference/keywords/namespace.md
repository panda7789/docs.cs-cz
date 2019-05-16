---
title: klíčové slovo oboru názvů - C# odkaz
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: f938e49267faad8aebbf4c22fc921f305d160123
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633440"
---
# <a name="namespace-c-reference"></a>namespace (Referenční dokumentace jazyka C#)

`namespace` – Klíčové slovo se používá k deklarování oboru, který obsahuje sadu souvisejících objektů. Obor názvů slouží k uspořádání prvků kódu a vytváření globálně jedinečných typů.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Poznámky

V rámci oboru názvů můžete deklarovat nula nebo více z následujících typů:

- jiný obor názvů

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

Zda explicitně deklarovat oboru názvů do zdrojového souboru jazyka C#, kompilátor přidá výchozí obor názvů. Tato nepojmenovaného oboru názvů, někdy označovány jako globální obor názvů, je k dispozici v každém souboru. Žádný identifikátor v globálním oboru názvů je k dispozici pro použití s názvem oboru názvů.

Obory názvů mají implicitně veřejný přístup, a to není možné upravit. Informace o přístupu modifikátory přístupu můžete přiřadit na prvky v oboru názvů, naleznete v tématu [modifikátory přístupu](access-modifiers.md).

Je možné definovat ve dvou nebo více deklarací oboru názvů. Například následující příklad definuje dvě třídy jako součást `MyCompany` obor názvů:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zavolat statickou metodu ve vnořené oboru názvů.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a>Související prostředky

Další informace o použití oboru názvů naleznete v následujících tématech:

- [Obory názvů](../../programming-guide/namespaces/index.md)

- [Použití oboru názvů](../../programming-guide/namespaces/using-namespaces.md)

- [Postupy: Použití aliasu globálního Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova oboru názvů](namespace-keywords.md)
- [using](using-directive.md)
- [Pomocí statické](using-static.md)
