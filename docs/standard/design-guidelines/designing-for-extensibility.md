---
title: Navrhování pro rozšiřitelnost
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709462"
---
# <a name="designing-for-extensibility"></a>Navrhování pro rozšiřitelnost
Jedním z důležitých aspektů návrhu rozhraní je zajistit pečlivě zvážení rozšiřitelnosti rozhraní. To vyžaduje, abyste porozuměli nákladům a výhodám přidruženým k různým mechanismům rozšiřitelnosti. Tato kapitola vám pomůže určit, který z mechanismů rozšíření – podtříd, události, virtuální členy, zpětná volání a tak dále, mohou nejlépe splňovat požadavky vašeho rozhraní.  
  
 Existuje mnoho způsobů, jak v rozhraních zakázat rozšiřitelnost. Jsou v rozsahu od méně výkonných, ale méně nákladné až po velmi výkonné, ale nákladné. Pro všechny požadavky na rozšiřitelnost byste měli zvolit nejméně nákladný mechanismus rozšiřitelnosti, který splňuje požadavky. Mějte na paměti, že je obvykle možné přidat další rozšiřitelnost později, ale nemůžete ji nikdy vzít, aniž byste museli zavádět zásadní změny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Chráněné členy](../../../docs/standard/design-guidelines/protected-members.md)  
 [Události a zpětná volání](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Virtuální členové](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrakce (abstraktní typy a rozhraní)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Základní třídy pro implementaci abstrakcí](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
