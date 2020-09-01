---
description: klíčové slovo Namespace – Referenční dokumentace jazyka C#
title: klíčové slovo Namespace – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139577"
---
# <a name="namespace-c-reference"></a>namespace (Referenční dokumentace jazyka C#)

`namespace`Klíčové slovo slouží k deklaraci oboru, který obsahuje sadu souvisejících objektů. Obor názvů můžete použít k uspořádání prvků kódu a k vytvoření globálně jedinečných typů.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Poznámky

V rámci oboru názvů můžete deklarovat nula nebo více následujících typů:

- jiný obor názvů

- [Deník](class.md)

- [prostředí](interface.md)

- [nemají](../builtin-types/struct.md)

- [vytváření](../builtin-types/enum.md)

- [dostával](../builtin-types/reference-types.md#the-delegate-type)

Bez ohledu na to, jestli explicitně deklarujete obor názvů ve zdrojovém souboru C#, kompilátor přidá výchozí obor názvů. Tento nepojmenovaný obor názvů, který se někdy označuje jako globální obor názvů, se nachází v každém souboru. Libovolný identifikátor v globálním oboru názvů je k dispozici pro použití v pojmenovaném oboru názvů.

Obory názvů mají implicitně veřejný přístup a nelze je upravovat. Diskuzi o modifikátorech přístupu, které můžete přiřadit k prvkům v oboru názvů, najdete v tématu [modifikátory přístupu](access-modifiers.md).

Je možné definovat obor názvů ve dvou nebo více deklaracích. Například následující příklad definuje dvě třídy jako součást `MyCompany` oboru názvů:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zavolat statickou metodu ve vnořeném oboru názvů.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [using](using-directive.md)
- [Použití static](using-static.md)
- [Kvalifikátor aliasu oboru názvů `::`](../operators/namespace-alias-qualifier.md)
- [Jmenné prostory](../../programming-guide/namespaces/index.md)
