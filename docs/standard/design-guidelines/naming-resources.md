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
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709163"
---
# <a name="naming-resources"></a>Prostředky pojmenování
Vzhledem k tomu, že lokalizovatelné prostředky mohou být odkazovány prostřednictvím určitých objektů, jako by se jednalo o vlastnosti, pokyny pro pojmenování prostředků jsou podobné pravidlům vlastností.  
  
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
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
