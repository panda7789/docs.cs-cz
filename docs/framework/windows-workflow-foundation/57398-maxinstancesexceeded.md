---
title: 57398 – MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945961"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="36f13-102">57398 – MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="36f13-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="36f13-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="36f13-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36f13-104">ID</span><span class="sxs-lookup"><span data-stu-id="36f13-104">ID</span></span>|<span data-ttu-id="36f13-105">57398</span><span class="sxs-lookup"><span data-stu-id="36f13-105">57398</span></span>|  
|<span data-ttu-id="36f13-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="36f13-106">Keywords</span></span>|<span data-ttu-id="36f13-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="36f13-107">WFServices</span></span>|  
|<span data-ttu-id="36f13-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="36f13-108">Level</span></span>|<span data-ttu-id="36f13-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="36f13-109">Warning</span></span>|  
|<span data-ttu-id="36f13-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="36f13-110">Channel</span></span>|<span data-ttu-id="36f13-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="36f13-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="36f13-112">Popis</span><span class="sxs-lookup"><span data-stu-id="36f13-112">Description</span></span>  
 <span data-ttu-id="36f13-113">Označuje, že systém dosáhl limitu nastaveného pro omezení "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="36f13-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="36f13-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="36f13-114">Message</span></span>  
 <span data-ttu-id="36f13-115">Systém dosáhl limitu nastaveného pro omezení "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="36f13-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="36f13-116">Limit pro toto omezení byl nastaven na hodnotu %1.</span><span class="sxs-lookup"><span data-stu-id="36f13-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="36f13-117">Hodnotu omezení lze změnit úpravou atributu "maxConcurrentInstances' v elementu serviceThrottle nebo upravením vlastnosti 'MaxConcurrentInstances' v třídě chování ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="36f13-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="36f13-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="36f13-118">Details</span></span>  
  
|<span data-ttu-id="36f13-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="36f13-119">Data Item Name</span></span>|<span data-ttu-id="36f13-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="36f13-120">Data Item Type</span></span>|<span data-ttu-id="36f13-121">Popis</span><span class="sxs-lookup"><span data-stu-id="36f13-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="36f13-122">Název</span><span class="sxs-lookup"><span data-stu-id="36f13-122">Name</span></span>|<span data-ttu-id="36f13-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="36f13-123">xs:string</span></span>|<span data-ttu-id="36f13-124">Název položky.</span><span class="sxs-lookup"><span data-stu-id="36f13-124">The name of the item.</span></span>|  
|<span data-ttu-id="36f13-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="36f13-125">AppDomain</span></span>|<span data-ttu-id="36f13-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="36f13-126">xs:string</span></span>|<span data-ttu-id="36f13-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="36f13-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
