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
author: KrzysztofCwalina
ms.openlocfilehash: 94900dee72230a1b9d099d78168acc508af62af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026455"
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
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
