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
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709410"
---
# <a name="events-and-callbacks"></a>Události a zpětná volání
Zpětná volání jsou body rozšiřitelnosti, které umožňují rozhraní volat zpět do uživatelského kódu prostřednictvím delegáta. Tyto delegáty jsou obvykle předávány rozhraní prostřednictvím parametru metody.  
  
 Události jsou zvláštním případem zpětných volání, která podporují praktické a konzistentní syntaxi pro poskytnutí delegáta (obslužná rutina události). Kromě toho dokončování příkazů sady Visual Studio a návrháři poskytují podporu pro používání rozhraní API založených na událostech. (Viz [návrh události](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** pomocí zpětná volání umožníte uživatelům poskytnout vlastní kód, který bude proveden podle rozhraní.  
  
 **✓ CONSIDER** pomocí události umožníte uživatelům přizpůsobit chování prostředí bez nutnosti Princip objektově orientované návrhu.  
  
 **✓ DO** raději události přes prostý zpětná volání, protože jsou známější pro širší vývojářů a jsou integrované s dokončování Visual Studio.  
  
 **X AVOID** pomocí zpětná volání rozhraní API náročné na výkon.  
  
 **✓ DO** pomocí nové `Func<...>`, `Action<...>`, nebo `Expression<...>` typy místo vlastní delegáty, při definování rozhraní API s zpětných volání.  
  
 `Func<...>` a `Action<...>` reprezentují Obecné delegáty. `Expression<...>` představuje definice funkcí, které lze zkompilovat a následně vyvolávat za běhu, ale mohou být také serializovány a předány vzdáleným procesům.  
  
 **✓ DO** měřit a chápat výkonu důsledky použití `Expression<...>`, místo použití `Func<...>` a `Action<...>` delegáti.  
  
 typy `Expression<...>` jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegáty. Hlavním rozdílem mezi nimi je to, že Delegáti mají být použiti v rámci scénářů místních procesů; výrazy jsou určené pro případy, kdy je výhodné a možné vyhodnotit výraz ve vzdáleném procesu nebo počítači.  
  
 **✓ DO** pochopit, jsou prováděny voláním delegáta libovolný kód a který může mít dopad na zabezpečení, správnost a kompatibility.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
