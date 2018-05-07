---
title: Kolekce a typy kolekcí v jazyku XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 5605c97b13503e18e2f698f2a19f715663052b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekce a typy kolekcí v jazyku XAML
Toto téma popisuje, jak definovat vlastnosti typů, které jsou určeny pro podporu kolekce a k podpoře syntaxe jazyka XAML pro vytvoření instance položky kolekce jako podřízené objekty element nadřazený objekt element nebo element vlastnosti.  
  
## <a name="xaml-collection-concepts"></a>Koncepty kolekce XAML  
 Koncepčně žádný vztah v jazyce XAML, je-li více podřízené položky v rámci oboru objektu elementu XAML nebo element XAML vlastnosti, musí být implementována jako kolekce. Tuto kolekci musí být přidružen konkrétní XAML vlastnost typu XAML, která je nadřazeným prvkem v této relaci. Vlastnost musí být kolekce, protože procesor XAML očekává přiřadit každou položku v značky, aby bylo nově přidané položky základní vlastnosti kolekce.  
  
 Na úrovni jazyka XAML nejsou definovány plně přesných požadavcích kolekce podpory. Pojem, kolekce může být buď seznam nebo slovník (ale ne oba) je vymezen na úrovni jazyka XAML, ale základní typy, které představují buď seznamy nebo slovníky není definován v jazyce XAML.  
  
 V rozhraní .NET Framework XAML Services je koncept XAML kolekce podporu více jasně definované z hlediska zálohování typy rozhraní .NET Framework. Konkrétně podporu XAML pro kolekce je založena na několik konceptů rozhraní .NET Framework a rozhraní API, které se používají pro seznamy a slovníků v obecné programování v rozhraní .NET Framework.  
  
1.  <xref:System.Collections.IList> Rozhraní označuje seznamu kolekce.  
  
2.  <xref:System.Collections.IDictionary> Rozhraní označuje dicionary kolekce.  
  
3.  <xref:System.Array> představuje pole a pole podporuje <xref:System.Collections.IList> metody.  
  
 V každé z těchto pojmech kolekce procesor rozhraní .NET Framework XAML Services XAML očekává, že volání `Add` metodu na konkrétní instanci typu vlastnost kolekce. Nebo ve scénáři serializace procesor XAML vytváří diskrétní instancí typ jazyka XAML pro každou položku najít v seznamu, slovníku nebo pole založené na každou kolekci konkrétní konceptu "Položky". Jsou to: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; explicitní <xref:System.Array.System%23Collections%23IList%23Item%2A> pro <xref:System.Array>.  
  
## <a name="generic-collections"></a>Obecné kolekce  
 Obecné kolekce může být užitečná pro programování obecné rozhraní .NET Framework a můžete také použít u vlastností kolekce XAML. Ale obecná rozhraní <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602> nejsou identifikovaný procesorů rozhraní .NET Framework XAML Services XAML neobecnou rovnocenné <xref:System.Collections.IList> nebo <xref:System.Collections.IDictionary>. Místo implementace rozhraní, je odvozena od třídy doporučený postup pro obecnou kolekci typů vlastností <xref:System.Collections.Generic.List%601> nebo <xref:System.Collections.Generic.Dictionary%602>. Tyto třídy implementovat rozhraní neobecnou a proto zahrnují očekávané podporu pro jazyk XAML kolekce v základní implementaci.  
  
## <a name="read-only-collections-and-initialization-logic"></a>Kolekce jen pro čtení a inicializace logiky  
 V rozhraní .NET Framework programování je běžné návrhový vzor, aby jakákoli vlastnost, která obsahuje hodnoty z kolekce jako kolekce jen pro čtení. Tento vzor umožňuje instanci, která vlastní vlastnosti kolekce, která má lepší řízení, co se stane, že do kolekce... Konkrétně vzoru zabrání náhodnému nahrazení celou existující kolekci nastavením vlastnosti. V tomto vzoru všechny přístupy do kolekce pomocí volajících místo toho je třeba při volání metody nebo vlastnosti, jako například podporovaný typ kolekce nebo rozhraní pro příslušné kolekce <xref:System.Collections.IList>.  
  
 Pomocí tohoto vzoru znamená, že žádné třída, která zveřejňuje vlastnosti jen pro čtení kolekce musí nejprve inicializovat tuto vlastnost k uchování prázdnou kolekci. Inicializace se obvykle provádí v rámci chování vytváření pro třídu. Být užitečné pro jazyk XAML, je důležité, aby tuto logiku vždy odkazuje výchozí konstruktor, protože XAML obecně volání výchozí konstruktor před zpracování vlastnosti (Vlastnosti kolekce nebo jinak).  
  
## <a name="xaml-type-system-support-and-collections"></a>Podpora systému typu XAML a kolekce  
 Nad rámec základní mechanismy analýza XAML a naplnění nebo serializaci vlastnosti kolekce systém typů XAML, jak jsou implementované v rozhraní .NET Framework XAML Services zahrnuje několik funkcí návrhu, které náleží do kolekcí v jazyce XAML.  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A> Vrátí hodnotu true, pokud je typ jazyka XAML zálohovaný pomocí typu, který poskytuje podporu kolekce XAML.  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A> a <xref:System.Xaml.XamlType.IsArray%2A> dále můžete určit, který režim kolekce podporuje typ jazyka XAML. Pro vlastní XAML procesorů, které jsou založené na rozhraní .NET Framework XAML Services a XAML zadejte systému, ale není na základě existující <xref:System.Xaml.XamlWriter> implementace, zároveň budete vědět, který režim kolekce slouží může být nezbytné, aby se vědět, jakým způsobem má být vyvolán pro kolekce zpracování.  
  
3.  Každý z předchozí hodnoty vlastností potenciálně vliv přepsání z <xref:System.Xaml.XamlType.LookupCollectionKind%2A> na typ jazyka XAML.
