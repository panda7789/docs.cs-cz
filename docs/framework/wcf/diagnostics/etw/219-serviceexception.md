---
title: "219 – ServiceException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5750748f2885418b8992ce54bbdf6a92b8e1fe39
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="219---serviceexception"></a><span data-ttu-id="b9c38-102">219 – ServiceException</span><span class="sxs-lookup"><span data-stu-id="b9c38-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="b9c38-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9c38-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9c38-104">ID</span><span class="sxs-lookup"><span data-stu-id="b9c38-104">ID</span></span>|<span data-ttu-id="b9c38-105">219</span><span class="sxs-lookup"><span data-stu-id="b9c38-105">219</span></span>|  
|<span data-ttu-id="b9c38-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b9c38-106">Keywords</span></span>|<span data-ttu-id="b9c38-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b9c38-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b9c38-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b9c38-108">Level</span></span>|<span data-ttu-id="b9c38-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="b9c38-109">Error</span></span>|  
|<span data-ttu-id="b9c38-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b9c38-110">Channel</span></span>|<span data-ttu-id="b9c38-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="b9c38-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9c38-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b9c38-112">Description</span></span>  
 <span data-ttu-id="b9c38-113">Tato událost je vygenerované, když dojde k neošetřené výjimce služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b9c38-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="b9c38-114">To zahrnuje neošetřené výjimky během aktivace, při zpracování zprávy a v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="b9c38-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9c38-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b9c38-115">Message</span></span>  
 <span data-ttu-id="b9c38-116">Při zpracování zprávy došlo k neošetřené výjimce typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="b9c38-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="b9c38-117">ToString – Úplná výjimka: %1.</span><span class="sxs-lookup"><span data-stu-id="b9c38-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9c38-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b9c38-118">Details</span></span>  
  
|<span data-ttu-id="b9c38-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b9c38-119">Data Item Name</span></span>|<span data-ttu-id="b9c38-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b9c38-120">Data Item Type</span></span>|<span data-ttu-id="b9c38-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b9c38-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9c38-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="b9c38-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="b9c38-123">Výsledek volání `ToString`() na výjimky CLR.</span><span class="sxs-lookup"><span data-stu-id="b9c38-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="b9c38-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="b9c38-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="b9c38-125">Položka FullName CLR v výjimky typu.</span><span class="sxs-lookup"><span data-stu-id="b9c38-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="b9c38-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="b9c38-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="b9c38-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="b9c38-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b9c38-128">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="b9c38-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b9c38-129">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="b9c38-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b9c38-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b9c38-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b9c38-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b9c38-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
