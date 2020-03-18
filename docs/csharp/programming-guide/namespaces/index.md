---
title: Obory názvů – programovací příručka jazyka C#
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937617"
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)

Obory názvů jsou v programování jazyka C# silně používány dvěma způsoby. Nejprve rozhraní .NET používá obory názvů k uspořádání mnoha tříd takto:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System>je obor názvů <xref:System.Console> a je třídou v tomto oboru názvů. Klíčové `using` slovo lze použít tak, aby není vyžadován oúplný název, jako v následujícím příkladu:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

Další informace naleznete v [směrnici o používání .](../../language-reference/keywords/using-directive.md)

Za druhé deklarování vlastní chodů názvů vám může pomoci řídit rozsah názvů tříd a metod ve větších programovacích projektech. Pomocí klíčového slova [oboru názvů](../../language-reference/keywords/namespace.md) deklarujte obor názvů, jako v následujícím příkladu:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Název oboru názvů musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)jazyka C# .

## <a name="namespaces-overview"></a>Obory názvů – přehled

Obory názvů mají následující vlastnosti:

- Organizují velké projekty kódu.
- Jsou vymezeny pomocí `.` operátoru.
- Směrnice `using` odstraňuje požadavek zadat název oboru názvů pro každou třídu.
- Obor `global` názvů je "kořenový" `global::System` obor názvů: bude <xref:System> vždy odkazovat na obor názvů .NET.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Namespaces](~/_csharplang/spec/namespaces.md) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Použití oborů názvů](using-namespaces.md)
- [Jak používat obor názvů My](how-to-use-the-my-namespace.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [using – direktiva](../../language-reference/keywords/using-directive.md)
- [:: Operátor](../../language-reference/operators/namespace-alias-qualifier.md)
