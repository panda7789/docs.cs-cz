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
ms.openlocfilehash: 68419fe293dd25936aa3c1e3def10bbe8852e175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571381"
---
# <a name="designing-for-extensibility"></a>Navrhování pro rozšiřitelnost
Jeden důležitým aspektem navrhování rozhraní je Ujistěte se, že pečlivě zvážit rozšiřitelnost rozhraní Framework. To vyžaduje, abyste rozuměli tomu náklady a výhod spojených s různé mechanismy pro rozšíření. Tato kapitola vám pomůže zjistit, které mechanismů rozšíření – vytváření podtříd, události, virtuální členové, zpětná volání a tak dále – nejlépe splňují požadavky vašeho prostředí.  
  
 Existuje mnoho způsobů tak, aby měl rozšiřitelnost rozhraní. Budou v rozsahu od méně efektivní, ale levněji k velmi výkonné, ale nákladná. Každý požadavek dané rozšíření měli byste vybrat alespoň nákladná mechanismus rozšiřitelnosti, který splňuje požadavky. Uvědomte si, že je obvykle možné později přidat další rozšíření, ale nikdy vám ji rychle bez zavedení nejnovější změny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Chráněné členy](../../../docs/standard/design-guidelines/protected-members.md)  
 [Události a zpětná volání](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Virtuální členové](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrakce (abstraktní typy a rozhraní)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Základní třídy pro implementaci abstrakcí](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
