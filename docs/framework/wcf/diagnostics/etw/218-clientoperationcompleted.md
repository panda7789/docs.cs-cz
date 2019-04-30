---
title: 218 – ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781759"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="a9ab2-102">218 – ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="a9ab2-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="a9ab2-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9ab2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9ab2-104">ID</span><span class="sxs-lookup"><span data-stu-id="a9ab2-104">ID</span></span>|<span data-ttu-id="a9ab2-105">218</span><span class="sxs-lookup"><span data-stu-id="a9ab2-105">218</span></span>|  
|<span data-ttu-id="a9ab2-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a9ab2-106">Keywords</span></span>|<span data-ttu-id="a9ab2-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a9ab2-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a9ab2-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a9ab2-108">Level</span></span>|<span data-ttu-id="a9ab2-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a9ab2-109">Information</span></span>|  
|<span data-ttu-id="a9ab2-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a9ab2-110">Channel</span></span>|<span data-ttu-id="a9ab2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a9ab2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9ab2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a9ab2-112">Description</span></span>  
 <span data-ttu-id="a9ab2-113">Tato událost je vygenerován klienti hned po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="a9ab2-114">Jednosměrná operace jde hned po úspěšném odeslání zprávy je.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="a9ab2-115">Pro operace požadavek odpověď jde po přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9ab2-116">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a9ab2-116">Message</span></span>  
 <span data-ttu-id="a9ab2-117">Klient dokončil provádění akce '%1' přidružené ke smlouvě '%2'.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="a9ab2-118">Zpráva byla odeslána na "%3".</span><span class="sxs-lookup"><span data-stu-id="a9ab2-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9ab2-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a9ab2-119">Details</span></span>  
  
|<span data-ttu-id="a9ab2-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a9ab2-120">Data Item Name</span></span>|<span data-ttu-id="a9ab2-121">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="a9ab2-121">Data Item Type</span></span>|<span data-ttu-id="a9ab2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a9ab2-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9ab2-123">Akce</span><span class="sxs-lookup"><span data-stu-id="a9ab2-123">Action</span></span>|<span data-ttu-id="a9ab2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9ab2-124">xs:string</span></span>|<span data-ttu-id="a9ab2-125">Záhlaví SOAP akce odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="a9ab2-126">Název smlouvy</span><span class="sxs-lookup"><span data-stu-id="a9ab2-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="a9ab2-127">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-127">The name of the contract.</span></span> <span data-ttu-id="a9ab2-128">Příklad: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="a9ab2-129">Cíl</span><span class="sxs-lookup"><span data-stu-id="a9ab2-129">Destination</span></span>|`xs:string`|<span data-ttu-id="a9ab2-130">Adresa se zpráva odeslala do koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="a9ab2-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="a9ab2-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="a9ab2-132">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a9ab2-133">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="a9ab2-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a9ab2-134">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="a9ab2-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a9ab2-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a9ab2-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a9ab2-136">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a9ab2-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
