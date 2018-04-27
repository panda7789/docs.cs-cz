---
title: Základní třídy pro implementaci abstrakce
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 70d107d96576b8cafe9e76135c00bd2c635f2d7e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="base-classes-for-implementing-abstractions"></a>Základní třídy pro implementaci abstrakce
Přesněji řečeno třídu změní základní třídy, pokud je z něj odvozenou jiné třídy. Pro účely této části je však základní třídu třídu určena především k poskytování běžné abstrakce nebo pro jiné třídy znovu použít některé výchozí implementace ale dědičnosti. Základní třídy se obvykle nacházejí uprostřed hierarchie dědičnosti mezi několik vlastní implementace v dolní části a abstrakci na nejnižší úrovni hierarchie.  
  
 Pro implementaci abstrakce představují implementace pomocné rutiny. Je například jeden z rozhraní Framework abstrakci pro seřazené kolekce položek <xref:System.Collections.Generic.IList%601> rozhraní. Implementace <xref:System.Collections.Generic.IList%601> není triviální, a proto rozhraní Framework poskytuje několik základní třídy, jako například <xref:System.Collections.ObjectModel.Collection%601> a <xref:System.Collections.ObjectModel.KeyedCollection%602>, který slouží jako pomocné rutiny pro implementaci vlastní kolekce.  
  
 Třídy Base obvykle nejsou vhodná, která bude sloužit jako abstrakce sami, protože se zpravidla obsahuje příliš mnoho implementace. Například `Collection<T>` základní třída obsahuje spoustu implementace souvisí se skutečností, že implementuje neobecné `IList` rozhraní (aby lépe integrovat neobecné kolekce) a na skutečnost, že je kolekce položek uložená v paměti v jednom z jeho polí.  
  
 Jak je uvedeno výše, základní třídy pro uživatele, kteří potřebují k implementaci abstrakce poskytnout neocenitelnou pomocí nápovědy, ale současně se může být důležité odpovědnosti. Jejich přidejte útoku a zvýšit hloubku hierarchie dědičnosti a proto koncepčně zkomplikovat rozhraní. Proto základní třídy by měl používat pouze v případě, že poskytují významné zlepšení uživatelům rozhraní. Budou se vyhnout, pokud poskytují hodnotu pouze pro implementátory architekturu, ve kterém případu delegování interní implementace místo dědění ze základní třídy silného považovat.  
  
 **✓ ZVAŽTE** provedení základní třídy abstraktní i v případě, že neobsahují žádné abstraktní členy. To jasně komunikuje uživatelům určený výhradně k možné zdědit z třídy.  
  
 **✓ ZVAŽTE** umístění základních tříd do samostatného oboru názvů z nejdůležitějších scénář typů. Podle definice základní třídy jsou určené pro scénáře pokročilé rozšiřitelnost a proto nejsou zajímavé pro většinu uživatelů.  
  
 **X nepoužívejte** pojmenování základní třídy s příponou "Základní", pokud třída je určena pro použití v veřejná rozhraní API.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
