---
title: 4203 – RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774345"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="ec6cb-102">4203 – RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="ec6cb-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="ec6cb-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ec6cb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec6cb-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec6cb-104">ID</span></span>|<span data-ttu-id="ec6cb-105">4203</span><span class="sxs-lookup"><span data-stu-id="ec6cb-105">4203</span></span>|  
|<span data-ttu-id="ec6cb-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ec6cb-106">Keywords</span></span>|<span data-ttu-id="ec6cb-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ec6cb-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ec6cb-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ec6cb-108">Level</span></span>|<span data-ttu-id="ec6cb-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="ec6cb-109">Error</span></span>|  
|<span data-ttu-id="ec6cb-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ec6cb-110">Channel</span></span>|<span data-ttu-id="ec6cb-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ec6cb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec6cb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ec6cb-112">Description</span></span>  
 <span data-ttu-id="ec6cb-113">Určuje zprostředkovatele SQL se nezdařilo se prodloužit platnost zámku z důvodu buď platnost zámku již předaný nebo byl odstraněn vlastník zámku.</span><span class="sxs-lookup"><span data-stu-id="ec6cb-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="ec6cb-114">Úložiště SqlWorkflowInstanceStore se přeruší.</span><span class="sxs-lookup"><span data-stu-id="ec6cb-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec6cb-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ec6cb-115">Message</span></span>  
 <span data-ttu-id="ec6cb-116">Nepovedlo se prodloužit platnost zámku, platnost zámku již vypršela nebo byl odstraněn vlastník zámku.</span><span class="sxs-lookup"><span data-stu-id="ec6cb-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="ec6cb-117">Přerušení metody SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="ec6cb-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec6cb-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ec6cb-118">Details</span></span>  
  
|<span data-ttu-id="ec6cb-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ec6cb-119">Data Item Name</span></span>|<span data-ttu-id="ec6cb-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="ec6cb-120">Data Item Type</span></span>|<span data-ttu-id="ec6cb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ec6cb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec6cb-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ec6cb-122">AppDomain</span></span>|<span data-ttu-id="ec6cb-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec6cb-123">xs:string</span></span>|<span data-ttu-id="ec6cb-124">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ec6cb-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
