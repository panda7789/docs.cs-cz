---
title: "Abstrakce (abstraktní typy a rozhraní)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrakce (abstraktní typy a rozhraní)
Abstrakci je typ, který popisuje kontraktu, ale neposkytuje úplnou implementaci kontraktu. Abstrakce jsou obvykle implementovány jako abstraktní třídy nebo rozhraní a začne s dobře definované sadě referenční dokumentaci k nástroji popisující požadované sémantika typy implementace kontraktu. Mezi nejdůležitější abstrakce v rozhraní .NET Framework patří <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, a <xref:System.Object>.  
  
 Rozhraní můžete rozšířit pomocí implementace konkrétní typ, který podporuje kontrakt abstrakci a pomocí tohoto konkrétního typu framework rozhraní API náročné (pracující na) odběru.  
  
 Smysluplný a užitečné abstrakce, který se bude moct odolat test čas je velmi obtížné návrhu. Potíže hlavní dochází správnou sadu žádné další a ne méně členů. Pokud abstrakci má příliš mnoho členů, bude obtížné nebo dokonce možné implementovat. Pokud má příliš málo členy pro funkci přislíbeném, stane nemá zajímavými způsoby.  
  
 Příliš mnoho abstrakce v rozhraní také negativně ovlivnit použitelnost rozhraní. Často je velmi obtížné porozumět abstrakci bez pochopení, jak zapadá do větší přehled o konkrétní implementace a rozhraní API pracující na odběru. Názvy abstrakce a jejich členové jsou také nutně abstraktní, často vede jako nesrozumitelné a unapproachable první neměňte širší kontextu jejich využití.  
  
 Abstrakce však poskytují velmi výkonné rozšíření, což často nemůže shodovat na rozšiřitelnost mechanismy. Jsou jádrem mnoho architektury vzory, třeba moduly plug-in inverzi řízení (IoC), kanálů a tak dále. Jsou také velmi důležité pro testovatelnosti architektury. Dobrý abstrakce umožňují se zakázaným inzerováním out velkou závislosti pro účely testování jednotek. V souhrnu jsou zodpovědní za sought-after bohatost moderní architektury objektově orientované abstrakce.  
  
 **X nesmí** zadejte abstrakce, pokud jsou neotestovali ve vývoji několik rozhraní API využívání abstrakce a konkrétní implementace.  
  
 **PROVEĎTE ✓** zvolit pečlivě abstraktní třídy a rozhraní při navrhování abstrakci.  
  
 **✓ ZVAŽTE** poskytuje odkaz testy pro konkrétní implementace abstrakce. Tyto testy by měl povolit uživatelům otestovat, zda jejich implementace správně implementaci kontraktu.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
