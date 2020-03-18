---
title: Vlastnosti – průvodce programováním jazyka C#
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: ee530e981e0c85302b2b11cc739d6c51d6650ddd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170101"
---
# <a name="properties-c-programming-guide"></a>Vlastnosti (Průvodce programováním v C#)

Vlastnost je člen, který poskytuje flexibilní mechanismus pro čtení, zápis nebo výpočet hodnoty soukromého pole. Vlastnosti lze použít, jako by byly veřejné datové členy, ale ve skutečnosti jsou speciální metody nazývané *přístupové objekty*. To umožňuje snadný přístup k datům a stále pomáhá podporovat bezpečnost a flexibilitu metod.  

## <a name="properties-overview"></a>Přehled vlastností  
  
- Vlastnosti umožňují třídě vystavit veřejný způsob získávání a nastavování hodnot při skrytí implementace nebo ověřovacího kódu.  
  
- Přístupový objekt [get](../../language-reference/keywords/get.md) vlastnost se používá k vrácení hodnoty vlastnosti a [přístupový objekt vlastnosti set](../../language-reference/keywords/set.md) se používá k přiřazení nové hodnoty. Tyto přístupové typy mohou mít různé úrovně přístupu. Další informace naleznete v [tématu Omezení přístupnosti přístupu k přístupu](./restricting-accessor-accessibility.md).  
  
- Klíčové slovo [value](../../language-reference/keywords/value.md) se používá k definování `set` hodnoty přiřazené přistupujícím ortelem.  
- Vlastnosti mohou být pro čtení `get` a `set` *zápis* (mají přístupový objekt i přistupující objekt), *jen pro čtení* (mají `get` přistupující objekt, ale žádný `set` přistupující objekt) nebo jen pro *zápis* (mají `set` přistupující objekt, ale žádný `get` přistupující objekt). Vlastnosti pouze pro zápis jsou vzácné a nejčastěji se používají k omezení přístupu k citlivým datům.

- Jednoduché vlastnosti, které nevyžadují žádný vlastní přistupující kód, mohou být implementovány buď jako definice těla výrazu, nebo jako [automaticky implementované vlastnosti](./auto-implemented-properties.md).

## <a name="properties-with-backing-fields"></a>Vlastnosti s opěrnými poli

Jeden základní vzor pro implementaci vlastnosti zahrnuje použití soukromé hodovací pole pro nastavení a načtení hodnoty vlastnosti. Přistupující `get` počitadla vrátí `set` hodnotu soukromého pole a přistupující subjekt může provést ověření některých dat před přiřazením hodnoty soukromému poli. Oba přistupující servery mohou také provést některé převodnebo výpočtu na data před uložením nebo vrácení.

Následující příklad ilustruje tento vzor. V tomto příkladu `TimePeriod` třída představuje časový interval. Interně třída ukládá časový interval v sekundách `_seconds`v soukromém poli s názvem . Vlastnost čtení a `Hours` zápisu s názvem umožňuje zákazníkovi zadat časový interval v hodinách. Jak `get` a `set` přistupující chodů provést potřebný převod mezi hodinami a sekundami. Kromě toho `set` přistupující objekt ověří <xref:System.ArgumentOutOfRangeException> data a vyvolá, pokud je počet hodin neplatný.

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definice těla výrazu  

 Přístupové objekty vlastností se často skládají z jednořádkových příkazů, které pouze přiřazují nebo vracejí výsledek výrazu. Tyto vlastnosti můžete implementovat jako členy s výrazem. Definice těla výrazu `=>` se skládají ze symbolu následovaného výrazem, který má být přiřazen nebo načten z vlastnosti.

 Počínaje C# 6, vlastnosti jen `get` pro čtení můžete implementovat přistupujícíobjekt jako člen s výrazem. V tomto případě se `get` nepoužívá klíčové `return` slovo přistupujícího ani klíčového slova. Následující příklad implementuje vlastnost `Name` jen pro čtení jako člen s výrazem.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Počínaje C# 7.0, `get` jak `set` a přistupující ho lze implementovat jako členy s výrazem. V tomto případě `get` `set` a klíčová slova musí být k dispozici. Následující příklad ilustruje použití definice těla výrazu pro oba přistupující subjekty. Všimněte `return` si, že klíčové `get` slovo se nepoužívá s přistupujícím ortelem.

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti

V některých `get` případech `set` vlastnost a přistupující objekty pouze přiřadit hodnotu nebo načíst hodnotu z pole zálohování bez zahrnutí jakékoli další logiky. Pomocí automaticky implementované vlastnosti, můžete zjednodušit kód při s kompilátorem Jazyka C# transparentně poskytnout záložní pole pro vás.

Pokud vlastnost má `get` oba `set` a a přistupující objekt, obě musí být automaticky implementována. Definujte automaticky implementovanou vlastnost `get` `set` pomocí klíčových slov a bez poskytnutí jakékoli implementace. Následující příklad opakuje předchozí, s `Name` tím `Price` rozdílem, že a jsou automaticky implementované vlastnosti. Všimněte si, že v příkladu také `SaleItem` odebere parametrizovaný konstruktor, takže objekty jsou nyní inicializovány s voláním konstruktoru bez parametrů a [inicializátorem objektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Související oddíly  
  
- [Použití vlastností](./using-properties.md)  
  
- [Vlastnosti rozhraní](./interface-properties.md)  
  
- [Porovnání vlastností a indexerů](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md)  
  
- [Automaticky implementované vlastnosti](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

For more information, see [Properties](~/_csharplang/spec/classes.md#properties) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Použití vlastností](./using-properties.md)
- [Indexery](../indexers/index.md)
- [získat klíčové slovo](../../language-reference/keywords/get.md)
- [nastavit klíčové slovo](../../language-reference/keywords/set.md)
