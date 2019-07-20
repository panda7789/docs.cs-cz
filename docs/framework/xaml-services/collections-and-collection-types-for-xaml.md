---
title: Kolekce a typy kolekcí v jazyku XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364337"
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekce a typy kolekcí v jazyku XAML

Toto téma popisuje, jak definovat vlastnosti typů, které jsou určeny pro podporu kolekce, a pro podporu syntaxe jazyka XAML pro vytváření instancí položek kolekce jako podřízených elementů nadřazeného objektu elementu nebo prvku vlastnosti.

## <a name="xaml-collection-concepts"></a>Koncepty shromažďování XAML

Koncepční, jakýkoli vztah v jazyce XAML, kde existuje více podřízených položek v rámci oboru elementu objektu XAML nebo elementu vlastnosti XAML, musí být implementovány jako kolekce. Tato kolekce musí být přidružena k určité vlastnosti XAML typu XAML, který je nadřazeným prvkem v daném vztahu. Vlastnost musí být kolekce, protože procesor XAML očekává, že každá položka v označení přiřadí každou položku jako nově přidanou položku Vlastnosti zálohování kolekce.

Na úrovni jazyka XAML nejsou přesné požadavky na podporu kolekce zcela definovány. Koncept, který může být kolekcí buď seznam, nebo slovník (ale ne obojí) je definován na úrovni jazyka XAML, ale které typy zálohování reprezentují buď seznamy nebo slovníky, nejsou definovány jazykem XAML.

V .NET Framework služby XAML je koncept podpory kolekce XAML jasně definován z podmínek .NET Frameworkch typů zálohování. Konkrétně podpora XAML pro kolekce je založena na několika .NET Framework konceptech a rozhraní API, která se používají pro seznamy a slovníky v Obecné .NET Framework programování.

1. <xref:System.Collections.IList> Rozhraní označuje kolekci seznamů.

2. <xref:System.Collections.IDictionary> Rozhraní označuje kolekci slovníku.

3. <xref:System.Array>představuje pole a pole podporuje <xref:System.Collections.IList> metody.

V každé z těchto konceptů kolekce očekává procesor XAML služby .NET Framework XAML, aby volal `Add` metodu na konkrétní instanci typu vlastnosti kolekce. Nebo ve scénáři serializace vytvoří procesor XAML diskrétní instance typu XAML pro každou položku, která se nachází v seznamu, slovníku nebo poli na základě konkrétního konceptu "Items" každé kolekce. Jsou to: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; Explicit<xref:System.Array.System%23Collections%23IList%23Item%2A> pro .<xref:System.Array>

## <a name="generic-collections"></a>Obecné kolekce

Obecné kolekce mohou být užitečné pro obecné .NET Framework programování a lze je také použít pro vlastnosti kolekce XAML. Nicméně Obecná rozhraní <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602> nejsou identifikovány pomocí .NET Framework procesory XAML služby XAML jako ekvivalent neobecného <xref:System.Collections.IList> nebo <xref:System.Collections.IDictionary>. Místo implementace rozhraní je doporučený přístup pro typy vlastností obecných kolekcí odvozen od tříd <xref:System.Collections.Generic.List%601> nebo. <xref:System.Collections.Generic.Dictionary%602> Tyto třídy implementují neobecná rozhraní, takže zahrnují očekávanou podporu pro kolekce XAML v základní implementaci.

## <a name="read-only-collections-and-initialization-logic"></a>Kolekce a logika inicializace jen pro čtení

V .NET Framework programování je to běžný vzor návrhu k vytvoření jakékoli vlastnosti, která obsahuje hodnotu kolekce jako kolekci jen pro čtení. Tento model umožňuje instanci, která vlastní vlastnost kolekce, lepší kontrolu nad tím, co se stane s kolekcí. Konkrétně vzor zabraňuje náhodnému nahrazení celé již existující kolekce nastavením vlastnosti. V tomto modelu by měl být jakýkoli přístup ke kolekci volajícím proveden místo toho voláním metod nebo vlastností, které podporuje typ kolekce a/nebo relevantní rozhraní kolekce, jako je například <xref:System.Collections.IList>.

Použití tohoto vzoru znamená, že každá třída, která zveřejňuje vlastnost kolekce jen pro čtení, musí nejdřív inicializovat tuto vlastnost, aby obsahovala prázdnou kolekci. Obvykle se inicializace provádí jako součást chování konstrukce pro třídu. Aby byla užitečná pro XAML, je důležité, aby tato logika vždy odkazovala na konstruktor bez parametrů, protože XAML obecně volá konstruktor bez parametrů před zpracováním vlastností (vlastnosti kolekce nebo jinak).

## <a name="xaml-type-system-support-and-collections"></a>Podpora a kolekce systému typů XAML

Kromě základní mechanismy analýzy XAML a naplnění nebo serializace vlastností kolekce je systém typů XAML, jak je implementován v .NET Framework služby XAML, obsahuje několik funkcí návrhu, které se týkají kolekcí v jazyce XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>Vrátí hodnotu true, pokud je typ XAML zálohovaný typem, který poskytuje podporu shromažďování XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>a <xref:System.Xaml.XamlType.IsArray%2A> může dále identifikovat, který režim kolekce podporuje typ XAML. Pro vlastní procesory XAML, které jsou založené na .NET Framework XAML Services a systému typů XAML, ale nejsou založené <xref:System.Xaml.XamlWriter> na stávajících implementacích, může být nutné zjistit, který způsob, jakým je použit režim sběru zpracování kolekce.

3. Všechny předchozí hodnoty vlastností jsou potenciálně ovlivněny přepsáním <xref:System.Xaml.XamlType.LookupCollectionKind%2A> typu XAML.
