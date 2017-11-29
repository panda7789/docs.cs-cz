---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a380def22c270a3fafe118a426609a93862c447
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="f541d-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="f541d-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="f541d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f541d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f541d-104">ID</span><span class="sxs-lookup"><span data-stu-id="f541d-104">ID</span></span>|<span data-ttu-id="f541d-105">3551</span><span class="sxs-lookup"><span data-stu-id="f541d-105">3551</span></span>|  
|<span data-ttu-id="f541d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f541d-106">Keywords</span></span>|<span data-ttu-id="f541d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f541d-107">WFServices</span></span>|  
|<span data-ttu-id="f541d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f541d-108">Level</span></span>|<span data-ttu-id="f541d-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="f541d-109">Information</span></span>|  
|<span data-ttu-id="f541d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f541d-110">Channel</span></span>|<span data-ttu-id="f541d-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="f541d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f541d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f541d-112">Description</span></span>  
 <span data-ttu-id="f541d-113">Označuje, že záložku obnovení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="f541d-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="f541d-114">Ve vyrovnávací paměti přijímat operace se pokusí znovu po připravený na zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="f541d-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f541d-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f541d-115">Message</span></span>  
 <span data-ttu-id="f541d-116">Operace: %2' na instanci služby '%1' nelze v tuto chvíli provést.</span><span class="sxs-lookup"><span data-stu-id="f541d-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="f541d-117">Další pokus bude provádět, pokud je připraven ke zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="f541d-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f541d-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f541d-118">Details</span></span>  
  
|<span data-ttu-id="f541d-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f541d-119">Data Item Name</span></span>|<span data-ttu-id="f541d-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="f541d-120">Data Item Type</span></span>|<span data-ttu-id="f541d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f541d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f541d-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="f541d-122">OperationName</span></span>|<span data-ttu-id="f541d-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="f541d-123">xs:string</span></span>|<span data-ttu-id="f541d-124">Název operace.</span><span class="sxs-lookup"><span data-stu-id="f541d-124">The name of the operation.</span></span>|  
|<span data-ttu-id="f541d-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="f541d-125">ServiceInstanceId</span></span>|<span data-ttu-id="f541d-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="f541d-126">xs:string</span></span>|<span data-ttu-id="f541d-127">Id instance služby.</span><span class="sxs-lookup"><span data-stu-id="f541d-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="f541d-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f541d-128">AppDomain</span></span>|<span data-ttu-id="f541d-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="f541d-129">xs:string</span></span>|<span data-ttu-id="f541d-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f541d-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
