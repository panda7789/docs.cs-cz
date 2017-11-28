---
title: "Události a zpětná volání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 217e9eae3540e0a20afd0888d24803285d6352b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="events-and-callbacks"></a>Události a zpětná volání
Zpětná volání jsou body rozšiřitelnosti, které umožňují rozhraní pro zpětné volání do kódu uživatele prostřednictvím delegáta. Tyto Delegáti jsou obvykle předaný rozhraní prostřednictvím parametru metody.  
  
 Události jsou ve speciálním případě zpětná volání, který podporuje pohodlný a konzistentní syntaxe pro zadávání delegáta (obslužné rutiny události). Kromě toho Visual Studio dokončování a návrháři poskytnutí nápovědy v pomocí rozhraní API založené na události. (Viz [událostí návrhu](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ ZVAŽTE** pomocí zpětná volání umožníte uživatelům poskytnout vlastní kód, který bude proveden podle rozhraní.  
  
 **✓ ZVAŽTE** pomocí události umožníte uživatelům přizpůsobit chování prostředí bez nutnosti Princip objektově orientované návrhu.  
  
 **PROVEĎTE ✓** raději události přes prostý zpětná volání, protože jsou známější pro širší vývojářů a jsou integrované s dokončování Visual Studio.  
  
 **X nepoužívejte** pomocí zpětná volání rozhraní API náročné na výkon.  
  
 **PROVEĎTE ✓** pomocí nové `Func<...>`, `Action<...>`, nebo `Expression<...>` typy místo vlastní delegáty, při definování rozhraní API s zpětných volání.  
  
 `Func<...>`a `Action<...>` představují obecní delegáti. `Expression<...>`Definice představuje funkcí, které můžete zkompilovat a následně vyvolat za běhu, ale mohou také být serializované a předaný vzdálených procesů.  
  
 **PROVEĎTE ✓** měřit a chápat výkonu důsledky použití `Expression<...>`, místo použití `Func<...>` a `Action<...>` delegáti.  
  
 `Expression<...>`typy jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegáti. Hlavní rozdíl mezi nimi je, že delegáty jsou určena pro použití ve scénářích místní proces. výrazy jsou určeny k případech, kdy je výhodné a možných při vyhodnocování výrazu v vzdáleného procesu nebo počítači.  
  
 **PROVEĎTE ✓** pochopit, jsou prováděny voláním delegáta libovolný kód a který může mít dopad na zabezpečení, správnost a kompatibility.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)
