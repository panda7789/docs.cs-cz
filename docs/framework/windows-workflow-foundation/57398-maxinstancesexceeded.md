---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512548"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="10fea-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="10fea-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="10fea-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="10fea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10fea-104">ID</span><span class="sxs-lookup"><span data-stu-id="10fea-104">ID</span></span>|<span data-ttu-id="10fea-105">57398</span><span class="sxs-lookup"><span data-stu-id="10fea-105">57398</span></span>|  
|<span data-ttu-id="10fea-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="10fea-106">Keywords</span></span>|<span data-ttu-id="10fea-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="10fea-107">WFServices</span></span>|  
|<span data-ttu-id="10fea-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="10fea-108">Level</span></span>|<span data-ttu-id="10fea-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="10fea-109">Warning</span></span>|  
|<span data-ttu-id="10fea-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="10fea-110">Channel</span></span>|<span data-ttu-id="10fea-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="10fea-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="10fea-112">Popis</span><span class="sxs-lookup"><span data-stu-id="10fea-112">Description</span></span>  
 <span data-ttu-id="10fea-113">Označuje, že systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="10fea-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="10fea-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="10fea-114">Message</span></span>  
 <span data-ttu-id="10fea-115">Systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="10fea-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="10fea-116">Limit pro toto omezení byla nastavena na %1.</span><span class="sxs-lookup"><span data-stu-id="10fea-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="10fea-117">Hodnota omezení lze změnit úpravou atribut 'maxConcurrentInstances' v omezení ServiceThrottle s hodnotou elementu nebo úpravou vlastnosti 'MaxConcurrentInstances' na chování třídy ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="10fea-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="10fea-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="10fea-118">Details</span></span>  
  
|<span data-ttu-id="10fea-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="10fea-119">Data Item Name</span></span>|<span data-ttu-id="10fea-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="10fea-120">Data Item Type</span></span>|<span data-ttu-id="10fea-121">Popis</span><span class="sxs-lookup"><span data-stu-id="10fea-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="10fea-122">Název</span><span class="sxs-lookup"><span data-stu-id="10fea-122">Name</span></span>|<span data-ttu-id="10fea-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="10fea-123">xs:string</span></span>|<span data-ttu-id="10fea-124">Název položky.</span><span class="sxs-lookup"><span data-stu-id="10fea-124">The name of the item.</span></span>|  
|<span data-ttu-id="10fea-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="10fea-125">AppDomain</span></span>|<span data-ttu-id="10fea-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="10fea-126">xs:string</span></span>|<span data-ttu-id="10fea-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="10fea-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
