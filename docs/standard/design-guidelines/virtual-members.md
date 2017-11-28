---
title: "Virtuální členové"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 56838fc4c1c1e7cb8723beee3f0e6b23515d43f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-members"></a>Virtuální členové
Virtuální členové lze přepsat, čímž dojde ke změně chování podtřídy. Jsou velmi podobné zpětná volání z hlediska rozšiřitelnosti, které poskytují, ale jsou lepší z hlediska provádění výkonu a využití paměti. Virtuální členové zaregistrované navíc přirozenější ve scénářích, které vyžadují speciální vytváření druh existující typ (specializace).  
  
 Virtuální členové vyšší výkon než zpětná volání a události, ale neprovádět lépe než nevirtuálních metody.  
  
 Hlavní nevýhodou virtuální členové je, že chování člena virtuální může upravit pouze v době kompilace. Chování zpětné volání lze upravit za běhu.  
  
 Virtuální členové, jako je zpětných volání (a může být více než zpětná volání), jsou nákladná pro návrh, testování a udržovat, protože všechny volání člena virtuální mohou být přepsána nastaveními v nepředvídatelnými způsoby a mohou spustit libovolný kód. Kromě toho mnohem víc úsilí většinou vyžaduje jasně definovat kontrakt virtuální členové tak, aby vyšší náklady na návrh a dokumentaci jejich.  
  
 **X nesmí** zkontrolujte virtuální členy, pokud máte dobrý důvod k tomu a jste si vědomi veškeré náklady související s návrh, testování a údržbě virtuální členy.  
  
 Virtuální členové jsou menší dovolí z hlediska změn, které můžete provedeny k nim, aniž by vás kompatibility. Navíc jsou nižší než nevirtuálních členy nejčastěji, protože nejsou vloženou obslužnou volání virtuální členové.  
  
 **✓ ZVAŽTE** omezení rozšiřitelnost pouze co je to nezbytně nutné.  
  
 **PROVEĎTE ✓** raději chráněné usnadnění přes veřejnou dostupnost pro virtuální členy. Veřejné členy by měl poskytovat rozšiřitelnost (v případě potřeby) pomocí volání do chráněného člena virtuální.  
  
 Veřejné členy třídy by měl poskytovat správnou sadu funkcí pro přímé příjemce této třídy. Virtuální členové jsou určeny k přepsání v podtřídách a chráněné usnadnění je skvělý způsob, jak obor všechny body rozšiřitelnosti virtuální kterém můžou použít.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
