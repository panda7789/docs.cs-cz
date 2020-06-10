---
title: 'Postupy: Nasazení aplikace integrací COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: b4ae7f730296d54debc1cf2971b61e5700503430
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595424"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Postupy: Nasazení aplikace integrací COM+
Po zapsání aplikace pro integraci COM+ můžete ji chtít nasadit na jiný počítač. Toto téma popisuje, jak přesunout integrační aplikaci modelu COM+ z jednoho počítače do jiného.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Přesun aplikace pro integraci hostované v modelu COM+  
  
1. Ujistěte se, že je na obou počítačích nainstalovaný WCF.  
  
2. Exportujte aplikaci z počítače A.  
  
3. Importujte aplikaci na počítač B.  
  
4. Nastavte kořenový adresář aplikace. Podle konvence je% PROGRAMFILES%/ComPlus aplikací/{AppGUID}.  
  
5. Zkopírujte soubory Application. config a Application. manifest z kořenového adresáře aplikace v počítači A do kořenového adresáře aplikace v počítači B.  
  
6. Upravte adresy koncových bodů služby v souboru Application. config na počítači B a Identifikujte příslušný počítač. Například změňte `http://machineA/MyService` na `http://machineB/MyService` .  
  
### <a name="moving-a-web-hosted-integration-application"></a>Přesun webové aplikace hostované na webu  
  
1. Ujistěte se, že je na obou počítačích nainstalovaný WCF.  
  
2. Exportujte aplikaci z počítače A.  
  
3. Importujte aplikaci na počítač B.  
  
4. Vytvořte složku IIS vroot na počítači B.  
  
5. Zkopírujte soubor. svc (Component. svc) a soubor Web. config z adresáře vroot na počítači A do nově vytvořené složky vroot v počítači B.  
  
## <a name="see-also"></a>Viz také

- [Přehled integrace s aplikacemi modelu COM+](integrating-with-com-plus-applications-overview.md)
- [Postupy: Konfigurace nastavení služby modelu COM+](how-to-configure-com-service-settings.md)
- [Postupy: Použití nástroje pro konfiguraci modelu služby COM+](how-to-use-the-com-service-model-configuration-tool.md)
