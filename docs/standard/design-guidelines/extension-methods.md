---
title: Metody rozšíření
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6247b6d1718f43d4b05d585cc12a05c5e0cc2035
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="extension-methods"></a>Metody rozšíření
Rozšiřující metody jsou jazyk funkce, která umožňuje statické metody, která se má volat pomocí volání syntaxi metody instance. Tyto metody vyžaduje minimálně jeden parametr, který představuje instanci, kterou je metoda má být použito.  
  
 Třídu, která definuje tyto rozšiřující metody se označuje jako "sponzor" třída a ho musí být deklarována jako statické. Použití metod rozšíření, jeden musíte importovat definice třídy sponzor obor názvů.  
  
 **X nepoužívejte** frivolously definování rozšiřující metody, hlavně na typech nevlastníte.  
  
 Pokud jste vlastníkem zdrojového kódu typu, zvažte použití metody normální instanci. Pokud nevlastníte a které chcete přidat metodu, buďte velmi opatrní. Volná použití metody rozšíření má potenciál zbytečného rozhraní API typů, které nebyly navrženy tak, aby tyto metody.  
  
 **✓ ZVAŽTE** metodami rozšíření v některém z následujících scénářů:  
  
-   Zajistit pomocné funkce, které jsou relevantní pro každou implementaci rozhraní, pokud uvedená funkce může být napsán z hlediska základní rozhraní. Je to proto, že konkrétní implementace v opačném případě nemůže být přiřazen rozhraní. Například `LINQ to Objects` operátory jsou implementované jako rozšiřující metody pro všechny <xref:System.Collections.Generic.IEnumerable%601> typy. Proto všechny `IEnumerable<>` implementace je automaticky povolené LINQ.  
  
-   Když metoda instance by vznikla závislost na nějaký typ, ale tato závislost by došlo k přerušení pravidla správy závislostí. Například závislost z <xref:System.String> k <xref:System.Uri?displayProperty=nameWithType> je pravděpodobně není žádoucí a tak `String.ToUri()` instance metoda vrací `System.Uri` by nesprávný návrhu z hlediska správy závislostí. Statické rozšíření metoda `Uri.ToUri(this string str)` vrácení `System.Uri` by mnohem lepší návrh.  
  
 **X nepoužívejte** definování rozšiřující metody na <xref:System.Object?displayProperty=nameWithType>.  
  
 VB uživatelé nebudou moci volat tyto metody pro objekt odkazů pomocí syntaxe využívající metody rozšíření. Jazyk Visual Basic nepodporuje volání těchto metod, protože deklarace odkaz jako objekt vynutí všechna volání metod na něm být pozdní vázán v jazyce Visual Basic, (skutečného člena s názvem je určena za běhu), zatímco vazby na rozšiřující metody jsou určeny při kompilaci (časná vázaný).  
  
 Všimněte si, že obecných zásad platí pro další jazyky, kde je přítomen stejné chování vazby, nebo pokud rozšíření metody nejsou podporovány.  
  
 **X nesmí** umístění rozšiřujících metod v jako typ rozšířené o stejný obor názvů, pokud je pro přidání metody do rozhraní nebo správě závislosti.  
  
 **X nepoužívejte** definování dvě nebo více metod rozšíření se stejným podpisem, i v případě, že jsou umístěny v různých oborech názvů.  
  
 **✓ ZVAŽTE** definování rozšiřující metody v jako typ rozšířené o stejný obor názvů, pokud typ je rozhraní, a pokud rozšiřující metody jsou určené pro použití ve většině nebo všem případů.  
  
 **X nesmí** definovat rozšiřující metody, které implementují funkce v obory názvů, které jsou obvykle spojené s jinými funkcemi. Místo toho je definujte v oboru názvů související s funkcí, ke které patří.  
  
 **X nepoužívejte** obecné názvy oborů názvů vyhrazený pro metody rozšíření (například "rozšíření"). Použijte popisný název (například "směrování") místo.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
