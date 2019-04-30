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
author: KrzysztofCwalina
ms.openlocfilehash: 7d940f10799df2efc6c6d031781e1ef7cf777dd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937394"
---
# <a name="protected-members"></a>Chránění členové
Chráněné členy samy o sobě neposkytuje žádné rozšíření, ale budou mít rozšiřitelnost prostřednictvím vytváření podtříd výkonnější. Umožňuje vystavit rozšířené možnosti vlastního nastavení bez zbytečně komplikují hlavní veřejného rozhraní.  
  
 Návrháři Framework muset být opatrní při práci s chráněné členy, protože název "protected" můžete poskytnout o zabezpečení. Všem uživatelům se bude moct podtřídy nezapečetěné třídy a přístupu k chráněným členům a stejné tak obranné drželi osvědčených kódovacích postupů použít pro veřejné členy platí pro chráněné členy.  
  
 **✓ CONSIDER** pomocí chráněné členy pro vlastní nastavení.  
  
 **✓ DO** považovat chráněné členy v nezapečetěných třídy jako veřejné pro účely analýzy zabezpečení, dokumentace a kompatibility.  
  
 Kdokoli na nich můžou dědit ze třídy a přistupovat k chráněným členům.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
