---
title: 219 – ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781729"
---
# <a name="219---serviceexception"></a><span data-ttu-id="b8e90-102">219 – ServiceException</span><span class="sxs-lookup"><span data-stu-id="b8e90-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="b8e90-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b8e90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8e90-104">ID</span><span class="sxs-lookup"><span data-stu-id="b8e90-104">ID</span></span>|<span data-ttu-id="b8e90-105">219</span><span class="sxs-lookup"><span data-stu-id="b8e90-105">219</span></span>|  
|<span data-ttu-id="b8e90-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b8e90-106">Keywords</span></span>|<span data-ttu-id="b8e90-107">EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b8e90-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b8e90-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b8e90-108">Level</span></span>|<span data-ttu-id="b8e90-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="b8e90-109">Error</span></span>|  
|<span data-ttu-id="b8e90-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b8e90-110">Channel</span></span>|<span data-ttu-id="b8e90-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b8e90-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8e90-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b8e90-112">Description</span></span>  
 <span data-ttu-id="b8e90-113">Tato událost je vygenerován, když dojde k neošetřené výjimce ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="b8e90-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="b8e90-114">To zahrnuje neošetřené výjimky během aktivace, při zpracování zprávy a v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="b8e90-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8e90-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b8e90-115">Message</span></span>  
 <span data-ttu-id="b8e90-116">Při zpracování zprávy došlo k neošetřené výjimce typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="b8e90-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="b8e90-117">ToString úplných informacích o výjimce: %1.</span><span class="sxs-lookup"><span data-stu-id="b8e90-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8e90-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b8e90-118">Details</span></span>  
  
|<span data-ttu-id="b8e90-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b8e90-119">Data Item Name</span></span>|<span data-ttu-id="b8e90-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="b8e90-120">Data Item Type</span></span>|<span data-ttu-id="b8e90-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b8e90-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8e90-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="b8e90-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="b8e90-123">Výsledek volání `ToString`() na výjimky modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e90-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="b8e90-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="b8e90-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="b8e90-125">CLR úplný název typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="b8e90-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="b8e90-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="b8e90-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="b8e90-127">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="b8e90-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b8e90-128">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b8e90-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b8e90-129">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="b8e90-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b8e90-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8e90-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b8e90-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b8e90-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
