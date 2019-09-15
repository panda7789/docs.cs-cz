---
title: 'Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: be8755ab4281b40d23ea4c8674c8c4f33631e7b6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991596"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe
K detekci chyb v implementacích a konfiguracích služby, aniž by bylo nutné hostovat službu, můžete použít [Nástroj (Svcutil. exe) nástroje ServiceModel Metadata](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
### <a name="to-validate-a-service"></a>Ověření služby  
  
1. Zkompilujte službu do spustitelného souboru a jednoho nebo více závislých sestavení.  
  
2. Otevření příkazového řádku sady SDK  
  
3. Na příkazovém řádku spusťte nástroj Svcutil. exe v následujícím formátu. Další informace o různých parametrech najdete v tématu Service Validationsection [(Svcutil. exe) pro nástroj](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     K určení názvu konfigurace `/serviceName` služby, kterou chcete ověřit, je nutné použít možnost.  
  
     `assemblyPath` Argument určuje cestu ke spustitelnému souboru pro službu a jedno nebo více sestavení, která obsahují typy služby, které mají být ověřeny. Spustitelné sestavení musí mít přidružený konfigurační soubor k poskytnutí konfigurace služby. K poskytnutí více sestavení můžete použít standardní zástupné znaky příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příkaz služba myServiceName implementovala ve spustitelném souboru myServiceHost. exe.  Konfigurační soubor služby (myServiceHost. exe. config) je automaticky načten.  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
