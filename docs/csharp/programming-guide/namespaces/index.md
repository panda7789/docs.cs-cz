---
title: Obory názvů – Průvodce programováním v C#
description: Přečtěte si o oborech názvů v programování v jazyce C#. Podívejte se na Přehled vlastností oboru názvů a Prohlédněte si další zdroje informací.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: fca2c641520bd9cd19a48bff2119a6f09c3713ea
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382097"
---
# <a name="namespaces-c-programming-guide"></a>Obory názvů (Průvodce programováním v C#)

Obory názvů se silně využívají v programování v jazyce C# dvěma způsoby. Rozhraní .NET nejprve používá obory názvů k uspořádání svých mnoha tříd, a to takto:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System>je obor názvů a <xref:System.Console> je třída v tomto oboru názvů. `using`Klíčové slovo lze použít, aby nebylo vyžadováno celé jméno, jako v následujícím příkladu:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

Další informace naleznete v [direktivě using](../../language-reference/keywords/using-directive.md).

Za druhé deklarujete vlastní obory názvů, které vám pomohou řídit obor názvů tříd a metod ve větších programovacích projektech. Použijte klíčové slovo [Namespace](../../language-reference/keywords/namespace.md) k deklarování oboru názvů, jak je uvedeno v následujícím příkladu:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Název oboru názvů musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)C#.

## <a name="namespaces-overview"></a>Přehled oborů názvů

Obory názvů mají následující vlastnosti:

- Organizují velké projekty kódu.
- Jsou odděleny pomocí `.` operátoru.
- `using`Direktiva obviates požadavek na zadání názvu oboru názvů pro každou třídu.
- `global`Obor názvů je "kořenový" obor názvů: `global::System` bude vždycky odkazovat na <xref:System> obor názvů .NET.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Používání oborů názvů](using-namespaces.md)
- [Jak používat obor názvů My](how-to-use-the-my-namespace.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [using – direktiva](../../language-reference/keywords/using-directive.md)
- [:: – Operátor](../../language-reference/operators/namespace-alias-qualifier.md)
