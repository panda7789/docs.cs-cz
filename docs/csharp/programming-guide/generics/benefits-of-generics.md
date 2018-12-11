---
title: Výhody obecných typů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
ms.openlocfilehash: f97d3ce7a67638719d02c31879c00679405118bc
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245009"
---
# <a name="benefits-of-generics-c-programming-guide"></a>Výhody obecných typů (Průvodce programováním v C#)
Obecné typy poskytují řešení k omezení v dřívějších verzích common language runtime a ve kterém se provádí generalizace typy přetypování do a z univerzální základní typ jazyka C# <xref:System.Object>. Vytvořením obecné třídy můžete vytvořit kolekci, která je typově bezpečné v době kompilace.  
  
 Omezení použití negenerická kolekce tříd mohou prokázat a napište krátký program, který používá <xref:System.Collections.ArrayList> kolekce tříd z knihovny tříd rozhraní .NET. Instance <xref:System.Collections.ArrayList> třída ukládat jakýkoli typ hodnotou nebo odkazem.  
  
 [!code-csharp[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Ale tato výhoda něco stojí. Jakýkoli typ odkazu nebo hodnoty, který je přidán do <xref:System.Collections.ArrayList> je implicitně povýšení na <xref:System.Object>. Pokud položky jsou typy hodnot, musí být zabaleny když se přidají do seznamu a rozbalit, pokud jsou načteny. Přetypování a operace zabalení a rozbalení snížení výkonu. účinek zabalení a rozbalení může být velmi důležité ve scénářích, kde musí iterovat rozsáhlých kolekcí.  
  
 Další omezení je nedostatek kontrolu typu za kompilace protože <xref:System.Collections.ArrayList> přetypování všechno <xref:System.Object>, neexistuje žádný způsob v době kompilace zabráníte dělali něco takovou situaci kód klienta:  
  
 [!code-csharp[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 I když je zcela přijatelné a někdy úmyslné, pokud vytváříte kolekci heterogenní kombinovaných řetězců a `ints` v jediném <xref:System.Collections.ArrayList> je pravděpodobně programovací chyba, a k této chybě nebudou zjištěny do modulu runtime.  
  
 Ve verzích 1.0 a 1.1 jazyka C# se můžete vyhnout nebezpečí zobecněný kód v kolekci tříd rozhraní .NET Framework základní třídy knihovny pouze vlastní kolekce konkrétního typu zápis. Samozřejmě protože takové třídy není opakovaně použitelné pro více než jeden datový typ, dojít ke ztrátě výhod Generalizace a je nutné přepsat třídy pro každý typ, který se uloží.  
  
 Co <xref:System.Collections.ArrayList> a další podobné třídy opravdu potřebujete je způsob, jak určit, na základě jednotlivé instance, které mají v úmyslu použít konkrétní datový typ v klientském kódu. Který by eliminuje nutnost přetypování nahoru na <xref:System.Object> a by také umožňují kontrolu typů kompilátoru. Jinými slovy <xref:System.Collections.ArrayList> vyžaduje, aby parametr typu. To je přesně co poskytují obecné typy. V Obecné <xref:System.Collections.Generic.List%601> kolekce v <xref:System.Collections.Generic> obor názvů, stejné operace přidání položky do kolekce vypadá takto:  
  
 [!code-csharp[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 Pro klientský kód pouze přidat syntaxe <xref:System.Collections.Generic.List%601> ve srovnání s <xref:System.Collections.ArrayList> je argument typu v deklaraci a instance. Po této o něco víc o kódování složitost, můžete vytvořit seznam, který je nejen bezpečnější než <xref:System.Collections.ArrayList>, ale také výrazně rychlejší, zejména v případě, že položky seznamu jsou typy hodnot.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
- [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)  
- [Pokyny pro kolekce](../../../standard/design-guidelines/guidelines-for-collections.md)   
