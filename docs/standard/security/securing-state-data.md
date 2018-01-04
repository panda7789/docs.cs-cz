---
title: "Zabezpečení stavových dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d5f8c4d17e17f7bcdf58db7052dbb2cf2b737a9c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="securing-state-data"></a>Zabezpečení stavových dat
Aplikace, které zpracovávají důvěrná data nebo se přesvědčte, jakýkoli druh rozhodnutí týkající se zabezpečení je třeba ponechat data v rámci své vlastní ovládací prvek a nelze povolit další potenciálně škodlivého kódu, chcete-li získat přístup k datům. Nejlepší způsob, jak chránit data v paměti je deklarovat data jako soukromý nebo interní (s rozsahem omezené na stejném sestavení) proměnné. Ale i tato data jsou přístupná, byste měli vědět:  
  
-   Pomocí reflexe mechanismy, vysoce důvěryhodný kód, který může odkazovat objektu získat a nastavte soukromé členy.  
  
-   Pomocí serializace, vysoce důvěryhodný kód můžete efektivně získat a nastavit soukromé členy, pokud má přístup k odpovídající data ve formuláři serializovaného objektu.  
  
-   V části ladění, můžete tato data přečíst.  
  
 Zajistěte, aby že žádné metody nebo vlastnosti neúmyslně zpřístupňuje tyto hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
