---
title: Parametry pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709176"
---
# <a name="naming-parameters"></a>Parametry pojmenování
Kromě zjevného důvodu čitelnosti je důležité postupovat podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když nástroje vizuálního návrhu poskytují funkce IntelliSense a procházení tříd.  
  
 **✓ DO** použít camelCasing v názvech parametrů.  
  
 **✓ DO** použít parametr popisné názvy.  
  
 **✓ CONSIDER** pomocí názvů založených na parametr význam, nikoli typ parametru.  
  
### <a name="naming-operator-overload-parameters"></a>Parametry přetížení operátoru názvů  
 **✓ DO** použít `left` a `right` pro názvy parametrů přetížení binární operátor Pokud neexistuje žádný význam na parametry.  
  
 **✓ DO** použít `value` pro unární operátor přetížení názvy parametrů, pokud neexistuje žádný význam na parametry.  
  
 **✓ CONSIDER** smysluplný názvy pro operátor přetížení parametry, pokud tento postup zvětší významné zlepšení.  
  
 **X DO NOT** používání zkratky nebo číselné indexů pro operátor přetížení názvy parametrů.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
