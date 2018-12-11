---
title: Prostředky pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: KrzysztofCwalina
ms.openlocfilehash: 5331c82069bb289c282e746841f5a328e2e628f2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130869"
---
# <a name="naming-resources"></a>Prostředky pojmenování
Protože lokalizovatelné prostředky může být odkazováno prostřednictvím určitých objektů, jako kdyby byly vlastnosti, pokyny pro pojmenování prostředků jsou podobné pokyny pro vlastnost.  
  
 **✓ DO** použít PascalCasing v klíčů prostředku.  
  
 **✓ DO** zadat popisný místo krátké identifikátory.  
  
 **X DO NOT** používat klíčová slova jazyka hlavní jazyky CLR.  
  
 **✓ DO** použijte pouze alfanumerické znaky a podtržítka v pojmenování prostředky.  
  
 **✓ DO** použít následující konvence pro prostředků zprávy výjimek.  
  
 Identifikátor prostředku by měl být název typu výjimky a krátký identifikátor výjimky:  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
