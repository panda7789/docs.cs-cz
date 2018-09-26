---
title: Navrhování pro rozšiřitelnost
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157451"
---
# <a name="designing-for-extensibility"></a>Navrhování pro rozšiřitelnost
Jeden důležitý aspekt návrhu rozhraní, je zajistit, že pečlivě zvážit rozšíření rozhraní framework. Tento postup vyžaduje, že rozumíte nákladů a přínosů přidružené různé mechanismy rozšiřitelnosti. Tato kapitola vám pomůže rozhodnout, které mechanismus rozšíření – vytváření podtříd, události, virtuální členy, zpětná volání a tak dále – můžete nejlíp vyhovovat požadavkům vaší architektury.  
  
 Existuje mnoho způsobů, jak povolit rozšíření v rozhraní. Jsou v rozsahu od méně efektivní, ale levnějších do velmi výkonné, ale drahé. Pro všechny požadavky dané rozšíření měli byste vybrat minimální nákladnou mechanismus rozšiřitelnosti, který splňuje požadavky. Mějte na paměti, že je obvykle možné případná další rozšíření později, ale nikdy udělat to okamžitě bez vnášení nejnovější změny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Chráněné členy](../../../docs/standard/design-guidelines/protected-members.md)  
 [Události a zpětná volání](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Virtuální členové](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrakce (abstraktní typy a rozhraní)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Základní třídy pro implementaci abstrakcí](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
