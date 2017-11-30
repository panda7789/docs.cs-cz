---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="be141-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="be141-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="be141-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="be141-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be141-104">ID</span><span class="sxs-lookup"><span data-stu-id="be141-104">ID</span></span>|<span data-ttu-id="be141-105">4203</span><span class="sxs-lookup"><span data-stu-id="be141-105">4203</span></span>|  
|<span data-ttu-id="be141-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="be141-106">Keywords</span></span>|<span data-ttu-id="be141-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="be141-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="be141-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="be141-108">Level</span></span>|<span data-ttu-id="be141-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="be141-109">Error</span></span>|  
|<span data-ttu-id="be141-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="be141-110">Channel</span></span>|<span data-ttu-id="be141-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="be141-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be141-112">Popis</span><span class="sxs-lookup"><span data-stu-id="be141-112">Description</span></span>  
 <span data-ttu-id="be141-113">Určuje zprostředkovatele SQL se nepodařilo prodloužit platnost zámku z důvodu vypršení buď zámku již uplynul nebo vlastníka zámku byla odstraněna.</span><span class="sxs-lookup"><span data-stu-id="be141-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="be141-114">SqlWorkflowInstanceStore bude ukončeno.</span><span class="sxs-lookup"><span data-stu-id="be141-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be141-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="be141-115">Message</span></span>  
 <span data-ttu-id="be141-116">Prodloužit platnost uzamčení se nezdařilo, vypršení platnosti zámku již předán nebo vlastníka zámku byla odstraněna.</span><span class="sxs-lookup"><span data-stu-id="be141-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="be141-117">Probíhá rušení SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="be141-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be141-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="be141-118">Details</span></span>  
  
|<span data-ttu-id="be141-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="be141-119">Data Item Name</span></span>|<span data-ttu-id="be141-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="be141-120">Data Item Type</span></span>|<span data-ttu-id="be141-121">Popis</span><span class="sxs-lookup"><span data-stu-id="be141-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be141-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="be141-122">AppDomain</span></span>|<span data-ttu-id="be141-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="be141-123">xs:string</span></span>|<span data-ttu-id="be141-124">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="be141-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
