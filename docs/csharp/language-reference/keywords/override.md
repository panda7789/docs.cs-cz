---
title: Modifikátor - přepsat C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 6a8e79da3897e867fa3becab5fcfc70afe72e614
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244437"
---
# <a name="override-c-reference"></a>override (Referenční dokumentace jazyka C#)

`override` Modifikátor je potřeba rozšířit nebo upravit abstraktní nebo virtuální provádění zděděné metody, vlastnosti, indexeru nebo události.

## <a name="example"></a>Příklad

V tomto příkladu `Square` třída musí poskytovat implementaci přepsané `Area` protože `Area` se dědí z abstraktní `ShapesClass`:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override` Metody poskytuje novou implementaci člena, který je zděděn ze základní třídy. Metoda, která je přepsána `override` prohlášení je označován jako přepsané základní metodě. Přepsané základní metoda musí mít stejný podpis jako `override` metody. Informace o dědičnosti, naleznete v tématu [dědičnosti](../../programming-guide/classes-and-structs/inheritance.md).

Nevirtuální nebo statické metody nelze přepsat. Přepsané základní metoda musí být `virtual`, `abstract`, nebo `override`.

`override` Deklarace nemůže změnit přístupnost `virtual` metody. Obě `override` metoda a `virtual` metoda musí mít stejný [úrovně modifikátor přístupu](access-modifiers.md).

Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metody.

Přepsání deklarace vlastnost musíte zadat přesně stejné modifikátor přístupu, typ a název jako zděděné vlastnosti a musí být přepsané vlastnosti `virtual`, `abstract`, nebo `override`.

Další informace o tom, jak používat `override` – klíčové slovo, naleznete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nová klíčová slova Override a](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Příklad

Tento příklad definuje základní třídu s názvem `Employee`a odvozená třída s názvem `SalesEmployee`. `SalesEmployee` Třída zahrnuje další pole, `salesbonus`a přepíše metodu `CalculatePay` aby vzít v úvahu.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](modifiers.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [new](new.md)
- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
