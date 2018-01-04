---
title: "Člen pokynů pro návrh"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae69b77098c7f2e1de83eedd40cf0f0da9473326
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="member-design-guidelines"></a>Člen pokynů pro návrh
Metody, vlastnosti, události, konstruktory a pole se souhrnně označují jako členy. Členy jsou nakonec prostředky, se kterým je funkce framework zpřístupněny koncovým uživatelům prostředí.  
  
 Členové můžou být statické virtuální nebo nevirtuální, konkrétní nebo abstraktní, nebo instance a může mít několik různými obory usnadnění. Všechna tato různých poskytuje neuvěřitelné expressiveness, ale současně vyžaduje pozornost ze strany návrháře framework.  
  
 Tato kapitola nabízí základní pokyny, které by se měly dodržovat při navrhování členy libovolného typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přetížení člena](../../../docs/standard/design-guidelines/member-overloading.md)  
 [Návrh vlastnosti](../../../docs/standard/design-guidelines/property.md)  
 [Návrh konstruktoru](../../../docs/standard/design-guidelines/constructor.md)  
 [Návrh události](../../../docs/standard/design-guidelines/event.md)  
 [Návrh pole](../../../docs/standard/design-guidelines/field.md)  
 [Metody rozšíření](../../../docs/standard/design-guidelines/extension-methods.md)  
 [Přetížení operátoru](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [Návrh parametru](../../../docs/standard/design-guidelines/parameter-design.md)  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
