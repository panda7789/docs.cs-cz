---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512228"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="e8030-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="e8030-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="e8030-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e8030-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8030-104">ID</span><span class="sxs-lookup"><span data-stu-id="e8030-104">ID</span></span>|<span data-ttu-id="e8030-105">3551</span><span class="sxs-lookup"><span data-stu-id="e8030-105">3551</span></span>|  
|<span data-ttu-id="e8030-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e8030-106">Keywords</span></span>|<span data-ttu-id="e8030-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e8030-107">WFServices</span></span>|  
|<span data-ttu-id="e8030-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e8030-108">Level</span></span>|<span data-ttu-id="e8030-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e8030-109">Information</span></span>|  
|<span data-ttu-id="e8030-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e8030-110">Channel</span></span>|<span data-ttu-id="e8030-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e8030-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e8030-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e8030-112">Description</span></span>  
 <span data-ttu-id="e8030-113">Označuje, že záložku obnovení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e8030-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="e8030-114">Ve vyrovnávací paměti přijímat operace se pokusí znovu po připravený na zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="e8030-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e8030-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e8030-115">Message</span></span>  
 <span data-ttu-id="e8030-116">Operace: %2' na instanci služby '%1' nelze v tuto chvíli provést.</span><span class="sxs-lookup"><span data-stu-id="e8030-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="e8030-117">Další pokus bude provádět, pokud je připraven ke zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="e8030-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e8030-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e8030-118">Details</span></span>  
  
|<span data-ttu-id="e8030-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e8030-119">Data Item Name</span></span>|<span data-ttu-id="e8030-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e8030-120">Data Item Type</span></span>|<span data-ttu-id="e8030-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e8030-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e8030-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="e8030-122">OperationName</span></span>|<span data-ttu-id="e8030-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="e8030-123">xs:string</span></span>|<span data-ttu-id="e8030-124">Název operace.</span><span class="sxs-lookup"><span data-stu-id="e8030-124">The name of the operation.</span></span>|  
|<span data-ttu-id="e8030-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="e8030-125">ServiceInstanceId</span></span>|<span data-ttu-id="e8030-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="e8030-126">xs:string</span></span>|<span data-ttu-id="e8030-127">Id instance služby.</span><span class="sxs-lookup"><span data-stu-id="e8030-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="e8030-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e8030-128">AppDomain</span></span>|<span data-ttu-id="e8030-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="e8030-129">xs:string</span></span>|<span data-ttu-id="e8030-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e8030-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
