---
title: "Výhody obecných typů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f46a328208b49aa33130a020e1a85b6f7aa7d97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="benefits-of-generics-c-programming-guide"></a>Výhody obecných typů (Průvodce programováním v C#)
Obecné typy poskytují řešení k omezení v dřívějších verzích modul common language runtime a ve kterém se provádí generalizace typy přetypování z universal základní typ a jazyk C# <xref:System.Object>. Vytvořením obecné třídy můžete vytvořit kolekci, která je bezpečnost typů v době kompilace.  
  
 Omezení používání negenerická kolekce tříd prokázat zápis krátký program, který používá <xref:System.Collections.ArrayList> třídy kolekce v knihovně tříd rozhraní .NET Framework. <xref:System.Collections.ArrayList>je třída vysoce vhodnou kolekci, která lze použít bez úprav pro ukládání libovolného typu hodnotou nebo odkazem.  
  
 [!code-csharp[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Ale tato výhoda se dodává s náklady. Hodnotou nebo odkazem typ, který je přidán do <xref:System.Collections.ArrayList> je implicitně přetypování nahoru k <xref:System.Object>. Pokud položky jsou typy hodnot, se musí zabalená, když jsou přidány do seznamu a nezabalený při načtení. Přetypování a operace zabalení a rozbalení snížit výkon; účinek zabalení a rozbalení může být velmi důležité ve scénářích, kde musí iterace v rozsáhlých kolekcí.  
  
 Další omezení je nedostatek typu kompilaci kontrolu. protože <xref:System.Collections.ArrayList> vrhá všechno k <xref:System.Object>, neexistuje žádný způsob při kompilaci kódu klienta zabránit dělat něco jako je tato:  
  
 [!code-csharp[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 I když je zcela přijatelné a někdy záměrné, pokud vytváříte kolekci heterogenní kombinovaných řetězců a `ints` v jediném <xref:System.Collections.ArrayList> může být chybě programování, a tato chyba nebudou zjištěna dokud modulu runtime.  
  
 V verze 1.0 a 1.1 jazyka C# se můžete vyhnout nebezpečích zobecněný kód v kolekce tříd rozhraní .NET Framework – základní třída knihovny pouze zápis vlastní typ konkrétní kolekce. Samozřejmě protože taková třída není opakovaně použitelné pro více než jeden typ dat, ztratíte výhod Generalizace a máte přepsání třídu pro každý typ, který se uloží.  
  
 Co <xref:System.Collections.ArrayList> a další podobné třídy skutečně potřebujete je způsob, jak kód klienta k určení, na základě jednotlivých instancí konkrétní datový typ, který mají v úmyslu použít. Který by eliminují nutnost použití přetypování nahoru k `T:System.Object` a by také umožnit kompilátor pro kontrolu typu. Jinými slovy <xref:System.Collections.ArrayList> potřebuje parametr typu. Který je právě co poskytují obecné typy. V Obecné <xref:System.Collections.Generic.List%601> kolekce v `N:System.Collections.Generic` obor názvů, stejné operace přidání položky do kolekce vypadá takto:  
  
 [!code-csharp[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 Pro kód klienta jediný přidat syntaxi společně s <xref:System.Collections.Generic.List%601> ve srovnání s <xref:System.Collections.ArrayList> je argument typu deklarace a vytváření instancí. Po této složitost něco víc kódování, můžete vytvořit seznam, který není pouze bezpečnější než <xref:System.Collections.ArrayList>, ale také výrazně rychlejší, zejména v případě, že položky seznamu jsou typy hodnot.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
 [Osvědčené postupy pro kolekce](http://go.microsoft.com/fwlink/?LinkId=112403)
