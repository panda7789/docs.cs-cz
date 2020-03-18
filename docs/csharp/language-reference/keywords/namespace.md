---
title: klíčové slovo oboru názvů – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625797"
---
# <a name="namespace-c-reference"></a>namespace (Referenční dokumentace jazyka C#)

Klíčové `namespace` slovo se používá k deklarování oboru, který obsahuje sadu souvisejících objektů. Obor názvů můžete použít k uspořádání prvků kódu a k vytvoření globálně jedinečných typů.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Poznámky

V rámci oboru názvů můžete deklarovat nulu nebo více z následujících typů:

- jiný obor názvů

- [Třída](class.md)

- [Rozhraní](interface.md)

- [Struct](../builtin-types/struct.md)

- [Výčtu](../builtin-types/enum.md)

- [delegát](../builtin-types/reference-types.md#the-delegate-type)

Bez ohledu na to, zda explicitně deklarujete obor názvů ve zdrojovém souboru jazyka C#, kompilátor přidá výchozí obor názvů. Tento nepojmenovaný obor názvů, někdy označovaný jako globální obor názvů, je přítomen v každém souboru. Všechny identifikátory v globálním oboru názvů jsou k dispozici pro použití v pojmenovaném oboru názvů.

Obory názvů implicitně mají veřejný přístup a nelze je upravit. Diskuse o modifikátory přístupu, které můžete přiřadit prvkům v oboru názvů, naleznete v [tématu Modifikátory aplikace Access](access-modifiers.md).

Je možné definovat obor názvů ve dvou nebo více deklaracích. Například následující příklad definuje dvě třídy `MyCompany` jako součást oboru názvů:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak volat statickou metodu v vnořené oboru názvů.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Namespaces](~/_csharplang/spec/namespaces.md) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Pomocí](using-directive.md)
- [použití statické](using-static.md)
- [Kvalifikátor aliasu oboru názvů`::`](../operators/namespace-alias-qualifier.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
