---
title: "Nástroj klienta WCF Data Service (DataSvcUtil.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcbbbe5180acaf943956310d4837a105d8d049d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="a794e-102">Nástroj klienta WCF Data Service (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="a794e-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>
<span data-ttu-id="a794e-103">DataSvcUtil.exe je nástroj příkazového řádku poskytovaný [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , který využívá [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu a vygeneruje třídy klienta dat služby, které jsou potřebné pro přístup ke službě data z klientské aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a794e-103">DataSvcUtil.exe is a command-line tool provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] that consumes an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="a794e-104">Tento nástroj může generovat datové třídy pomocí následujících zdrojů metadat:</span><span class="sxs-lookup"><span data-stu-id="a794e-104">This utility can generate data classes by using the following metadata sources:</span></span>  
  
-   <span data-ttu-id="a794e-105">Kořen identifikátor URI služby data.</span><span class="sxs-lookup"><span data-stu-id="a794e-105">The root URI of a data service.</span></span> <span data-ttu-id="a794e-106">Nástroj požadavků dokumentu metadat služby, která popisuje datový model vystavené službu data.</span><span class="sxs-lookup"><span data-stu-id="a794e-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="a794e-107">Další informace najdete v tématu [OData: dokument metadat služby](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="a794e-107">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span>  
  
-   <span data-ttu-id="a794e-108">Soubor modelu dat (.csdl) definované za použití definice jazyka konceptuálního schématu (CSDL), jak jsou definovány v [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](http://go.microsoft.com/fwlink/?LinkID=159072) specifikace.</span><span class="sxs-lookup"><span data-stu-id="a794e-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](http://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>  
  
-   <span data-ttu-id="a794e-109">Soubor EDMX vytvořili pomocí nástroje datového modelu Entity, které jsou k dispozici rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a794e-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="a794e-110">Další informace najdete v tématu [ \[MC EDMX\]: datového modelu Entity pro formát dat služby balení](http://go.microsoft.com/fwlink/?LinkID=178833) specifikace.</span><span class="sxs-lookup"><span data-stu-id="a794e-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>  
  
 <span data-ttu-id="a794e-111">Další informace najdete v tématu [postupy: ruční generování dat služby třídy klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a794e-111">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a794e-112">Nástroj DataSvcUtil.exe se nainstaluje v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře.</span><span class="sxs-lookup"><span data-stu-id="a794e-112">The DataSvcUtil.exe tool is installed in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory.</span></span> <span data-ttu-id="a794e-113">V mnoha případech je umístěn v C:\Windows\Microsoft.NET\Framework\v4.0.</span><span class="sxs-lookup"><span data-stu-id="a794e-113">In many cases, this is located in C:\Windows\Microsoft.NET\Framework\v4.0,.</span></span> <span data-ttu-id="a794e-114">Pro 64bitové systémy je umístěný v C:\Windows\Microsoft.NET\Framework64\v4.0.</span><span class="sxs-lookup"><span data-stu-id="a794e-114">For 64-bit systems, this is located in C:\Windows\Microsoft.NET\Framework64\v4.0.</span></span> <span data-ttu-id="a794e-115">Můžete také využít nástroj DataSvcUtil.exe z příkazového řádku Visual Studia (klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, přejděte na příkaz **Microsoft Visual Studio 2010**, přejděte na příkaz **nástroje sady Visual Studio**a potom klikněte na **příkazový řádek sady Visual Studio 2010**).</span><span class="sxs-lookup"><span data-stu-id="a794e-115">You can also access the DataSvcUtil.exe tool from the Visual Studio command prompt (Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, and then click **Visual Studio 2010 Command Prompt**).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a794e-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a794e-116">Syntax</span></span>  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a794e-117">Parametry</span><span class="sxs-lookup"><span data-stu-id="a794e-117">Parameters</span></span>  
  
|<span data-ttu-id="a794e-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="a794e-118">Option</span></span>|<span data-ttu-id="a794e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a794e-119">Description</span></span>|  
|------------|-----------------|  
|`/dataservicecollection`|<span data-ttu-id="a794e-120">Určuje, že je kód potřebný k připojení objektů k ovládacím prvkům je vytvořena také.</span><span class="sxs-lookup"><span data-stu-id="a794e-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|  
|`/help`<br /><br /> <span data-ttu-id="a794e-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="a794e-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="a794e-122">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a794e-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a794e-123">`/in:` *\<souboru >*</span><span class="sxs-lookup"><span data-stu-id="a794e-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="a794e-124">Určuje .csdl nebo .edmx soubor nebo adresář, kde je umístěn soubor.</span><span class="sxs-lookup"><span data-stu-id="a794e-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|  
|<span data-ttu-id="a794e-125">`/language:`[VB &#124; CSharp]</span><span class="sxs-lookup"><span data-stu-id="a794e-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="a794e-126">Určuje jazyk pro soubory generované zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="a794e-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="a794e-127">Výchozí hodnoty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a794e-127">The language defaults to C#.</span></span>|  
|`/nologo`|<span data-ttu-id="a794e-128">Potlačí zprávu o autorských právech ze zobrazení.</span><span class="sxs-lookup"><span data-stu-id="a794e-128">Suppresses the copyright message from displaying.</span></span>|  
|<span data-ttu-id="a794e-129">`/out:` *\<souboru >*</span><span class="sxs-lookup"><span data-stu-id="a794e-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="a794e-130">Určuje název souboru zdrojového kódu, který obsahuje třídy generovaného klienta služby data.</span><span class="sxs-lookup"><span data-stu-id="a794e-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|  
|<span data-ttu-id="a794e-131">`/uri:` *\<řetězec >*</span><span class="sxs-lookup"><span data-stu-id="a794e-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="a794e-132">Identifikátor URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="a794e-132">The URI of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span>|  
|<span data-ttu-id="a794e-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="a794e-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="a794e-134">Určuje nejvyšší přijatý verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a794e-134">Specifies the highest accepted version of [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="a794e-135">Verze je určena na základě `DataServiceVersion` atribut elementu DataService v metadatech služby vrácená data.</span><span class="sxs-lookup"><span data-stu-id="a794e-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="a794e-136">Další informace najdete v tématu [verze datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a794e-136">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="a794e-137">Pokud zadáte `/dataservicecollection` parametru, je nutné také zadat `/version:2.0` povolit datové vazby.</span><span class="sxs-lookup"><span data-stu-id="a794e-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a794e-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="a794e-138">See Also</span></span>  
 [<span data-ttu-id="a794e-139">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="a794e-139">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="a794e-140">Postupy: Přidání odkazu na datovou službu</span><span class="sxs-lookup"><span data-stu-id="a794e-140">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
