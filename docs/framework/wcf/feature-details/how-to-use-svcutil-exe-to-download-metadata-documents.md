---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 25840247e59b9dd61cadaa2ee94713240d135f88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991605"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="f3d2b-102">Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="f3d2b-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="f3d2b-103">Pomocí Svcutil. exe můžete stahovat metadata ze spuštěných služeb a ukládat je do místních souborů.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="f3d2b-104">V případě schémat URL s protokolem HTTP a HTTPS se Svcutil. exe pokusí načíst metadata pomocí [zjišťování webové služby](https://go.microsoft.com/fwlink/?LinkId=94950)WS-MetadataExchange a XML.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="f3d2b-105">Pro všechna ostatní schémata URL používá Svcutil. exe pouze WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="f3d2b-106">Ve výchozím nastavení používá Svcutil. exe vazby definované ve <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="f3d2b-107">Pokud chcete nakonfigurovat vazbu použitou pro WS-MetadataExchange, musíte v konfiguračním souboru pro Svcutil. exe (Svcutil. exe. config) definovat koncový bod klienta, který používá `IMetadataExchange` kontrakt a který má stejný název jako identifikátor URI (Uniform Resource Identifier). schéma adresy koncového bodu metadat</span><span class="sxs-lookup"><span data-stu-id="f3d2b-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f3d2b-108">Při spuštění Svcutil. exe za účelem získání metadat pro službu, která zveřejňuje dvě různé kontrakty služby, které obsahují operaci se stejným názvem, Svcutil. exe zobrazí chybu s oznámením, že nelze získat metadata z.... Například pokud máte službu, `ICarService` která zveřejňuje kontrakt služby s názvem, který má operaci `Get(Car c)` , a stejná služba zveřejňuje kontrakt služby s názvem `IBookService` , který má operaci `Get(Book b)`.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="f3d2b-109">Chcete-li tento problém obejít, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f3d2b-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="f3d2b-110">Přejmenujte jednu z operací.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="f3d2b-111"><xref:System.ServiceModel.OperationContractAttribute.Name%2A> Nastavte na jiný název.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="f3d2b-112">Nastavte jeden z oborů názvů operací na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="f3d2b-113">Stažení metadat pomocí Svcutil. exe</span><span class="sxs-lookup"><span data-stu-id="f3d2b-113">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="f3d2b-114">Vyhledejte nástroj Svcutil. exe v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="f3d2b-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="f3d2b-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="f3d2b-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="f3d2b-116">Na příkazovém řádku spusťte nástroj v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="f3d2b-117">Je nutné zadat `/t:metadata` možnost stahovat metadata.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="f3d2b-118">V opačném případě se generuje kód klienta a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-118">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="f3d2b-119">Argument <`url`> Určuje adresu URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="f3d2b-120">Argument <`epr`> Určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="f3d2b-121">Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f3d2b-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3d2b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3d2b-122">Example</span></span>  
 <span data-ttu-id="f3d2b-123">Následující příkaz stáhne dokumenty metadat z běžící služby.</span><span class="sxs-lookup"><span data-stu-id="f3d2b-123">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3d2b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3d2b-124">See also</span></span>

- [<span data-ttu-id="f3d2b-125">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f3d2b-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
