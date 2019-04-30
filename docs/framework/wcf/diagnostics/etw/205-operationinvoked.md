---
title: 205 – OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781976"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="fd3d0-102">205 – OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="fd3d0-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="fd3d0-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fd3d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd3d0-104">ID</span><span class="sxs-lookup"><span data-stu-id="fd3d0-104">ID</span></span>|<span data-ttu-id="fd3d0-105">205</span><span class="sxs-lookup"><span data-stu-id="fd3d0-105">205</span></span>|  
|<span data-ttu-id="fd3d0-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fd3d0-106">Keywords</span></span>|<span data-ttu-id="fd3d0-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fd3d0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fd3d0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="fd3d0-108">Level</span></span>|<span data-ttu-id="fd3d0-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="fd3d0-109">Information</span></span>|  
|<span data-ttu-id="fd3d0-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="fd3d0-110">Channel</span></span>|<span data-ttu-id="fd3d0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fd3d0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd3d0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fd3d0-112">Description</span></span>  
 <span data-ttu-id="fd3d0-113">Tato událost je vygenerován těsně před výchozím modelu služby `OperationInvoker` zahájí volání metody.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd3d0-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="fd3d0-114">Message</span></span>  
 <span data-ttu-id="fd3d0-115">Třída OperationInvoker vyvolala metodu '%1'.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="fd3d0-116">Informace o volajícím: '%2'.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd3d0-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fd3d0-117">Details</span></span>  
  
|<span data-ttu-id="fd3d0-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="fd3d0-118">Data Item Name</span></span>|<span data-ttu-id="fd3d0-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="fd3d0-119">Data Item Type</span></span>|<span data-ttu-id="fd3d0-120">Popis</span><span class="sxs-lookup"><span data-stu-id="fd3d0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd3d0-121">Název metody</span><span class="sxs-lookup"><span data-stu-id="fd3d0-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="fd3d0-122">Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="fd3d0-123">Informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="fd3d0-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="fd3d0-124">IP adresu a číslo portu klienta ve formátu "IPAddress:PortNumber".</span><span class="sxs-lookup"><span data-stu-id="fd3d0-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="fd3d0-125">Tyto dvě hodnoty jsou načten z vlastnosti zprávy "System.ServiceModel.Channels.RemoteEndpointMessageProperty" v rámci operace.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="fd3d0-126">Všimněte si, že u vazeb mimo TCP tuto hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="fd3d0-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="fd3d0-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="fd3d0-128">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fd3d0-129">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="fd3d0-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fd3d0-130">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="fd3d0-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fd3d0-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3d0-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fd3d0-132">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fd3d0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
