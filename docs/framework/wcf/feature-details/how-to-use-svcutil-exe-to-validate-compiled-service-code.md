---
title: 'Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 1e90d71d5831ccf262315ebf9c1deb99b386e224
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196408"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="65cad-102">Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="65cad-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="65cad-103">Můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kvůli zjištění chyb v implementacemi služeb a konfigurace bez, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="65cad-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="65cad-104">K ověření služby</span><span class="sxs-lookup"><span data-stu-id="65cad-104">To validate a service</span></span>  
  
1.  <span data-ttu-id="65cad-105">Zkompilujte služby do spustitelného souboru a jeden nebo více závislých sestavení.</span><span class="sxs-lookup"><span data-stu-id="65cad-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2.  <span data-ttu-id="65cad-106">Otevřete příkazový řádek sady SDK</span><span class="sxs-lookup"><span data-stu-id="65cad-106">Open an SDK command prompt</span></span>  
  
3.  <span data-ttu-id="65cad-107">Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="65cad-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="65cad-108">Další informace o různých parametrů, najdete v článku Služba Validationsection z [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="65cad-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="65cad-109">Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="65cad-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="65cad-110">`assemblyPath` Argument určuje cestu ke spustitelnému souboru pro službu a jedno nebo více sestavení, které obsahují typy, které služba má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="65cad-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="65cad-111">Spustitelný soubor sestavení musí mít přidružený konfiguračního souboru a zadejte konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="65cad-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="65cad-112">Můžete použít standardní zástupné znaky příkazového řádku k poskytování více sestavení.</span><span class="sxs-lookup"><span data-stu-id="65cad-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65cad-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="65cad-113">Example</span></span>  
 <span data-ttu-id="65cad-114">Následující příkaz myServiceName služby implementované ve spustitelném souboru myServiceHost.exe.</span><span class="sxs-lookup"><span data-stu-id="65cad-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="65cad-115">Konfigurační soubor služby (myServiceHost.exe.config) je automaticky načíst.</span><span class="sxs-lookup"><span data-stu-id="65cad-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="65cad-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65cad-116">See also</span></span>

- [<span data-ttu-id="65cad-117">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="65cad-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
