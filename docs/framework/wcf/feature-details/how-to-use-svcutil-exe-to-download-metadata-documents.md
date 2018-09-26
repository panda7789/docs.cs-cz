---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 6643f0a5dba98afcef38870cf24d91e7d69a1440
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195417"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="5afb3-102">Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="5afb3-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="5afb3-103">Svcutil.exe můžete použít ke stažení metadat z službami a k uložení metadat do místních souborů.</span><span class="sxs-lookup"><span data-stu-id="5afb3-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="5afb3-104">Pro schémata HTTP a HTTPS URL Svcutil.exe pokusí se načíst metadata pomocí WS-MetadataExchange a [zjišťování webové služby XML](https://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="5afb3-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="5afb3-105">Pro všechny ostatní schémata URL Svcutil.exe používá pouze WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="5afb3-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="5afb3-106">Ve výchozím nastavení používá Svcutil.exe vazeb definovaných v <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy.</span><span class="sxs-lookup"><span data-stu-id="5afb3-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="5afb3-107">Ke konfiguraci vazby používá pro WS-MetadataExchange, je nutné definovat koncový bod klienta v konfiguračním souboru pro Svcutil.exe (svcutil.exe.config), který používá `IMetadataExchange` kontrakt a, který má stejný název jako identifikátor URI (Uniform Resource) schéma adresu koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="5afb3-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5afb3-108">Při spuštění Svcutil.exe k získání metadat pro službu, která poskytuje dva různé služby je smlouvách, že každý obsahuje operace se stejným názvem, Svcutil.exe zobrazí chyba s oznámením, "Nelze získat Metadata z..." Například, pokud máte službu, která zveřejňuje kontrakt služby s názvem `ICarService` , který má operace `Get(Car c)` a ve stejné službě zpřístupňuje kontrakt služby s názvem `IBookService` , který má operace `Get(Book b)`.</span><span class="sxs-lookup"><span data-stu-id="5afb3-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="5afb3-109">Chcete-li tento problém obejít, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="5afb3-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="5afb3-110">Po přejmenování jedné z operací.</span><span class="sxs-lookup"><span data-stu-id="5afb3-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="5afb3-111">Nastavte <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na jiný název.</span><span class="sxs-lookup"><span data-stu-id="5afb3-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="5afb3-112">Jeden z oborů názvů operace nastavenou na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5afb3-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="5afb3-113">Chcete-li stáhnout metadata pomocí Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="5afb3-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="5afb3-114">Vyhledejte nástroje Svcutil.exe v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="5afb3-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="5afb3-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="5afb3-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="5afb3-116">Na příkazovém řádku spusťte nástroj v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="5afb3-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="5afb3-117">Je nutné zadat `/t:metadata` možnost stažení metadat.</span><span class="sxs-lookup"><span data-stu-id="5afb3-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="5afb3-118">V opačném případě se generují kód klienta a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5afb3-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="5afb3-119"><`url`> Argument určuje adresu URL koncového bodu služby, která poskytuje metadata nebo k dokumentu metadat hostované online.</span><span class="sxs-lookup"><span data-stu-id="5afb3-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="5afb3-120"><`epr`> Argument určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="5afb3-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="5afb3-121">Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5afb3-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5afb3-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5afb3-122">Example</span></span>  
 <span data-ttu-id="5afb3-123">Následující příkaz soubory ke stažení dokumentů metadat ze spuštěné služby.</span><span class="sxs-lookup"><span data-stu-id="5afb3-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="5afb3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5afb3-124">See Also</span></span>  
 [<span data-ttu-id="5afb3-125">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="5afb3-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
