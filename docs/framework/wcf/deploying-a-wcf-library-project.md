---
title: "Nasazení projektu knihovny WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbbbff1d88559f8ab35caa48fcb04ff1cd7bf015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-wcf-library-project"></a>Nasazení projektu knihovny WCF
Toto téma popisuje, jak můžete nasadit [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] projektu knihovny služby.  
  
## <a name="deploying-a-wcf-service-library"></a>Nasazení knihovny služby WCF  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby je dynamická knihovna (DLL). Jako takový ho nelze provést na svou vlastní. Musí být nasazeny do hostitelského prostředí. Další informace o tomto procesu najdete v tématu [hostitelský a využívání služby WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby se dá nasadit jako libovolný jiný [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Ale pozor který [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje konfiguraci pro knihovny DLL. <xref:System.Configuration>podporuje jeden soubor konfigurace pro doménu AppDomain. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projektu knihovny služby nebude toto omezení tím, že poskytuje soubor App.config pro knihovnu během vývoje. Soubor App.config se však nerozpoznal po nasazení.  
  
 Je nutné přesunout konfigurace kódu do konfiguračního souboru rozpoznáno hostitelského prostředí. Pro vlastní hostování, měli byste zkopírovat obsah souboru App.config do souboru App.config hostování spustitelného souboru. Pokud použijete k hostování služby IIS, měli byste zkopírovat obsah souboru App.config v souboru Web.config virtuálního adresáře.
