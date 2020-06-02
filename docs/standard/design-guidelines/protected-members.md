---
title: Chránění členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: afcb92e48996d594fcedc5b579922b179f754b9d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286116"
---
# <a name="protected-members"></a>Chránění členové
Chránění členové samy o sebe neposkytují žádné rozšiřitelnosti, ale mohou zvýšit výkon pomocí podtříd. Dají se použít k vystavení pokročilých možností přizpůsobení, aniž by to zbytečně zkomplikovat hlavní veřejné rozhraní.

 Návrháři architektury musí být opatrní s chráněnými členy, protože název chráněný může mít nepravdivý smysl zabezpečení. Kdokoli může podtřídit nezapečetěnou třídu a přistupovat k chráněným členům, takže všechny stejné postupy kódování obrannou linií použité pro veřejné členy se vztahují i na chráněné členy.

 ✔️ Zvažte použití chráněných členů pro pokročilé přizpůsobení.

 ✔️ zacházet s chráněnými členy v nezapečetěných třídách jako veřejné pro účely zabezpečení, dokumentace a analýzy kompatibility.

 Kdokoli může dědit z třídy a přistupovat k chráněným členům.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Navrhování pro rozšiřitelnost](designing-for-extensibility.md)
