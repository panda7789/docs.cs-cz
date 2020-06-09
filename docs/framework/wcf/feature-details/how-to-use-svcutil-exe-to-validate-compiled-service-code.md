---
title: 'Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 6f2064c696e3186c3208a7e57dc51655056d23ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595346"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="c4757-102">Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="c4757-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="c4757-103">K detekci chyb v implementacích a konfiguracích služby, aniž by bylo nutné hostovat službu, můžete použít [Nástroj (Svcutil. exe) nástroje ServiceModel Metadata](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="c4757-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="c4757-104">Ověření služby</span><span class="sxs-lookup"><span data-stu-id="c4757-104">To validate a service</span></span>  
  
1. <span data-ttu-id="c4757-105">Zkompilujte službu do spustitelného souboru a jednoho nebo více závislých sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4757-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="c4757-106">Otevření příkazového řádku sady SDK</span><span class="sxs-lookup"><span data-stu-id="c4757-106">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="c4757-107">Na příkazovém řádku spusťte nástroj Svcutil. exe v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="c4757-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="c4757-108">Další informace o různých parametrech najdete v tématu Service Validationsection [(Svcutil. exe) pro nástroj](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="c4757-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="c4757-109">`/serviceName`K určení názvu konfigurace služby, kterou chcete ověřit, je nutné použít možnost.</span><span class="sxs-lookup"><span data-stu-id="c4757-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="c4757-110">`assemblyPath`Argument určuje cestu ke spustitelnému souboru pro službu a jedno nebo více sestavení, která obsahují typy služby, které mají být ověřeny.</span><span class="sxs-lookup"><span data-stu-id="c4757-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="c4757-111">Spustitelné sestavení musí mít přidružený konfigurační soubor k poskytnutí konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="c4757-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="c4757-112">K poskytnutí více sestavení můžete použít standardní zástupné znaky příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c4757-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4757-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4757-113">Example</span></span>  
 <span data-ttu-id="c4757-114">Následující příkaz služba myServiceName implementovala ve spustitelném souboru myServiceHost. exe.</span><span class="sxs-lookup"><span data-stu-id="c4757-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="c4757-115">Konfigurační soubor služby (myServiceHost. exe. config) je automaticky načten.</span><span class="sxs-lookup"><span data-stu-id="c4757-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4757-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4757-116">See also</span></span>

- [<span data-ttu-id="c4757-117">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c4757-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
