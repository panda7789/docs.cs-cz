---
title: 206 – ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781924"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="83809-102">206 – ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="83809-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="83809-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="83809-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83809-104">ID</span><span class="sxs-lookup"><span data-stu-id="83809-104">ID</span></span>|<span data-ttu-id="83809-105">206</span><span class="sxs-lookup"><span data-stu-id="83809-105">206</span></span>|  
|<span data-ttu-id="83809-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="83809-106">Keywords</span></span>|<span data-ttu-id="83809-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="83809-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="83809-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="83809-108">Level</span></span>|<span data-ttu-id="83809-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="83809-109">Information</span></span>|  
|<span data-ttu-id="83809-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="83809-110">Channel</span></span>|<span data-ttu-id="83809-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="83809-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83809-112">Popis</span><span class="sxs-lookup"><span data-stu-id="83809-112">Description</span></span>  
 <span data-ttu-id="83809-113">Tato událost je vygenerován po `ErrorHandler` zaznamenala příležitosti ke zpracování výjimky, ke které došlo v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="83809-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83809-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="83809-114">Message</span></span>  
 <span data-ttu-id="83809-115">Dispečer vyvolal rutinu ErrorHandler typu '%1' se výjimka typu '%3'.</span><span class="sxs-lookup"><span data-stu-id="83809-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="83809-116">ErrorHandled == '%2'.</span><span class="sxs-lookup"><span data-stu-id="83809-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83809-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="83809-117">Details</span></span>  
  
|<span data-ttu-id="83809-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="83809-118">Data Item Name</span></span>|<span data-ttu-id="83809-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="83809-119">Data Item Type</span></span>|<span data-ttu-id="83809-120">Popis</span><span class="sxs-lookup"><span data-stu-id="83809-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83809-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="83809-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="83809-122">Celý název CLR typu vyvolanou `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="83809-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="83809-123">Zpracování</span><span class="sxs-lookup"><span data-stu-id="83809-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="83809-124">`true` Pokud obslužná rutina chyb zpracovává chyby, v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="83809-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="83809-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="83809-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="83809-126">Celý název CLR výjimky, která se právě zpracovává.</span><span class="sxs-lookup"><span data-stu-id="83809-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="83809-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="83809-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="83809-128">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="83809-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="83809-129">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="83809-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="83809-130">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="83809-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="83809-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83809-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="83809-132">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="83809-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
