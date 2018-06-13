---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513926"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="0f0f5-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="0f0f5-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="0f0f5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0f0f5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f0f5-104">ID</span><span class="sxs-lookup"><span data-stu-id="0f0f5-104">ID</span></span>|<span data-ttu-id="0f0f5-105">4203</span><span class="sxs-lookup"><span data-stu-id="0f0f5-105">4203</span></span>|  
|<span data-ttu-id="0f0f5-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0f0f5-106">Keywords</span></span>|<span data-ttu-id="0f0f5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0f0f5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0f0f5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0f0f5-108">Level</span></span>|<span data-ttu-id="0f0f5-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="0f0f5-109">Error</span></span>|  
|<span data-ttu-id="0f0f5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0f0f5-110">Channel</span></span>|<span data-ttu-id="0f0f5-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="0f0f5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0f0f5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0f5-112">Description</span></span>  
 <span data-ttu-id="0f0f5-113">Určuje zprostředkovatele SQL se nepodařilo prodloužit platnost zámku z důvodu vypršení buď zámku již uplynul nebo vlastníka zámku byla odstraněna.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="0f0f5-114">SqlWorkflowInstanceStore bude ukončeno.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0f0f5-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0f0f5-115">Message</span></span>  
 <span data-ttu-id="0f0f5-116">Prodloužit platnost uzamčení se nezdařilo, vypršení platnosti zámku již předán nebo vlastníka zámku byla odstraněna.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="0f0f5-117">Probíhá rušení SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0f0f5-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0f0f5-118">Details</span></span>  
  
|<span data-ttu-id="0f0f5-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0f0f5-119">Data Item Name</span></span>|<span data-ttu-id="0f0f5-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="0f0f5-120">Data Item Type</span></span>|<span data-ttu-id="0f0f5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0f5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0f0f5-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="0f0f5-122">AppDomain</span></span>|<span data-ttu-id="0f0f5-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="0f0f5-123">xs:string</span></span>|<span data-ttu-id="0f0f5-124">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0f0f5-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
