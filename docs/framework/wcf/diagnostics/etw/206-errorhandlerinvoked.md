---
title: 206 – ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458816"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="a955d-102">206 – ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="a955d-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a955d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a955d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a955d-104">ID</span><span class="sxs-lookup"><span data-stu-id="a955d-104">ID</span></span>|<span data-ttu-id="a955d-105">206</span><span class="sxs-lookup"><span data-stu-id="a955d-105">206</span></span>|  
|<span data-ttu-id="a955d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a955d-106">Keywords</span></span>|<span data-ttu-id="a955d-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a955d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a955d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a955d-108">Level</span></span>|<span data-ttu-id="a955d-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a955d-109">Information</span></span>|  
|<span data-ttu-id="a955d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a955d-110">Channel</span></span>|<span data-ttu-id="a955d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a955d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a955d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a955d-112">Description</span></span>  
 <span data-ttu-id="a955d-113">Tato událost je vygenerované po `ErrorHandler` zaznamenala příležitost ke zpracování výjimky, k níž došlo v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="a955d-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a955d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a955d-114">Message</span></span>  
 <span data-ttu-id="a955d-115">Dispečer vyvolat ZpracováníChyby typu "%1, s výjimkou typu"%3".</span><span class="sxs-lookup"><span data-stu-id="a955d-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="a955d-116">ErrorHandled == '%2'.</span><span class="sxs-lookup"><span data-stu-id="a955d-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a955d-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a955d-117">Details</span></span>  
  
|<span data-ttu-id="a955d-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a955d-118">Data Item Name</span></span>|<span data-ttu-id="a955d-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a955d-119">Data Item Type</span></span>|<span data-ttu-id="a955d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a955d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a955d-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="a955d-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="a955d-122">Položka FullName CLR typu vyvolanou `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="a955d-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="a955d-123">Zpracovává</span><span class="sxs-lookup"><span data-stu-id="a955d-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="a955d-124">`true` Pokud obslužná rutina chyb zpracovávat chyby, jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="a955d-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="a955d-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="a955d-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="a955d-126">Položka FullName CLR výjimky, která se právě zpracovává.</span><span class="sxs-lookup"><span data-stu-id="a955d-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="a955d-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="a955d-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="a955d-128">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="a955d-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a955d-129">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="a955d-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a955d-130">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a955d-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a955d-131">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a955d-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a955d-132">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a955d-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
