---
title: Generování klientské knihovny datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 96b7bfabef589464e99e808d19f0dee6cfb23536
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765658"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="fc56a-102">Generování klientské knihovny datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="fc56a-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="fc56a-103">Datové služby, který implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] může vrátit metadata dokumentu služby, které popisují datový model vystavené [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="fc56a-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="fc56a-104">Další informace najdete v tématu [OData: Dokument metadat služby](https://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="fc56a-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="fc56a-105">Můžete použít **přidat odkaz na službu** dialogového okna v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby.</span><span class="sxs-lookup"><span data-stu-id="fc56a-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="fc56a-106">Při použití tohoto nástroje se přidat odkaz na metadata vrácený [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu klientský projekt, provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="fc56a-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="fc56a-107">Požadavky služby dokument metadat z datové služby a interpretuje vrácených metadat.</span><span class="sxs-lookup"><span data-stu-id="fc56a-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc56a-108">Vrácené metadata jsou uložena v klientském projektu jako soubor .edmx.</span><span class="sxs-lookup"><span data-stu-id="fc56a-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="fc56a-109">Nelze otevřít tento soubor .edmx s použitím modelu Entity Data Model designer, protože nemá stejný formát souboru .edmx používá Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fc56a-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="fc56a-110">Zobrazí se tento soubor metadat pomocí editoru XML nebo libovolného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="fc56a-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="fc56a-111">Další informace najdete v tématu [ \[MC EDMX\]: Model Entity Data Model pro formát dat služby balení](https://go.microsoft.com/fwlink/?LinkID=178833) specifikace</span><span class="sxs-lookup"><span data-stu-id="fc56a-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="fc56a-112">Generuje reprezentaci služby jako třídu kontejneru entity, která dědí z <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="fc56a-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="fc56a-113">Tato třída kontejneru generované entity se podobá kontejneru entity, které generují nástroje modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="fc56a-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="fc56a-114">Další informace najdete v tématu [Přehled služby objektů (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fc56a-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="fc56a-115">Vygeneruje třídy dat pro datové typy modelů, které zjistí v metadata služby.</span><span class="sxs-lookup"><span data-stu-id="fc56a-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="fc56a-116">Přidá odkaz na `System.Data.Services.Client` sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="fc56a-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="fc56a-117">Další informace najdete v tématu [jak: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc56a-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="fc56a-118">Tříd klientské datové služby může být také generovány pomocí [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fc56a-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="fc56a-119">Další informace najdete v tématu [jak: Ruční generování tříd klientské datové služby](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc56a-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="fc56a-120">Mapování datového typu klienta</span><span class="sxs-lookup"><span data-stu-id="fc56a-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="fc56a-121">Při použití **přidat odkaz na službu** dialogového okna v sadě Visual Studio nebo `DataSvcUtil.exe` nástroj pro generování klienta datových tříd, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, datové typy rozhraní .NET Framework, které jsou mapovány na primitivní typy z datový model následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fc56a-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="fc56a-122">Typ datového modelu</span><span class="sxs-lookup"><span data-stu-id="fc56a-122">Data model type</span></span>|<span data-ttu-id="fc56a-123">Datový typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="fc56a-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="fc56a-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="fc56a-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="fc56a-125">Další informace najdete v tématu [OData: Primitivní datové typy](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="fc56a-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc56a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc56a-126">See also</span></span>

- [<span data-ttu-id="fc56a-127">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="fc56a-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="fc56a-128">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="fc56a-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
