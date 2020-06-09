---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: c04b63fa4963a5df0f910da8702643a6484a4edd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596926"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="df556-102">Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="df556-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="df556-103">Pomocí Svcutil. exe můžete stahovat metadata ze spuštěných služeb a ukládat je do místních souborů.</span><span class="sxs-lookup"><span data-stu-id="df556-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="df556-104">V případě schémat URL s protokolem HTTP a HTTPS se Svcutil. exe pokusí načíst metadata pomocí [zjišťování webové služby](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))WS-MetadataExchange a XML.</span><span class="sxs-lookup"><span data-stu-id="df556-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="df556-105">Pro všechna ostatní schémata URL používá Svcutil. exe pouze WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="df556-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="df556-106">Ve výchozím nastavení používá Svcutil. exe vazby definované ve <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě.</span><span class="sxs-lookup"><span data-stu-id="df556-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="df556-107">Pokud chcete nakonfigurovat vazbu použitou pro WS-MetadataExchange, musíte v konfiguračním souboru pro Svcutil. exe (Svcutil. exe. config) definovat koncový bod klienta, který používá `IMetadataExchange` kontrakt a který má stejný název jako schéma identifikátoru koncového bodu metadat (URI).</span><span class="sxs-lookup"><span data-stu-id="df556-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="df556-108">Při spuštění Svcutil. exe za účelem získání metadat pro službu, která zveřejňuje dvě různé kontrakty služby, které obsahují operaci se stejným názvem, Svcutil. exe zobrazí chybu s oznámením, že nelze získat metadata z.... Například pokud máte službu, která zveřejňuje kontrakt služby s názvem `ICarService` , který má operaci, `Get(Car c)` a stejná služba zveřejňuje kontrakt služby `IBookService` s názvem, který má operaci `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="df556-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="df556-109">Chcete-li tento problém obejít, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="df556-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="df556-110">Přejmenujte jednu z operací.</span><span class="sxs-lookup"><span data-stu-id="df556-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="df556-111">Nastavte na <xref:System.ServiceModel.OperationContractAttribute.Name%2A> jiný název.</span><span class="sxs-lookup"><span data-stu-id="df556-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="df556-112">Nastavte jeden z oborů názvů operací na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df556-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="df556-113">Stažení metadat pomocí Svcutil. exe</span><span class="sxs-lookup"><span data-stu-id="df556-113">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="df556-114">Vyhledejte nástroj Svcutil. exe v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="df556-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="df556-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="df556-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="df556-116">Na příkazovém řádku spusťte nástroj v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="df556-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="df556-117">Je nutné zadat `/t:metadata` možnost stahovat metadata.</span><span class="sxs-lookup"><span data-stu-id="df556-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="df556-118">V opačném případě se generuje kód klienta a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="df556-118">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="df556-119">Argument <`url`>Určuje adresu URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online.</span><span class="sxs-lookup"><span data-stu-id="df556-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="df556-120">Argument <`epr`> Určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="df556-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="df556-121">Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="df556-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df556-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="df556-122">Example</span></span>  
 <span data-ttu-id="df556-123">Následující příkaz stáhne dokumenty metadat z běžící služby.</span><span class="sxs-lookup"><span data-stu-id="df556-123">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="df556-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="df556-124">See also</span></span>

- [<span data-ttu-id="df556-125">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="df556-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
