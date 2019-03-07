---
title: Kolekce a typy kolekcí v jazyku XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 4123b64545f7c47a96c4cae496046a89b7e576b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494620"
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekce a typy kolekcí v jazyku XAML

Toto téma popisuje, jak definovat vlastnosti typů, které jsou určené pro podporu kolekce a které zajišťují podporu syntaxe XAML pro vytvoření instance položky kolekce jako podřízené položky elementu nadřazeného elementu object nebo property – element.

## <a name="xaml-collection-concepts"></a>Koncepty kolekce XAML

Koncepčně každá relace v XAML, kde existuje více podřízených položek v rámci oboru prvku objektu XAML nebo elementu vlastnosti XAML musí být implementován jako kolekce. Tuto kolekci musí být přidružen určité vlastnosti XAML, která je v této relaci typu XAML. Vlastnost musí být kolekce, protože procesor XAML se očekává, že přiřadit každé položky v kódu na nově přidané položky základní vlastnosti kolekce.

Na úrovni jazyka XAML nejsou přesné požadavky na kolekce podpory plně definován. Koncepci, že kolekce může být buď seznam nebo slovník (ale ne obojí) je definovaný na úrovni jazyka XAML, ale základní typy, které představují buď seznamy nebo slovníky není definován v jazyce XAML.

V rozhraní .NET Framework XAML Services koncept XAML kolekce podporu více jasně definované z hlediska zálohování typy rozhraní .NET Framework. Podpora XAML pro kolekce je konkrétně podle několika koncepty rozhraní .NET Framework a rozhraní API, která se používají pro seznamy a slovníků v obecné programování v rozhraní .NET Framework.

1. <xref:System.Collections.IList> Rozhraní určuje kolekci seznamů.

2. <xref:System.Collections.IDictionary> Rozhraní určuje kolekci slovníku.

3. <xref:System.Array> představuje pole a pole podporuje <xref:System.Collections.IList> metody.

V každé z těchto konceptů kolekce na rozhraní .NET Framework XAML Services XAML procesor očekává, že volání `Add` metodu na konkrétní instanci typu vlastnost kolekce. Nebo v případě serializace v procesoru XAML vytváří samostatné instance typu XAML pro každou položku v seznamu, slovníku nebo pole založené na konkrétní pojem "Položky" každou kolekci. Jedná se o: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; explicitní <xref:System.Array.System%23Collections%23IList%23Item%2A> pro <xref:System.Array>.

## <a name="generic-collections"></a>Obecné kolekce

Obecné kolekce může být užitečné pro obecné programování rozhraní .NET Framework a je také možné kolekci vlastností XAML. Ale obecný rozhraní <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602> nejdou identifikovány pomocí rozhraní .NET Framework XAML Services XAML procesorů jako ekvivalentní neobecné <xref:System.Collections.IList> nebo <xref:System.Collections.IDictionary>. Místo implementace rozhraní, je doporučený postup pro obecnou kolekci typů vlastností jsou odvozeny z třídy <xref:System.Collections.Generic.List%601> nebo <xref:System.Collections.Generic.Dictionary%602>. Tyto třídy implementovat obecné rozhraní a proto zahrnout očekávané podporu pro kolekce XAML základní implementaci.

## <a name="read-only-collections-and-initialization-logic"></a>Kolekce jen pro čtení a logiku inicializace

V rozhraní .NET Framework programování je běžný vzor návrhu, aby jakákoli vlastnost, která obsahuje hodnotu z kolekce, kolekce jen pro čtení. Tento model umožňuje instanci, která vlastní vlastnost kolekce získat lepší kontrolu nad, co se stane, že do kolekce... Konkrétně vzor zabrání náhodnému nahrazení celou existující kolekci nastavením vlastnosti. V tomto modelu, všechny přístupy do kolekce pomocí volajících místo toho je třeba pomocí volání metody nebo vlastnosti podporuje typ kolekce a/nebo relevantní kolekci rozhraní, jako <xref:System.Collections.IList>.

Použití tohoto modelu znamená, že každá třída, která zpřístupňuje vlastnost kolekce jenom pro čtení musí nejprve inicializovat tuto vlastnost pro prázdnou kolekci. Inicializace se obvykle provádí jako součást konstrukce chování pro třídu. Užitečnost pro XAML, je důležité, že tuto logiku je vždy odkazuje na výchozí konstruktor, vzhledem k tomu XAML obecně volá výchozí konstruktor před zpracováním vlastnosti (Vlastnosti kolekce nebo jinak).

## <a name="xaml-type-system-support-and-collections"></a>Podpora typu systému XAML a kolekce

Nad rámec základní mechanismy analýze XAML a naplnění nebo serializaci vlastnosti kolekce systém typů XAML, jak je implementován v rozhraní .NET Framework XAML Services zahrnuje několik funkcí návrhu, které se týkají kolekce v XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A> Vrátí hodnotu true, pokud typ XAML je založená na typ, který poskytuje podporu kolekce XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A> a <xref:System.Xaml.XamlType.IsArray%2A> dále můžete určit, které režim kolekce podporuje typ XAML. Pro vlastní XAML procesorů, které jsou založeny na rozhraní .NET Framework XAML Services a XAML systém typů, ale není založen na existující <xref:System.Xaml.XamlWriter> implementace, znalost režimu kolekce, který se používá může být nezbytné, pokud chcete zjistit, která metoda se má vyvolat pro zpracování kolekce.

3. Všechny předchozí hodnoty vlastnosti jsou potenciálně ovlivněny přepsání <xref:System.Xaml.XamlType.LookupCollectionKind%2A> typu XAML.
