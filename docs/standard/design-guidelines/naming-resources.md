---
title: "Názvy prostředků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0387d820cc660bdf6cbafb9d76bbf0184c111881
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="naming-resources"></a>Názvy prostředků
Protože lokalizovatelný prostředků může být odkazováno prostřednictvím určité objekty, jako kdyby byly vlastnosti, jsou podobné vlastnost pokyny pro pojmenování pokyny pro prostředky.  
  
 **PROVEĎTE ✓** použít PascalCasing v klíčů prostředku.  
  
 **PROVEĎTE ✓** zadat popisný místo krátké identifikátory.  
  
 **X nesmí** používat klíčová slova jazyka hlavní jazyky CLR.  
  
 **PROVEĎTE ✓** použijte pouze alfanumerické znaky a podtržítka v pojmenování prostředky.  
  
 **PROVEĎTE ✓** použít následující konvence pro prostředků zprávy výjimek.  
  
 Identifikátor prostředku musí být název typu výjimka plus krátké identifikátor výjimky:  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
