---
title: Vlastnosti – Průvodce programováním v C#
description: Vlastnost v jazyce C# je člen, který používá přístupové metody ke čtení, zápisu nebo výpočtu hodnoty soukromého pole, jako by šlo o veřejný datový člen.
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 231e8e6a11f2655ccdea5489f054910a1ecf2586
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863939"
---
# <a name="properties-c-programming-guide"></a>Vlastnosti (Průvodce programováním v C#)

Vlastnost je člen, který poskytuje flexibilní mechanismus pro čtení, zápis nebo výpočet hodnoty soukromého pole. Vlastnosti lze použít, jako by se jedná o veřejné datové členy, ale ve skutečnosti se jedná o speciální metody nazývané *přistupující objekty*. Díky tomu je možné snadno získávat data a pořád podporovat zabezpečení a flexibilitu metod.  

## <a name="properties-overview"></a>Přehled vlastností  
  
- Vlastnosti umožňují třídě zveřejnit veřejný způsob získávání a nastavování hodnot při skrývání implementačního nebo ověřovacího kódu.  
  
- Přístup k vlastnosti [Get](../../language-reference/keywords/get.md) se používá k vrácení hodnoty vlastnosti a k přiřazení nové hodnoty se používá přístupový objekt vlastnosti [sady](../../language-reference/keywords/set.md) . Tyto přístupové objekty mohou mít různé úrovně přístupu. Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md).  
  
- Klíčové slovo [Value](../../language-reference/keywords/value.md) slouží k definování hodnoty přidělené `set` přístupovým objektem.  
- Vlastnosti mohou být *určeny pro čtení i zápis* (mají přístup i `get` `set` přístup), *jen pro čtení* (mají `get` přistupující objekt, ale bez `set` přístupového objektu), nebo *jen pro zápis* (mají `set` přístup, ale bez `get` přístupového objektu). Vlastnosti jen pro zápis jsou vzácné a nejčastěji se používají k omezení přístupu k citlivým datům.

- Jednoduché vlastnosti, které nevyžadují žádný vlastní přistupující kód, se dají implementovat buď jako definice těla výrazu, nebo jako [automaticky implementované vlastnosti](./auto-implemented-properties.md).

## <a name="properties-with-backing-fields"></a>Vlastnosti s zálohovanými poli

Jeden základní vzor pro implementaci vlastnosti zahrnuje použití privátního zálohovacího pole pro nastavení a načtení hodnoty vlastnosti. `get`Přistupující objekt vrátí hodnotu soukromého pole a `set` přistupující objekt může provést některá ověření dat před přiřazením hodnoty k soukromému poli. Oba přistupující objekty mohou také provést nějaký převod nebo výpočet dat před uložením nebo vrácením.

Následující příklad znázorňuje tento model. V tomto příkladu `TimePeriod` Třída představuje časový interval. Interně Třída ukládá časový interval v sekundách v rámci soukromého pole s názvem `_seconds` . Vlastnost pro čtení i zápis s názvem `Hours` umožňuje zákazníkovi zadat časový interval v hodinách. I `get` `set` přistupující objekty provádějí nezbytný převod mezi hodinami a sekundami. Kromě toho `set` přistupující objekt ověřuje data a vyvolá v případě, že <xref:System.ArgumentOutOfRangeException> počet hodin je neplatný.

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  

 Přistupující objekty vlastnosti se často skládají z jednoduchých příkazů, které pouze přiřadí nebo vracejí výsledek výrazu. Tyto vlastnosti můžete implementovat jako členy Expression-těle. Definice textu výrazu se skládají z `=>` symbolu následovaného výrazem, který se má přiřadit nebo načíst z vlastnosti.

 Počínaje jazykem C# 6 vlastnosti jen pro čtení mohou implementovat `get` přistupující objekt jako člena Expression-těle. V takovém případě se `get` nepoužije klíčové slovo přistupující ani `return` klíčové slovo. Následující příklad implementuje vlastnost jen pro čtení `Name` jako člen Expression-těle.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Počínaje jazykem C# 7,0 `get` `set` mohou být oba a přistupující objekty implementovány jako členové Expression-těle. V takovém případě `get` `set` musí být k dispozici klíčová slova a. Následující příklad ilustruje použití definice textu výrazu pro přistupující objekty. Všimněte si, že `return` klíčové slovo se u `get` přístupového objektu nepoužívá.

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti

V některých případech vlastnosti `get` a `set` přistupující objekty přiřadí hodnotu nebo načítají hodnotu z pole pro zálohování bez zahrnutí další logiky. Pomocí automaticky implementovaných vlastností můžete zjednodušit kód, zatímco kompilátor jazyka C# transparentně poskytuje pole pro zálohování.

Pokud má vlastnost i `get` `set` přístup, musí být oba implementovány automaticky. Automaticky implementovanou vlastnost definujete pomocí `get` `set` klíčových slov a, aniž byste museli poskytovat žádnou implementaci. Následující příklad opakuje předchozí, s tím rozdílem, že `Name` a `Price` jsou automaticky implementované vlastnosti. Všimněte si, že tento příklad také odebere parametrizovaný konstruktor, aby `SaleItem` objekty byly nyní inicializovány s voláním konstruktoru bez parametrů a [inicializátoru objektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Související oddíly  
  
- [Použití vlastností](./using-properties.md)  
  
- [Vlastnosti rozhraní](./interface-properties.md)  
  
- [Porovnání mezi vlastnostmi a indexery](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md)  
  
- [Automaticky implementované vlastnosti](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [vlastnosti](~/_csharplang/spec/classes.md#properties) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Použití vlastností](./using-properties.md)
- [Indexery](../indexers/index.md)
- [získat klíčové slovo](../../language-reference/keywords/get.md)
- [Set – klíčové slovo](../../language-reference/keywords/set.md)
