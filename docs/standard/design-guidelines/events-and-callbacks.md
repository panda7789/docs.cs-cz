---
title: Události a zpětná volání
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: KrzysztofCwalina
ms.openlocfilehash: c9ed52c5a313676baeba66f5cb79c7a56927babb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154421"
---
# <a name="events-and-callbacks"></a>Události a zpětná volání
Zpětná volání nejsou body rozšiřitelnosti, které umožňují rozhraní pro zpětné volání do uživatelského kódu prostřednictvím delegáta. Jsou tyto delegáty rozhraní Framework obvykle předat prostřednictvím parametru metody.  
  
 Události jsou zvláštním případem zpětná volání, která podporuje syntaxi pohodlný a konzistentní vzhledem k aplikacím pro poskytnutí delegáta (Obslužná rutina události). Kromě toho dokončování příkazů sady Visual Studio a návrháři poskytnutí nápovědy v rozhraní API založeného na událostech. (Viz [návrh události](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** pomocí zpětná volání umožníte uživatelům poskytnout vlastní kód, který bude proveden podle rozhraní.  
  
 **✓ CONSIDER** pomocí události umožníte uživatelům přizpůsobit chování prostředí bez nutnosti Princip objektově orientované návrhu.  
  
 **✓ DO** raději události přes prostý zpětná volání, protože jsou známější pro širší vývojářů a jsou integrované s dokončování Visual Studio.  
  
 **X AVOID** pomocí zpětná volání rozhraní API náročné na výkon.  
  
 **✓ DO** pomocí nové `Func<...>`, `Action<...>`, nebo `Expression<...>` typy místo vlastní delegáty, při definování rozhraní API s zpětných volání.  
  
 `Func<...>` a `Action<...>` představují obecných delegátů. `Expression<...>` představuje definice funkcí, které mohou být zkompilovány a následně vyvolá za běhu, ale mohou také být serializován a předat vzdálených procesů.  
  
 **✓ DO** měřit a chápat výkonu důsledky použití `Expression<...>`, místo použití `Func<...>` a `Action<...>` delegáti.  
  
 `Expression<...>` typy jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegátů. Hlavní rozdíl mezi nimi je, že delegáty jsou určena pro použití ve scénářích místní proces. výrazy jsou určené pro případech, kdy je výhodné a je to možné, k vyhodnocení výrazu v vzdálený proces nebo počítače.  
  
 **✓ DO** pochopit, jsou prováděny voláním delegáta libovolný kód a který může mít dopad na zabezpečení, správnost a kompatibility.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
