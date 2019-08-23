---
title: Generování klientské knihovny datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 14ea550715c1b224945137f123eed3b53e56cead
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918640"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="b2828-102">Generování klientské knihovny datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="b2828-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="b2828-103">Datová služba, která implementuje rozhraní [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] , může vracet dokument metadat služby, který popisuje datový model vystavený [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačním kanálem.</span><span class="sxs-lookup"><span data-stu-id="b2828-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="b2828-104">Další informace najdete v tématu [OData: Dokument](https://go.microsoft.com/fwlink/?LinkId=186070)metadat služby</span><span class="sxs-lookup"><span data-stu-id="b2828-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="b2828-105">Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]službu založenou na službě.</span><span class="sxs-lookup"><span data-stu-id="b2828-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="b2828-106">Při použití tohoto nástroje k přidání odkazu na metadata vrácená [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačním kanálem v klientském projektu provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="b2828-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="b2828-107">Požádá o dokument metadat služby z datové služby a interpretuje vrácená metadata.</span><span class="sxs-lookup"><span data-stu-id="b2828-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b2828-108">Vrácená metadata jsou uložena v projektu klienta jako soubor. edmx.</span><span class="sxs-lookup"><span data-stu-id="b2828-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="b2828-109">Tento soubor. edmx nejde otevřít pomocí návrháře model EDM (Entity Data Model), protože nemá stejný formát jako soubor. edmx, který používá Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b2828-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="b2828-110">Tento soubor metadat můžete zobrazit pomocí editoru XML nebo libovolného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="b2828-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="b2828-111">Další informace najdete v tématu [ \[MC-EDMX\]: Specifikace formátu](https://go.microsoft.com/fwlink/?LinkID=178833) balíčku pro Data Services model EDM (Entity Data Model)</span><span class="sxs-lookup"><span data-stu-id="b2828-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="b2828-112">Generuje reprezentace služby jako třídu kontejneru entity, ze <xref:System.Data.Services.Client.DataServiceContext>které dědí.</span><span class="sxs-lookup"><span data-stu-id="b2828-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="b2828-113">Tato generovaná třída kontejneru entity se podobá kontejneru entit, který generují nástroje model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="b2828-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="b2828-114">Další informace najdete v tématu [Přehled služby Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b2828-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="b2828-115">Generuje datové třídy pro typy datových modelů, které zjišťuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="b2828-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="b2828-116">Přidá do projektu odkaz na `System.Data.Services.Client` sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2828-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="b2828-117">Další informace najdete v tématu [jak: Přidejte odkaz](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)na datovou službu.</span><span class="sxs-lookup"><span data-stu-id="b2828-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="b2828-118">Třídy klientské datové služby je také možné vygenerovat pomocí nástroje [DataSvcUtil. exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b2828-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="b2828-119">Další informace najdete v tématu [jak: Ručně vygenerujte třídy](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)datové služby klienta.</span><span class="sxs-lookup"><span data-stu-id="b2828-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="b2828-120">Mapování datových typů klienta</span><span class="sxs-lookup"><span data-stu-id="b2828-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="b2828-121">Při použití dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio nebo `DataSvcUtil.exe` v nástroji ke generování datových tříd klienta, které [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jsou založeny na informačním kanálu, jsou .NET Framework datové typy mapovány na primitivní typy z datového modelu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b2828-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="b2828-122">Typ datového modelu</span><span class="sxs-lookup"><span data-stu-id="b2828-122">Data model type</span></span>|<span data-ttu-id="b2828-123">.NET Framework datový typ</span><span class="sxs-lookup"><span data-stu-id="b2828-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="b2828-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="b2828-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="b2828-125">Další informace najdete v tématu [OData: Primitivní datové typy](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="b2828-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2828-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2828-126">See also</span></span>

- [<span data-ttu-id="b2828-127">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b2828-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="b2828-128">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="b2828-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
