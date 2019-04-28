---
title: 2578 – TryCatchExceptionFromCatchOrFinally
ms.date: 03/30/2017
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
ms.openlocfilehash: 46fb52e665d49ed7a0336dbeeb6ed07f0d479fb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755607"
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a><span data-ttu-id="61d70-102">2578 – TryCatchExceptionFromCatchOrFinally</span><span class="sxs-lookup"><span data-stu-id="61d70-102">2578 - TryCatchExceptionFromCatchOrFinally</span></span>
## <a name="properties"></a><span data-ttu-id="61d70-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="61d70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61d70-104">ID</span><span class="sxs-lookup"><span data-stu-id="61d70-104">ID</span></span>|<span data-ttu-id="61d70-105">2578</span><span class="sxs-lookup"><span data-stu-id="61d70-105">2578</span></span>|  
|<span data-ttu-id="61d70-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="61d70-106">Keywords</span></span>|<span data-ttu-id="61d70-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="61d70-107">WFActivities</span></span>|  
|<span data-ttu-id="61d70-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="61d70-108">Level</span></span>|<span data-ttu-id="61d70-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="61d70-109">Warning</span></span>|  
|<span data-ttu-id="61d70-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="61d70-110">Channel</span></span>|<span data-ttu-id="61d70-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="61d70-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="61d70-112">Popis</span><span class="sxs-lookup"><span data-stu-id="61d70-112">Description</span></span>  
 <span data-ttu-id="61d70-113">Označuje bloku Catch nebo Finally aktivita byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="61d70-113">Indicates a Catch or Finally activity has thrown an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="61d70-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="61d70-114">Message</span></span>  
 <span data-ttu-id="61d70-115">Aktivita Catch nebo Finally, která je přidružená k aktivitě TryCatch '%1' byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="61d70-115">A Catch or Finally activity that is associated with the TryCatch activity '%1' has thrown an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="61d70-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="61d70-116">Details</span></span>  
  
|<span data-ttu-id="61d70-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="61d70-117">Data Item Name</span></span>|<span data-ttu-id="61d70-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="61d70-118">Data Item Type</span></span>|<span data-ttu-id="61d70-119">Popis</span><span class="sxs-lookup"><span data-stu-id="61d70-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="61d70-120">displayName</span><span class="sxs-lookup"><span data-stu-id="61d70-120">DisplayName</span></span>|<span data-ttu-id="61d70-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="61d70-121">xs:string</span></span>|<span data-ttu-id="61d70-122">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="61d70-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="61d70-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="61d70-123">AppDomain</span></span>|<span data-ttu-id="61d70-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="61d70-124">xs:string</span></span>|<span data-ttu-id="61d70-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="61d70-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
