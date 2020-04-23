---
title: Kolekce a typy kolekcí v jazyku XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 2ec58026c605df31489c8aab4c4cc714dab11474
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "82071295"
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekce a typy kolekcí pro XAML

Tento článek popisuje, jak definovat vlastnosti typů, které jsou určeny pro podporu kolekce a pro podporu syntaxe XAML pro vytváření instancí položek kolekce jako podřízené prvky elementu elementu nebo elementu vlastnosti.

## <a name="xaml-collection-concepts"></a>Koncepty kolekce XAML

Koncepčně všechny relace v XAML, kde existuje více podřízených položek v rámci oboru Element objektu XAML nebo XAML prvek vlastnosti musí být implementována jako kolekce. Tato kolekce musí být přidružena k určité vlastnosti XAML typu XAML, který je nadřazeným v tomto vztahu. Vlastnost musí být kolekce, protože procesor XAML očekává, že přiřadit každou položku ve značkách být nově přidané položky vlastnosti zálohování kolekce.

Na jazykové úrovni XAML nejsou zcela definovány přesné požadavky na podporu kolekce. Koncept, že kolekce může být seznam nebo slovník (ale ne obojí) je definována na úrovni jazyka XAML, ale které typy zálohování představují seznamy nebo slovníky, není definován jazykem XAML.

Ve službě .NET XAML services je koncept podpory kolekce XAML jasněji definován z hlediska typů zálohování .NET. Konkrétně podpora XAML pro kolekce je založena na několika konceptech rozhraní .NET a rozhraní API, které se používají pro seznamy a slovníky obecně .NET programování.

1. Rozhraní <xref:System.Collections.IList> označuje seznam kolekce.

2. Rozhraní <xref:System.Collections.IDictionary> označuje kolekci slovníku.

3. <xref:System.Array>představuje pole a pole <xref:System.Collections.IList> podporuje metody.

V každém z těchto konceptů kolekce .NET XAML Services XAML procesor očekává volání `Add` metody na konkrétní instanci typu vlastnosti kolekce. Nebo ve scénáři serializace procesorXAML vytváří diskrétní XAML-typ instance pro každou položku nalézt v seznamu, slovníku nebo pole na základě každé kolekce konkrétní koncept "Položky". Jedná se <xref:System.Collections.IList.Item%2A?displayProperty=nameWithType>o tyto položky: ; <xref:System.Collections.IDictionary.Item%2A?displayProperty=nameWithType>; explicitní <xref:System.Array.System%23Collections%23IList%23Item%2A?displayProperty=nameWithType> pro <xref:System.Array>.

## <a name="generic-collections"></a>Obecné kolekce

Obecné kolekce mohou být užitečné pro obecné programování .NET a lze je také použít pro vlastnosti kolekce XAML. <xref:System.Collections.Generic.IList%601> Obecná rozhraní a <xref:System.Collections.Generic.IDictionary%602> nejsou však identifikovány procesory XAML služby XAML služby <xref:System.Collections.IList> <xref:System.Collections.IDictionary>.NET jako rovnocenné neobecným nebo . Spíše než implementaci rozhraní, doporučený přístup pro typy vlastností obecné <xref:System.Collections.Generic.List%601> kolekce <xref:System.Collections.Generic.Dictionary%602>je odvodit z třídy nebo . Tyto třídy implementují neobecná rozhraní a proto zahrnují očekávanou podporu pro kolekce XAML v základní implementaci.

## <a name="read-only-collections-and-initialization-logic"></a>Kolekce jen pro čtení a logika inicializace

V programování .NET je běžný návrhový vzor, aby všechny vlastnosti, které obsahuje hodnotu kolekce jako kolekce jen pro čtení. Tento vzor umožňuje instance, která vlastní vlastnost kolekce lépe řídit, co se stane s kolekcí.. Konkrétně vzor zabraňuje náhodné nahrazení celé existující kolekce nastavením vlastnosti. V tomto vzoru jakýkoli přístup ke kolekci volajícími by měl být místo toho pomocí volání metod nebo vlastností, jak je podporován typem kolekce a/nebo příslušná rozhraní kolekce, jako je například <xref:System.Collections.IList>.

Použití tohoto vzoru znamená, že všechny třídy, která zveřejňuje vlastnost kolekce jen pro čtení musí nejprve inicializovat tuto vlastnost držet prázdnou kolekci. Obvykle se inicializace provádí jako součást chování konstrukce pro třídu. Chcete-li být užitečné pro XAML, je důležité, aby tato logika je vždy odkazuje konstruktor bez parametrů, protože XAML obecně volá konstruktor bez parametrů před zpracováním vlastnosti (vlastnosti kolekce nebo jinak).

## <a name="xaml-type-system-support-and-collections"></a>Podpora a kolekce systému typu XAML

Kromě základní mechaniky analýzy XAML a vyplnění nebo serializace vlastností kolekce obsahuje systém typu XAML implementovaný ve službě .NET XAML Services několik funkcí návrhu, které se týká kolekcí v jazyce XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>vrátí hodnotu true, pokud je typ XAML zálohován typem, který poskytuje podporu kolekce XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>a <xref:System.Xaml.XamlType.IsArray%2A> můžete dále určit, který režim sběru typ XAML podporuje. Pro vlastní xaml procesory, které jsou založeny na služby .NET XAML a systému typu XAML, ale není založen na existující <xref:System.Xaml.XamlWriter> implementace, vědět, který režim kolekce se používá může být nezbytné vědět, kterou metodu vyvolat pro zpracování kolekce.

3. Každá z předchozích hodnot vlastností je potenciálně ovlivněna lokálními hodnotami <xref:System.Xaml.XamlType.LookupCollectionKind%2A> typu XAML.
