---
title: Prostředky pojmenování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5b53fc383e6fc9a5f056bab4eabde9979cd734b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133555"
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
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
