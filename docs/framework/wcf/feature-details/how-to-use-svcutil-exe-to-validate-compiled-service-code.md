---
title: "Postupy: použití Svcutil.exe pro ověření kompilovaného kódu služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ea14631208f755b45a27ff323b7d875c1ae5cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="6ca4e-102">Postupy: použití Svcutil.exe pro ověření kompilovaného kódu služby</span><span class="sxs-lookup"><span data-stu-id="6ca4e-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="6ca4e-103">Můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke zjištění chyby v implementace služby a konfigurace bez hostující službu.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="6ca4e-104">K ověření služby</span><span class="sxs-lookup"><span data-stu-id="6ca4e-104">To validate a service</span></span>  
  
1.  <span data-ttu-id="6ca4e-105">Zkompilujte služby do spustitelného souboru a jeden nebo více závislých sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2.  <span data-ttu-id="6ca4e-106">Otevřete příkazový řádek SDK</span><span class="sxs-lookup"><span data-stu-id="6ca4e-106">Open an SDK command prompt</span></span>  
  
3.  <span data-ttu-id="6ca4e-107">Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="6ca4e-108">Další informace o různých parametrů, najdete v části služby Validationsection z [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="6ca4e-109">Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="6ca4e-110">`assemblyPath` Argument určuje cestu ke spustitelnému souboru pro službu a jeden nebo více sestavení, které obsahují typy služby, které mají být ověřen.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="6ca4e-111">Spustitelný soubor sestavení musí být přidružen konfigurační soubor a zadejte konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="6ca4e-112">Standardní zástupné znaky příkazového řádku můžete uvést více sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ca4e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ca4e-113">Example</span></span>  
 <span data-ttu-id="6ca4e-114">Následující příkaz myServiceName služby je implementovaná v myServiceHost.exe spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="6ca4e-115">Konfigurační soubor služby (myServiceHost.exe.config) je automaticky načíst.</span><span class="sxs-lookup"><span data-stu-id="6ca4e-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ca4e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ca4e-116">See Also</span></span>  
 [<span data-ttu-id="6ca4e-117">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="6ca4e-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
