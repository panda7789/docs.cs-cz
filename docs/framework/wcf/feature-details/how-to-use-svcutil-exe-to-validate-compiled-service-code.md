---
title: 'Postupy: použití Svcutil.exe pro ověření kompilovaného kódu služby'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 9e7bdf98f578e9b5f9ef2be9c46ccbe811358467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Postupy: použití Svcutil.exe pro ověření kompilovaného kódu služby
Můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke zjištění chyby v implementace služby a konfigurace bez hostující službu.  
  
### <a name="to-validate-a-service"></a>K ověření služby  
  
1.  Zkompilujte služby do spustitelného souboru a jeden nebo více závislých sestavení.  
  
2.  Otevřete příkazový řádek SDK  
  
3.  Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu. Další informace o různých parametrů, najdete v části služby Validationsection z [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tématu.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete ověřit.  
  
     `assemblyPath` Argument určuje cestu ke spustitelnému souboru pro službu a jeden nebo více sestavení, které obsahují typy služby, které mají být ověřen. Spustitelný soubor sestavení musí být přidružen konfigurační soubor a zadejte konfiguraci služby. Standardní zástupné znaky příkazového řádku můžete uvést více sestavení.  
  
## <a name="example"></a>Příklad  
 Následující příkaz myServiceName služby je implementovaná v myServiceHost.exe spustitelný soubor.  Konfigurační soubor služby (myServiceHost.exe.config) je automaticky načíst.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
