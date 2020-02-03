---
title: Pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741803"
---
# <a name="arrays"></a>Pole
✔️ preferovat používání kolekcí v polích ve veřejných rozhraních API. V části [kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) najdete podrobné informace o tom, jak zvolit mezi kolekcemi a poli.

 ❌ pole nepoužívají pole jen pro čtení. Pole, které je samotné, je jen pro čtení a nelze jej změnit, ale prvky v poli lze změnit.

 ✔️ Zvažte použití vícenásobných polí namísto multidimenzionálních polí.

 Vícenásobné pole je pole s prvky, které jsou také pole. Pole, která tvoří prvky, mohou mít různé velikosti, což vede k menšímu množství nevyužitého prostoru pro některé sady dat (například zhuštěné matrice) ve srovnání s multidimenzionálními poli. Kromě toho CLR optimalizuje operace indexu u vícenásobných polí, takže může v některých scénářích vykazovat lepší běhový výkon.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
