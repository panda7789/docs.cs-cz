---
title: "Generování dat služby klientské knihovny (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6adbaafe170cf3f5398677d5df3b3d2ff0a95abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="fa51f-102">Generování dat služby klientské knihovny (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="fa51f-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="fa51f-103">Služba data, která implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] může vrátit dokument metadat služby, který popisuje datový model vystavené [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="fa51f-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="fa51f-104">Další informace najdete v tématu [OData: dokument metadat služby](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="fa51f-104">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="fa51f-105">Můžete použít **přidat odkaz na službu** dialogové okno v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby.</span><span class="sxs-lookup"><span data-stu-id="fa51f-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="fa51f-106">Při použití tohoto nástroje se přidat odkaz na metadata vrácený [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v projektu klienta, provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="fa51f-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="fa51f-107">Požadavky služby dokument metadat ze služby data a interpretuje Vrácená metadata.</span><span class="sxs-lookup"><span data-stu-id="fa51f-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fa51f-108">Vrácená metadata se ukládají do projektu klienta do souboru .edmx.</span><span class="sxs-lookup"><span data-stu-id="fa51f-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="fa51f-109">Tento soubor EDMX nelze otevřít pomocí návrháře datového modelu Entity, protože nemá stejný formátu souboru .edmx používá rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fa51f-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="fa51f-110">Tento soubor metadat můžete zobrazit pomocí editoru XML nebo libovolného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="fa51f-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="fa51f-111">Další informace najdete v tématu [ \[MC EDMX\]: datového modelu Entity pro formát dat služby balení](http://go.microsoft.com/fwlink/?LinkID=178833) specifikace</span><span class="sxs-lookup"><span data-stu-id="fa51f-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="fa51f-112">Generuje reprezentaci služby jako třída kontejneru entit, která dědí z <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="fa51f-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="fa51f-113">Tato třída kontejneru generovaného entity se podobá kontejneru entit, který generovat nástroje modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="fa51f-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="fa51f-114">Další informace najdete v tématu [přehled služeb objektů (rozhraní Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="fa51f-114">For more information, see [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="fa51f-115">V metadatech service generuje datové třídy pro datové typy modelu, které zjistí.</span><span class="sxs-lookup"><span data-stu-id="fa51f-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="fa51f-116">Přidá odkaz na `System.Data.Services.Client` sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="fa51f-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="fa51f-117">Další informace najdete v tématu [postupy: Přidání odkazu na službu Data](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fa51f-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="fa51f-118">Třídy klienta dat služby také může být generována pomocí [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fa51f-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="fa51f-119">Další informace najdete v tématu [postupy: ruční generování dat služby třídy klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fa51f-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="fa51f-120">Mapování datového typu klienta</span><span class="sxs-lookup"><span data-stu-id="fa51f-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="fa51f-121">Při použití **přidat odkaz na službu** dialogové okno v sadě Visual Studio nebo `DataSvcUtil.exe` nástroj pro generování klienta datových tříd, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, rozhraní .NET Framework datové typy jsou namapované na primitivní typy z datový model následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fa51f-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="fa51f-122">Typ modelu dat</span><span class="sxs-lookup"><span data-stu-id="fa51f-122">Data model type</span></span>|<span data-ttu-id="fa51f-123">Datový typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="fa51f-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="fa51f-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="fa51f-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="fa51f-125">Další informace najdete v tématu [OData: primitivní datové typy](http://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="fa51f-125">For more information, see [OData: Primitive Data Types](http://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa51f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa51f-126">See Also</span></span>  
 [<span data-ttu-id="fa51f-127">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="fa51f-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="fa51f-128">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="fa51f-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
