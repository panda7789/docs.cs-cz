---
title: klíčové slovo Namespace C# – referenční informace
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 04595e96f6f14b8806a2d89625151910cac9e0d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345423"
---
# <a name="namespace-c-reference"></a>namespace (Referenční dokumentace jazyka C#)

Klíčové slovo `namespace` slouží k deklaraci oboru, který obsahuje sadu souvisejících objektů. Obor názvů můžete použít k uspořádání prvků kódu a k vytvoření globálně jedinečných typů.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Poznámky

V rámci oboru názvů můžete deklarovat nula nebo více následujících typů:

- jiný obor názvů

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](../builtin-types/enum.md)

- [delegate](../builtin-types/reference-types.md#the-delegate-type)

Bez ohledu na to, jestli explicitně deklarujete obor C# názvů ve zdrojovém souboru, kompilátor přidá výchozí obor názvů. Tento nepojmenovaný obor názvů, který se někdy označuje jako globální obor názvů, se nachází v každém souboru. Libovolný identifikátor v globálním oboru názvů je k dispozici pro použití v pojmenovaném oboru názvů.

Obory názvů mají implicitně veřejný přístup a nelze je upravovat. Diskuzi o modifikátorech přístupu, které můžete přiřadit k prvkům v oboru názvů, najdete v tématu [modifikátory přístupu](access-modifiers.md).

Je možné definovat obor názvů ve dvou nebo více deklaracích. Například následující příklad definuje dvě třídy jako součást oboru názvů `MyCompany`:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zavolat statickou metodu ve vnořeném oboru názvů.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [using](using-directive.md)
- [Použití static](using-static.md)
- [`::` kvalifikátoru aliasu oboru názvů](../operators/namespace-alias-qualifier.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
