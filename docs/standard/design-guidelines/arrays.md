---
title: Pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 30277507050091de6b1e9293401d61ac5e351a1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280605"
---
# <a name="arrays"></a>Pole
✔️ preferovat používání kolekcí v polích ve veřejných rozhraních API. V části [kolekce](guidelines-for-collections.md) najdete podrobné informace o tom, jak zvolit mezi kolekcemi a poli.

 ❌Nepoužívejte pole polí jen pro čtení. Pole, které je samotné, je jen pro čtení a nelze jej změnit, ale prvky v poli lze změnit.

 ✔️ Zvažte použití vícenásobných polí namísto multidimenzionálních polí.

 Vícenásobné pole je pole s prvky, které jsou také pole. Pole, která tvoří prvky, mohou mít různé velikosti, což vede k menšímu množství nevyužitého prostoru pro některé sady dat (například zhuštěné matrice) ve srovnání s multidimenzionálními poli. Kromě toho CLR optimalizuje operace indexu u vícenásobných polí, takže může v některých scénářích vykazovat lepší běhový výkon.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Pokyny k návrhu architektury](index.md)
- [Pokyny k použití](usage-guidelines.md)
