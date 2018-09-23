---
title: Metody rozšíření
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bfc2e6def94d0830df4a4cdf738cdeef106de9f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703528"
---
# <a name="extension-methods"></a>Metody rozšíření
Rozšiřující metody jsou jazyk funkce, která umožňuje statické metody, která se má volat pomocí syntaxe volání metody instance. Tyto metody musí přijmout nejmíň jeden parametr, který představuje instanci, kterou metoda se má operace provést.  
  
 Třídy, která definuje tyto rozšiřující metody jsou označovány jako "sponzor" třídy a musí být deklarován jako statické. Chcete-li použít rozšiřující metody, jeden musí importujte obor názvů definování třídy sponzor.  
  
 **X AVOID** frivolously definování rozšiřující metody, hlavně na typech nevlastníte.  
  
 Pokud vlastníte zdrojový kód typu, zvažte použití metody normální instanci aplikace. Pokud nevlastníte, a je třeba přidat metodu, buďte velmi opatrní. Liberální použití metody rozšíření se dá potenciálně nebudou zbytečně zabírat rozhraní API typů, které nebyly navrženy tak, aby tyto metody.  
  
 **✓ CONSIDER** metodami rozšíření v některém z následujících scénářů:  
  
-   K poskytují pomocná funkce, které jsou relevantní pro každou implementaci rozhraní, pokud se říká, že funkce může být napsán z hlediska základní rozhraní. Je to proto, že konkrétní implementace nelze přiřadit jinak rozhraní. Například `LINQ to Objects` operátory jsou implementovány jako rozšiřující metody pro všechny <xref:System.Collections.Generic.IEnumerable%601> typy. Díky tomu se některé `IEnumerable<>` implementace je automaticky povolen LINQ.  
  
-   Pokud by metodu instance zavést závislost na nějaký typ, ale tato závislost by narušil pravidla správy závislostí. Například závislost z <xref:System.String> k <xref:System.Uri?displayProperty=nameWithType> je pravděpodobně není žádoucí a proto `String.ToUri()` chybí metoda instance `System.Uri` by chybný návrhu z hlediska správy závislostí. Metoda statické rozšíření `Uri.ToUri(this string str)` vrácení `System.Uri` by mnohem lepší návrh.  
  
 **X AVOID** definování rozšiřující metody na <xref:System.Object?displayProperty=nameWithType>.  
  
 VB uživatelé nebudou moct volat tyto metody pro odkazy na objekty pomocí syntaxe metody rozšíření. VB nepodporuje volání těchto metod, protože deklarace odkazu jako objekt vynutí všechna volání metod na něm nestíháte vázán v jazyce Visual Basic, (skutečný člen s názvem je určeno za běhu), zatímco vazby na metody rozšíření jsou určeny při kompilaci (již v rané fázi ven).  
  
 Všimněte si, že pravidlo platí do jiných jazyků, kde je k dispozici stejné chování vazby nebo pokud rozšíření metody nejsou podporovány.  
  
 **X DO NOT** umístění rozšiřujících metod v jako typ rozšířené o stejný obor názvů, pokud je pro přidání metody do rozhraní nebo správě závislosti.  
  
 **X AVOID** definování dvě nebo více metod rozšíření se stejným podpisem, i v případě, že jsou umístěny v různých oborech názvů.  
  
 **✓ CONSIDER** definování rozšiřující metody v jako typ rozšířené o stejný obor názvů, pokud typ je rozhraní, a pokud rozšiřující metody jsou určené pro použití ve většině nebo všem případů.  
  
 **X DO NOT** definovat rozšiřující metody, které implementují funkce v obory názvů, které jsou obvykle spojené s jinými funkcemi. Místo toho je definujte v přidružené k této funkci, ke které patří do oboru názvů.  
  
 **X AVOID** obecné názvy oborů názvů vyhrazený pro metody rozšíření (například "rozšíření"). Použijte popisný název (například "směrování") místo toho.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
