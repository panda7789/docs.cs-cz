---
title: 301 – UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596476"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="25d90-102">301 – UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="25d90-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="25d90-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25d90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25d90-104">ID</span><span class="sxs-lookup"><span data-stu-id="25d90-104">ID</span></span>|<span data-ttu-id="25d90-105">301</span><span class="sxs-lookup"><span data-stu-id="25d90-105">301</span></span>|  
|<span data-ttu-id="25d90-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="25d90-106">Keywords</span></span>|<span data-ttu-id="25d90-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="25d90-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="25d90-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="25d90-108">Level</span></span>|<span data-ttu-id="25d90-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="25d90-109">Error</span></span>|  
|<span data-ttu-id="25d90-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="25d90-110">Channel</span></span>|<span data-ttu-id="25d90-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="25d90-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25d90-112">Popis</span><span class="sxs-lookup"><span data-stu-id="25d90-112">Description</span></span>  
 <span data-ttu-id="25d90-113">Tato událost je vygenerován z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="25d90-113">This event is emitted from user code.</span></span> <span data-ttu-id="25d90-114">Vývojáři mohou vygenerovat tuto událost, pokud dojde k chybě s uživatelem definované ve své službě.</span><span class="sxs-lookup"><span data-stu-id="25d90-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="25d90-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="25d90-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="25d90-116">Kromě toho je Ukázky WCF, která zabalí toto rozhraní API a ukazuje, jak se správně generovat této události.</span><span class="sxs-lookup"><span data-stu-id="25d90-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25d90-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="25d90-117">Message</span></span>  
 <span data-ttu-id="25d90-118">Název: %1, odkaz: %2, vytížení: %3</span><span class="sxs-lookup"><span data-stu-id="25d90-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="25d90-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="25d90-119">Details</span></span>  
  
|<span data-ttu-id="25d90-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="25d90-120">Data Item Name</span></span>|<span data-ttu-id="25d90-121">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="25d90-121">Data Item Type</span></span>|<span data-ttu-id="25d90-122">Popis</span><span class="sxs-lookup"><span data-stu-id="25d90-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25d90-123">Název</span><span class="sxs-lookup"><span data-stu-id="25d90-123">Name</span></span>|`xs:string`|<span data-ttu-id="25d90-124">Uživatelem definovaný název události.</span><span class="sxs-lookup"><span data-stu-id="25d90-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="25d90-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="25d90-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="25d90-126">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="25d90-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="25d90-127">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="25d90-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="25d90-128">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="25d90-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="25d90-129">datová část</span><span class="sxs-lookup"><span data-stu-id="25d90-129">Payload</span></span>|`xs:string`|<span data-ttu-id="25d90-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="25d90-130">The user-defined payload of the event.</span></span>|
