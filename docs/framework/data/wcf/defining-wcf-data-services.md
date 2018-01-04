---
title: "Definování datových služeb WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61b04be25f54ef22511f45b5752c3ccfa90d94ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="70047-102">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="70047-102">Defining WCF Data Services</span></span>
<span data-ttu-id="70047-103">Tato část popisuje, jak vytvořit a nakonfigurovat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vystavit data jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="70047-103">This section describes how to create and configure [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="70047-104">základní kroky potřebné pro vytvoření datové služby, najdete v části [vystavení vaše Data jako služba](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="70047-104"> the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70047-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="70047-105">In This Section</span></span>  
 [<span data-ttu-id="70047-106">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="70047-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="70047-107">Popisuje možnosti konfigurace dat služby poskytované [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70047-107">Describes the data service configuration options provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="70047-108">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="70047-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 <span data-ttu-id="70047-109">Popisuje zprostředkovatele modely pro vystavení dat jako datové služby.</span><span class="sxs-lookup"><span data-stu-id="70047-109">Describes the provider models for exposing data as a data service.</span></span>  
  
 [<span data-ttu-id="70047-110">Operace služby</span><span class="sxs-lookup"><span data-stu-id="70047-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)  
 <span data-ttu-id="70047-111">Popisuje, jak definovat operace služby, které zveřejňují metody na serveru.</span><span class="sxs-lookup"><span data-stu-id="70047-111">Describes how to define service operations that expose methods on the server.</span></span>  
  
 [<span data-ttu-id="70047-112">Přizpůsobení informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="70047-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)  
 <span data-ttu-id="70047-113">Popisuje, jak vytvořit mapování mezi entitami v datovém modelu definované poskytovatele dat služeb a elementy v datový kanál.</span><span class="sxs-lookup"><span data-stu-id="70047-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>  
  
 [<span data-ttu-id="70047-114">Zachycovače</span><span class="sxs-lookup"><span data-stu-id="70047-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)  
 <span data-ttu-id="70047-115">Popisuje, jak definovat interceptoru metody k provedení vlastní obchodní logiku v žádosti o službu data.</span><span class="sxs-lookup"><span data-stu-id="70047-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>  
  
 [<span data-ttu-id="70047-116">Vývoj a nasazení služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="70047-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 <span data-ttu-id="70047-117">Popisuje, jak pro vývoj a nasazení služby dat pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70047-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>  
  
 [<span data-ttu-id="70047-118">Zabezpečení datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="70047-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 <span data-ttu-id="70047-119">Popisuje ověřování a autorizace pro službu data a další důležité informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="70047-119">Describes authentication and authorization for the data service and other security considerations.</span></span>  
  
 [<span data-ttu-id="70047-120">Hostování datové služby</span><span class="sxs-lookup"><span data-stu-id="70047-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="70047-121">Popisuje postup výběru hostitel služby data.</span><span class="sxs-lookup"><span data-stu-id="70047-121">Describes how to select a host for your data service.</span></span>  
  
 [<span data-ttu-id="70047-122">Správa verzí datové služby</span><span class="sxs-lookup"><span data-stu-id="70047-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)  
 <span data-ttu-id="70047-123">Popisuje, jak pracovat s různými verzemi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70047-123">Describes how to work with different versions of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span>  
  
 [<span data-ttu-id="70047-124">Podrobnosti implementace protokolu služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="70047-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)  
 <span data-ttu-id="70047-125">Popisuje volitelné funkce [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu, které nejsou aktuálně implementované služby WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="70047-125">Describes optional functionalities of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol that are not currently implemented by WCF Data Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70047-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="70047-126">See Also</span></span>  
 [<span data-ttu-id="70047-127">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="70047-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="70047-128">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="70047-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [<span data-ttu-id="70047-129">Začínáme</span><span class="sxs-lookup"><span data-stu-id="70047-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
