---
title: Prostředky pojmenování
description: Přečtěte si pokyny pro pojmenování prostředků v .NET, které jsou podobné pravidlům pro pojmenování vlastností.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 765337bcf9fad4f9a8c9272a15b5c77d02770471
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768245"
---
# <a name="naming-resources"></a>Prostředky pojmenování
Vzhledem k tomu, že lokalizovatelné prostředky mohou být odkazovány prostřednictvím určitých objektů, jako by se jednalo o vlastnosti, pokyny pro pojmenování prostředků jsou podobné pravidlům vlastností.

 ✔️ používat PascalCasing v klíčích prostředků.

 ✔️ Zadejte popisný název místo krátkých identifikátorů.

 ❌Nepoužívejte klíčová slova specifická pro jazyky modulu CLR.

 ✔️ v názvech prostředků používat pouze alfanumerické znaky a podtržítka.

 ✔️ použít následující zásady vytváření názvů pro prostředky zpráv o výjimkách.

 Identifikátor prostředku by měl být název typu výjimky a krátký identifikátor výjimky:

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Pokyny pro pojmenování](naming-guidelines.md)
