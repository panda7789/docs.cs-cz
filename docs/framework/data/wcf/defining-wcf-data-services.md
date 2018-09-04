---
title: Definování datových služeb WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: c0c9010a71877d2c9757a2c9cf2d5c1fec8aedf7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515534"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="56817-102">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="56817-102">Defining WCF Data Services</span></span>

<span data-ttu-id="56817-103">Tato část popisuje postup vytvoření a konfigurace služeb WCF Data Services k vystavení dat jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="56817-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="56817-104">Další informace o základní kroky potřebné k vytvoření datové služby, najdete v části [vystavení dat jako službu](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="56817-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="56817-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="56817-105">In This Section</span></span>

 [<span data-ttu-id="56817-106">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="56817-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="56817-107">Popisuje možnosti konfigurace služby data poskytované službou WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="56817-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="56817-108">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="56817-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

 <span data-ttu-id="56817-109">Popisuje modely zprostředkovatelů pro vystavení dat jako datové služby.</span><span class="sxs-lookup"><span data-stu-id="56817-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="56817-110">Operace služby</span><span class="sxs-lookup"><span data-stu-id="56817-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

 <span data-ttu-id="56817-111">Popisuje, jak definovat operace služby, které zveřejňovat metody na serveru.</span><span class="sxs-lookup"><span data-stu-id="56817-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="56817-112">Přizpůsobení informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="56817-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)

 <span data-ttu-id="56817-113">Popisuje postup vytvoření mapování mezi entitami v modelu definovaném zprostředkovateli datových služeb a prvky datového kanálu.</span><span class="sxs-lookup"><span data-stu-id="56817-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="56817-114">Zachycovače</span><span class="sxs-lookup"><span data-stu-id="56817-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)

 <span data-ttu-id="56817-115">Popisuje, jak definovat zachycování metody k provedení vlastní obchodní logiky na požadavky na datové služby.</span><span class="sxs-lookup"><span data-stu-id="56817-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="56817-116">Vývoj a nasazení služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="56817-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="56817-117">Popisuje, jak vyvíjet a nasazovat datové služby pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="56817-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="56817-118">Zabezpečení datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="56817-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)

 <span data-ttu-id="56817-119">Popisuje, ověřování a autorizace pro datové služby a další informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="56817-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="56817-120">Hostování datové služby</span><span class="sxs-lookup"><span data-stu-id="56817-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="56817-121">Popisuje, jak vybrat hostitele kvůli datové služby.</span><span class="sxs-lookup"><span data-stu-id="56817-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="56817-122">Správa verzí datové služby</span><span class="sxs-lookup"><span data-stu-id="56817-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="56817-123">Popisuje, jak pracovat s různými verzemi prostředí OData.</span><span class="sxs-lookup"><span data-stu-id="56817-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="56817-124">Podrobnosti implementace protokolu služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="56817-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="56817-125">Popisuje volitelné funkce protokolu OData, které nejsou nyní implementovány služby WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="56817-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="56817-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="56817-126">See Also</span></span>

- [<span data-ttu-id="56817-127">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="56817-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="56817-128">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="56817-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="56817-129">Začínáme</span><span class="sxs-lookup"><span data-stu-id="56817-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
