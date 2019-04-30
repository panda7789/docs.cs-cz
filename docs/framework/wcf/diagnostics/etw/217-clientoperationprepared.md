---
title: 217 – ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781758"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="2be8c-102">217 – ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="2be8c-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="2be8c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2be8c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2be8c-104">ID</span><span class="sxs-lookup"><span data-stu-id="2be8c-104">ID</span></span>|<span data-ttu-id="2be8c-105">217</span><span class="sxs-lookup"><span data-stu-id="2be8c-105">217</span></span>|  
|<span data-ttu-id="2be8c-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2be8c-106">Keywords</span></span>|<span data-ttu-id="2be8c-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2be8c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2be8c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2be8c-108">Level</span></span>|<span data-ttu-id="2be8c-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="2be8c-109">Information</span></span>|  
|<span data-ttu-id="2be8c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2be8c-110">Channel</span></span>|<span data-ttu-id="2be8c-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2be8c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2be8c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2be8c-112">Description</span></span>  
 <span data-ttu-id="2be8c-113">Tato událost je vygenerován klienty těsně před plánovaným operace je odeslána do služby.</span><span class="sxs-lookup"><span data-stu-id="2be8c-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2be8c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2be8c-114">Message</span></span>  
 <span data-ttu-id="2be8c-115">Klient provádí akci '%1' přidružené ke smlouvě '%2'.</span><span class="sxs-lookup"><span data-stu-id="2be8c-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="2be8c-116">"% 3" pošle zpráva.</span><span class="sxs-lookup"><span data-stu-id="2be8c-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2be8c-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2be8c-117">Details</span></span>  
  
|<span data-ttu-id="2be8c-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2be8c-118">Data Item Name</span></span>|<span data-ttu-id="2be8c-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="2be8c-119">Data Item Type</span></span>|<span data-ttu-id="2be8c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2be8c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2be8c-121">Akce</span><span class="sxs-lookup"><span data-stu-id="2be8c-121">Action</span></span>|`xs:string`|<span data-ttu-id="2be8c-122">Záhlaví SOAP akce odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="2be8c-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="2be8c-123">Název smlouvy</span><span class="sxs-lookup"><span data-stu-id="2be8c-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="2be8c-124">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2be8c-124">The name of the contract.</span></span> <span data-ttu-id="2be8c-125">Příklad: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="2be8c-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="2be8c-126">Cíl</span><span class="sxs-lookup"><span data-stu-id="2be8c-126">Destination</span></span>|`xs:string`|<span data-ttu-id="2be8c-127">Adresa koncového bodu služby, které je zpráva odeslána.</span><span class="sxs-lookup"><span data-stu-id="2be8c-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="2be8c-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="2be8c-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="2be8c-129">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="2be8c-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2be8c-130">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="2be8c-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2be8c-131">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="2be8c-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2be8c-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2be8c-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2be8c-133">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2be8c-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
