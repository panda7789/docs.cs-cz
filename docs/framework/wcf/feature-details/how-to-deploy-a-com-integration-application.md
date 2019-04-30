---
title: 'Postupy: Nasazení aplikace integrací COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778323"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Postupy: Nasazení aplikace integrací COM+
Jakmile jste napsali aplikace COM + integration, můžete chtít nasadit virtuální počítač na jiném počítači. Toto téma popisuje, jak aplikace integrací COM + přesunete z jednoho počítače do jiného.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Přesunutí modelu COM + hostované aplikace integrace  
  
1. Zkontrolujte, zda je na obou počítačích nainstalován WCF.  
  
2. Exportovat aplikaci z počítače A.  
  
3. Import aplikace na počítači B.  
  
4. Nastavte kořenový adresář aplikace. Podle konvence, toto je aplikace %PROGRAMFILES%/ComPlus / {AppGUID}.  
  
5. Zkopírujte soubory Application.config a Application.manifest z kořenového adresáře aplikace na počítači A do kořenového adresáře aplikace na počítači B.  
  
6. Úprava adresy koncových bodů služby v souboru Application.config v počítači B k identifikaci příslušné počítače. Například změnit `http://machineA/MyService` k `http://machineB/MyService`.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Přesunutí integrace hostované webové aplikace  
  
1. Zkontrolujte, zda je na obou počítačích nainstalován WCF.  
  
2. Exportovat aplikaci z počítače A.  
  
3. Import aplikace na počítači B.  
  
4. Vytvořit složku IIS vroot na počítači B.  
  
5. Kopírování souboru .svc (componentName.svc) a v souboru Web.config z virtuální kořenový adresář v počítači A do nově vytvořené virtuální kořenový adresář v počítači služby serveru B.  
  
## <a name="see-also"></a>Viz také:

- [Přehled integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [Postupy: Konfigurace nastavení služby modelu COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [Postupy: Použijte nástroj pro konfiguraci modelu služby COM +](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
