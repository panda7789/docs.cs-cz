---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
description: Naučte se, jak pomocí Svcutil.exe stahovat metadata ze spuštěných služeb a ukládat tato metadata do místních souborů.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246763"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="56845-103">Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="56845-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="56845-104">Pomocí Svcutil.exe můžete stahovat metadata ze spuštěných služeb a ukládat je do místních souborů.</span><span class="sxs-lookup"><span data-stu-id="56845-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="56845-105">V případě schémat URL protokolu HTTP a HTTPS se Svcutil.exe pokusí načíst metadata pomocí funkce WS-MetadataExchange a [zjišťování webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="56845-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="56845-106">Pro všechna ostatní schémata URL Svcutil.exe používá pouze WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="56845-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="56845-107">Ve výchozím nastavení Svcutil.exe používá vazby definované ve <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě.</span><span class="sxs-lookup"><span data-stu-id="56845-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="56845-108">Pokud chcete nakonfigurovat vazbu použitou pro WS-MetadataExchange, je nutné v konfiguračním souboru pro Svcutil.exe (svcutil.exe.config) definovat koncový bod klienta, který používá `IMetadataExchange` kontrakt a který má stejný název jako schéma identifikátoru URI (Uniform Resource Identifier) adresy koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="56845-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="56845-109">Při spuštění Svcutil.exe k získání metadat pro službu, která zveřejňuje dvě různé kontrakty služby, které obsahují operaci se stejným názvem, Svcutil.exe se zobrazí chyba s oznámením, že nejde získat metadata z.... Například pokud máte službu, která zveřejňuje kontrakt služby s názvem `ICarService` , který má operaci, `Get(Car c)` a stejná služba zveřejňuje kontrakt služby `IBookService` s názvem, který má operaci `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="56845-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="56845-110">Chcete-li tento problém obejít, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="56845-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="56845-111">Přejmenujte jednu z operací.</span><span class="sxs-lookup"><span data-stu-id="56845-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="56845-112">Nastavte na <xref:System.ServiceModel.OperationContractAttribute.Name%2A> jiný název.</span><span class="sxs-lookup"><span data-stu-id="56845-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="56845-113">Nastavte jeden z oborů názvů operací na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="56845-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="56845-114">Stažení metadat pomocí Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="56845-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="56845-115">Vyhledejte nástroj Svcutil.exe v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="56845-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="56845-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="56845-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="56845-117">Na příkazovém řádku spusťte nástroj v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="56845-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="56845-118">Je nutné zadat `/t:metadata` možnost stahovat metadata.</span><span class="sxs-lookup"><span data-stu-id="56845-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="56845-119">V opačném případě se generuje kód klienta a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="56845-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="56845-120">Argument <`url`>Určuje adresu URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online.</span><span class="sxs-lookup"><span data-stu-id="56845-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="56845-121">Argument <`epr`> Určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="56845-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="56845-122">Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [Nástroj pro nástroj pro metadata ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="56845-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56845-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="56845-123">Example</span></span>  
 <span data-ttu-id="56845-124">Následující příkaz stáhne dokumenty metadat z běžící služby.</span><span class="sxs-lookup"><span data-stu-id="56845-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="56845-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="56845-125">See also</span></span>

- [<span data-ttu-id="56845-126">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="56845-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
