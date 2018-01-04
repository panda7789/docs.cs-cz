---
title: "Názvy sestavení a knihoven DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76584e0d22b6e651dfd851675a72d1f0cb70feb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-assemblies-and-dlls"></a>Názvy sestavení a knihoven DLL
Sestavení je jednotka nasazení a identity pro spravovaný kód programy. I když sestavení může mít rozsah jeden nebo více souborů, obvykle sestavení mapování typu 1: 1 s knihovny DLL. Proto tato část popisuje pouze DLL zásady vytváření názvů, které lze poté mapovat na zásady vytváření názvů sestavení.  
  
 **PROVEĎTE ✓** zvolte názvy pro vaše sestavení knihovny DLL, které naznačují velké množství funkcí, jako je například System.Data.  
  
 Názvy sestavení a knihovny DLL nemají tak, aby odpovídaly názvy oborů názvů, ale je možné logicky podle oboru názvů v názvu sestavení. Dobré pravidlo je název knihovny DLL na základě běžných předpony sestavení obsažený v sestavení. Například sestavení s dva obory názvů, `MyCompany.MyTechnology.FirstFeature` a `MyCompany.MyTechnology.SecondFeature`, může být volána `MyCompany.MyTechnology.dll`.  
  
 **✓ ZVAŽTE** pojmenování knihovny DLL podle vzoru následující:  
  
 `<Company>.<Component>.dll`  
  
 kde `<Component>` obsahuje jeden nebo více klauzulích oddělené tečkou. Příklad:  
  
 `Litware.Controls.dll`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
