---
title: "Postupy: Nasazení aplikace integrací COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d6d9103c2d36de81392858fedc249be9f7ae94f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a>Postupy: Nasazení aplikace integrací COM+
Jednou byly zapsány aplikace integrací COM +, můžete chtít nasadit virtuální počítač na jiný počítač. Toto téma popisuje postup přesunutí integrace aplikace modelu COM + z jednoho počítače do druhého.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Přesunutí modelu COM + hostované integrace aplikace  
  
1.  Ujistěte se, že [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nainstalován v obou počítačích.  
  
2.  Exportujte aplikace z počítače A.  
  
3.  Importovat aplikace na počítači B.  
  
4.  Nastavte kořenový adresář aplikace. Podle konvence, to je %PROGRAMFILES%/ComPlus aplikace / {AppGUID}.  
  
5.  Zkopírujte soubory Application.config a Application.manifest z kořenového adresáře aplikace na počítače A do kořenového adresáře aplikace v počítači B.  
  
6.  Upravte adresy koncového bodu služby v souboru Application.config na počítači B identifikovat příslušný počítač. Můžete například změňte http://machineA/MyService k http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Přesunutí integrace hostované webové aplikace  
  
1.  Ujistěte se, že [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nainstalován v obou počítačích.  
  
2.  Exportujte aplikace z počítače A.  
  
3.  Importovat aplikace na počítači B.  
  
4.  Vytvořte kořenovou složku IIS v počítači B.  
  
5.  Zkopírujte soubor .svc (componentName.svc) a v souboru Web.config z vroot na počítač A pro nově vytvořený virtuální kořenový adresář na počítači B.  
  
## <a name="see-also"></a>Viz také  
 [Integrace s přehled aplikací modelu COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Postupy: Konfigurace nastavení služby COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Postupy: použití modelu COM + Service Model Configuration Tool](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
