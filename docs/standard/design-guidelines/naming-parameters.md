---
title: Parametry pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 0e5b33839372e303b96bd6b84949f9a82da2f689
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646617"
---
# <a name="naming-parameters"></a>Parametry pojmenování
Nad rámec zřejmé z důvodu čitelnosti je potřeba postupovat podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když poskytují vizuální návrh nástroje technologie Intellisense a procházení funkce třídy.  
  
 **✓ DO** použít camelCasing v názvech parametrů.  
  
 **✓ DO** použít parametr popisné názvy.  
  
 **✓ CONSIDER** pomocí názvů založených na parametr význam, nikoli typ parametru.  
  
### <a name="naming-operator-overload-parameters"></a>Pojmenovávání parametrů přetížení operátoru  
 **✓ DO** použít `left` a `right` pro názvy parametrů přetížení binární operátor Pokud neexistuje žádný význam na parametry.  
  
 **✓ DO** použít `value` pro unární operátor přetížení názvy parametrů, pokud neexistuje žádný význam na parametry.  
  
 **✓ CONSIDER** smysluplný názvy pro operátor přetížení parametry, pokud tento postup zvětší významné zlepšení.  
  
 **X DO NOT** používání zkratky nebo číselné indexů pro operátor přetížení názvy parametrů.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
