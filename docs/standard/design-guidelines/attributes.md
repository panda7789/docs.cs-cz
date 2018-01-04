---
title: Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 89e892a379c7540cf67488471ae5281a4c4b86f4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="attributes"></a>Atributy
<xref:System.Attribute?displayProperty=nameWithType>je základní třídu používá k definování vlastní atributy.  
  
 Poznámky přidané k elementům programování například sestavení, typy, členů a parametry jsou atributy. Tyto jsou uložené v metadatech sestavení a je přístupný v době běhu pomocí rozhraní API reflexe. Například rozhraní definuje <xref:System.ObsoleteAttribute>, který je možné použít pro určitý typ nebo člen k označení, že typ nebo člen je zastaralá.  
  
 Atributy mohou mít jednu nebo více vlastností, které zajišťují další data související s atribut. Například `ObsoleteAttribute` může nést další informace o verzi v která získali nepoužívá typ nebo člen a popis nové rozhraní API nahrazení zastaralá rozhraní API.  
  
 Některé vlastnosti atributu je třeba zadat při použití atributu. Tyto jsou označovány jako požadované vlastnosti nebo povinnými argumenty, protože jsou reprezentovány jako konstruktor poziční parametry. Například <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> vlastnost <xref:System.Diagnostics.ConditionalAttribute> je požadovaná vlastnost.  
  
 Vlastnosti, které není potřeba zadat, kdy je použit atribut se nazývají volitelných vlastností (nebo volitelné argumenty). Jsou zobrazeny v nastavit vlastnosti. Kompilátory poskytují speciální syntaxe a nastavte tyto vlastnosti, když se použije atribut. Například <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> vlastnost představuje za volitelným argumentem.  
  
 **PROVEĎTE ✓** název třídy vlastních atributů s příponou "Atribut."  
  
 **PROVEĎTE ✓** použít <xref:System.AttributeUsageAttribute> vlastních atributů.  
  
 **PROVEĎTE ✓** zadejte nastavit vlastnosti pro volitelné argumenty.  
  
 **PROVEĎTE ✓** zadejte vlastnosti jen get pro povinnými argumenty.  
  
 **PROVEĎTE ✓** zadat parametry konstruktor k chybě při inicializaci vlastnosti odpovídající povinnými argumenty. Každý parametr by měl mít stejný název (i když se jiný velká a malá písmena) jako odpovídající vlastnost.  
  
 **X nepoužívejte** poskytuje konstruktor parametry k chybě při inicializaci vlastnosti odpovídající volitelné argumenty.  
  
 Jinými slovy nemají vlastnosti, které lze nastavit pomocí konstruktoru a setter. Toto platí umožňuje velmi explicitní argumenty, které jsou volitelné a které jsou požadovány a tomu není nutné dva způsoby, jak to samé.  
  
 **X nepoužívejte** přetížení konstruktory vlastních atributů.  
  
 Má jenom jeden konstruktor jasně komunikuje uživateli, které argumenty jsou povinné a jsou volitelné.  
  
 **PROVEĎTE ✓** zapečetit vlastní atribut třídy, pokud je to možné. Díky tomu rychlejší hledání pro atribut.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
