---
title: 215 – MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964190"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="393bc-102">215 – MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="393bc-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="393bc-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="393bc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="393bc-104">id</span><span class="sxs-lookup"><span data-stu-id="393bc-104">ID</span></span>|<span data-ttu-id="393bc-105">215</span><span class="sxs-lookup"><span data-stu-id="393bc-105">215</span></span>|  
|<span data-ttu-id="393bc-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="393bc-106">Keywords</span></span>|<span data-ttu-id="393bc-107">Řešení potíží, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="393bc-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="393bc-108">Level</span><span class="sxs-lookup"><span data-stu-id="393bc-108">Level</span></span>|<span data-ttu-id="393bc-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="393bc-109">Information</span></span>|  
|<span data-ttu-id="393bc-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="393bc-110">Channel</span></span>|<span data-ttu-id="393bc-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="393bc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="393bc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="393bc-112">Description</span></span>  
 <span data-ttu-id="393bc-113">K této události dojde, když přenos založený na protokolu TCP obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="393bc-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="393bc-114">Všimněte si, že na úrovni přenosu je možné vyměňovat více zpráv mezi klienty a službami pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="393bc-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="393bc-115">To může být způsobeno chováním infrastruktury, takže zabezpečení je dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="393bc-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="393bc-116">Počet `MessageReceivedByTransport` událostí, které jsou vygenerovány, se tedy liší v závislosti na vazbě služby a její konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="393bc-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="393bc-117">Tato událost se nevysílá pro jednosměrná přenos.</span><span class="sxs-lookup"><span data-stu-id="393bc-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="393bc-118">Message</span><span class="sxs-lookup"><span data-stu-id="393bc-118">Message</span></span>  
 <span data-ttu-id="393bc-119">Přenos přijal zprávu od '% 1 '.</span><span class="sxs-lookup"><span data-stu-id="393bc-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="393bc-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="393bc-120">Details</span></span>  
  
|<span data-ttu-id="393bc-121">Název datové položky</span><span class="sxs-lookup"><span data-stu-id="393bc-121">Data Item Name</span></span>|<span data-ttu-id="393bc-122">Typ datové položky</span><span class="sxs-lookup"><span data-stu-id="393bc-122">Data Item Type</span></span>|<span data-ttu-id="393bc-123">Popis</span><span class="sxs-lookup"><span data-stu-id="393bc-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="393bc-124">Adresa naslouchání</span><span class="sxs-lookup"><span data-stu-id="393bc-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="393bc-125">Adresa, která přijala zprávu.</span><span class="sxs-lookup"><span data-stu-id="393bc-125">The address that received the message.</span></span>|  
|<span data-ttu-id="393bc-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="393bc-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="393bc-127">V případě služeb hostovaných na webu toto pole jedinečně identifikuje službu ve webové hierarchii.</span><span class="sxs-lookup"><span data-stu-id="393bc-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="393bc-128">Jeho formát je definován jako název webové stránky služba virtuální cesta&#124;&#124;ServiceName.</span><span class="sxs-lookup"><span data-stu-id="393bc-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="393bc-129">Příklad: ' Výchozí web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.</span><span class="sxs-lookup"><span data-stu-id="393bc-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="393bc-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="393bc-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="393bc-131">Řetězec vrácený třídou AppDomain. CurrentDomain. FriendlyName</span><span class="sxs-lookup"><span data-stu-id="393bc-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
