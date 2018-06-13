---
title: 302 – UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: c70857951309ef54ba460e96e948c9320269d30f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461897"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="862da-102">302 – UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="862da-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="862da-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="862da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="862da-104">ID</span><span class="sxs-lookup"><span data-stu-id="862da-104">ID</span></span>|<span data-ttu-id="862da-105">302</span><span class="sxs-lookup"><span data-stu-id="862da-105">302</span></span>|  
|<span data-ttu-id="862da-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="862da-106">Keywords</span></span>|<span data-ttu-id="862da-107">Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="862da-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="862da-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="862da-108">Level</span></span>|<span data-ttu-id="862da-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="862da-109">Warning</span></span>|  
|<span data-ttu-id="862da-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="862da-110">Channel</span></span>|<span data-ttu-id="862da-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="862da-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="862da-112">Popis</span><span class="sxs-lookup"><span data-stu-id="862da-112">Description</span></span>  
 <span data-ttu-id="862da-113">Tato událost je vygenerované z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="862da-113">This event is emitted from user code.</span></span> <span data-ttu-id="862da-114">Vývojáři mohou emitování Tato událost při výskytu události definované vlastní upozornění ve své služby.</span><span class="sxs-lookup"><span data-stu-id="862da-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="862da-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="862da-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="862da-116">Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.</span><span class="sxs-lookup"><span data-stu-id="862da-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="862da-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="862da-117">Message</span></span>  
 <span data-ttu-id="862da-118">Název: %1, Reference: %2, datové části: % 3</span><span class="sxs-lookup"><span data-stu-id="862da-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="862da-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="862da-119">Details</span></span>  
  
|<span data-ttu-id="862da-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="862da-120">Data Item Name</span></span>|<span data-ttu-id="862da-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="862da-121">Data Item Type</span></span>|<span data-ttu-id="862da-122">Popis</span><span class="sxs-lookup"><span data-stu-id="862da-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="862da-123">Název</span><span class="sxs-lookup"><span data-stu-id="862da-123">Name</span></span>|`xs:string`|<span data-ttu-id="862da-124">Název uživatelem definované události.</span><span class="sxs-lookup"><span data-stu-id="862da-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="862da-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="862da-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="862da-126">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="862da-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="862da-127">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="862da-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="862da-128">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="862da-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="862da-129">datová část</span><span class="sxs-lookup"><span data-stu-id="862da-129">Payload</span></span>|`xs:string`|<span data-ttu-id="862da-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="862da-130">The user-defined payload of the event.</span></span>|
