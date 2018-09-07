---
title: Chráněné členy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068973"
---
# <a name="protected-members"></a>Chráněné členy
Chráněné členy samy o sobě neposkytuje žádné rozšíření, ale budou mít rozšiřitelnost prostřednictvím vytváření podtříd výkonnější. Umožňuje vystavit rozšířené možnosti vlastního nastavení bez zbytečně komplikují hlavní veřejného rozhraní.  
  
 Návrháři Framework muset být opatrní při práci s chráněné členy, protože název "protected" můžete poskytnout o zabezpečení. Všem uživatelům se bude moct podtřídy nezapečetěné třídy a přístupu k chráněným členům a stejné tak obranné drželi osvědčených kódovacích postupů použít pro veřejné členy platí pro chráněné členy.  
  
 **✓ CONSIDER** pomocí chráněné členy pro vlastní nastavení.  
  
 **✓ DO** považovat chráněné členy v nezapečetěných třídy jako veřejné pro účely analýzy zabezpečení, dokumentace a kompatibility.  
  
 Kdokoli na nich můžou dědit ze třídy a přistupovat k chráněným členům.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
