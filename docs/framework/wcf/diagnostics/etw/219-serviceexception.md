---
title: 219 – ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460512"
---
# <a name="219---serviceexception"></a><span data-ttu-id="8f2b4-102">219 – ServiceException</span><span class="sxs-lookup"><span data-stu-id="8f2b4-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="8f2b4-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8f2b4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f2b4-104">ID</span><span class="sxs-lookup"><span data-stu-id="8f2b4-104">ID</span></span>|<span data-ttu-id="8f2b4-105">219</span><span class="sxs-lookup"><span data-stu-id="8f2b4-105">219</span></span>|  
|<span data-ttu-id="8f2b4-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8f2b4-106">Keywords</span></span>|<span data-ttu-id="8f2b4-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8f2b4-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8f2b4-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8f2b4-108">Level</span></span>|<span data-ttu-id="8f2b4-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="8f2b4-109">Error</span></span>|  
|<span data-ttu-id="8f2b4-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8f2b4-110">Channel</span></span>|<span data-ttu-id="8f2b4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8f2b4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8f2b4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8f2b4-112">Description</span></span>  
 <span data-ttu-id="8f2b4-113">Tato událost je vygenerované, když dojde k neošetřené výjimce služby WCF.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="8f2b4-114">To zahrnuje neošetřené výjimky během aktivace, při zpracování zprávy a v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8f2b4-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8f2b4-115">Message</span></span>  
 <span data-ttu-id="8f2b4-116">Při zpracování zprávy došlo k neošetřené výjimce typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="8f2b4-117">ToString – Úplná výjimka: %1.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8f2b4-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8f2b4-118">Details</span></span>  
  
|<span data-ttu-id="8f2b4-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8f2b4-119">Data Item Name</span></span>|<span data-ttu-id="8f2b4-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8f2b4-120">Data Item Type</span></span>|<span data-ttu-id="8f2b4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8f2b4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8f2b4-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="8f2b4-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="8f2b4-123">Výsledek volání `ToString`() na výjimky CLR.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="8f2b4-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="8f2b4-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="8f2b4-125">Položka FullName CLR v výjimky typu.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="8f2b4-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="8f2b4-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="8f2b4-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8f2b4-128">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8f2b4-129">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8f2b4-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8f2b4-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8f2b4-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8f2b4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
