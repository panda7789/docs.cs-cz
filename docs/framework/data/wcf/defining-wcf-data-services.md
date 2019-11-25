---
title: Definování datových služeb WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 26cfee95f7cd3b956ff263d90b713e9d70b98202
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975336"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="b85b4-102">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b85b4-102">Defining WCF Data Services</span></span>

<span data-ttu-id="b85b4-103">Tato část popisuje, jak vytvořit a nakonfigurovat WCF Data Services k vystavení dat jako informačního kanálu OData (Open Data Protocol).</span><span class="sxs-lookup"><span data-stu-id="b85b4-103">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="b85b4-104">Další informace o základních krocích požadovaných k vytvoření datové služby najdete v tématu vystavení [dat jako služby](exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b85b4-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b85b4-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b85b4-105">In This Section</span></span>

 [<span data-ttu-id="b85b4-106">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="b85b4-106">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="b85b4-107">Popisuje možnosti konfigurace datové služby, které poskytuje WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="b85b4-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="b85b4-108">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="b85b4-108">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="b85b4-109">Popisuje modely poskytovatele pro vystavení dat jako datovou službu.</span><span class="sxs-lookup"><span data-stu-id="b85b4-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="b85b4-110">Operace služby</span><span class="sxs-lookup"><span data-stu-id="b85b4-110">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="b85b4-111">Popisuje, jak definovat operace služby, které zveřejňují metody na serveru.</span><span class="sxs-lookup"><span data-stu-id="b85b4-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="b85b4-112">Přizpůsobení informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="b85b4-112">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="b85b4-113">Popisuje, jak vytvořit mapování mezi entitami v datovém modelu definovaném poskytovatelem datové služby a prvky v datovém kanálu.</span><span class="sxs-lookup"><span data-stu-id="b85b4-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="b85b4-114">Zachycovače</span><span class="sxs-lookup"><span data-stu-id="b85b4-114">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="b85b4-115">Popisuje, jak definovat metody pro zachycování, které provádějí vlastní obchodní logiku pro požadavky na datovou službu.</span><span class="sxs-lookup"><span data-stu-id="b85b4-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="b85b4-116">Vývoj a nasazení služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b85b4-116">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="b85b4-117">Popisuje, jak vyvíjet a nasazovat datovou službu pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b85b4-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="b85b4-118">Zabezpečení datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b85b4-118">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="b85b4-119">Popisuje ověřování a autorizaci pro datovou službu a další otázky týkající se zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b85b4-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="b85b4-120">Hostování datové služby</span><span class="sxs-lookup"><span data-stu-id="b85b4-120">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="b85b4-121">Popisuje, jak vybrat hostitele pro datovou službu.</span><span class="sxs-lookup"><span data-stu-id="b85b4-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="b85b4-122">Správa verzí datové služby</span><span class="sxs-lookup"><span data-stu-id="b85b4-122">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="b85b4-123">Popisuje, jak pracovat s různými verzemi OData.</span><span class="sxs-lookup"><span data-stu-id="b85b4-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="b85b4-124">Podrobnosti implementace protokolu služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b85b4-124">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="b85b4-125">Popisuje volitelné funkce protokolu OData, které nejsou aktuálně implementovány nástrojem WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="b85b4-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="b85b4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b85b4-126">See also</span></span>

- [<span data-ttu-id="b85b4-127">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b85b4-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="b85b4-128">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="b85b4-128">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="b85b4-129">Začínáme</span><span class="sxs-lookup"><span data-stu-id="b85b4-129">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
