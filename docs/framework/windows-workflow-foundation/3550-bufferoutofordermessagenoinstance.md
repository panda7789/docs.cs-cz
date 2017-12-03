---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eabc6a6915560d8c49e695d5d681f1544689cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="082a7-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="082a7-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="082a7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="082a7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="082a7-104">ID</span><span class="sxs-lookup"><span data-stu-id="082a7-104">ID</span></span>|<span data-ttu-id="082a7-105">3550</span><span class="sxs-lookup"><span data-stu-id="082a7-105">3550</span></span>|  
|<span data-ttu-id="082a7-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="082a7-106">Keywords</span></span>|<span data-ttu-id="082a7-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="082a7-107">WFServices</span></span>|  
|<span data-ttu-id="082a7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="082a7-108">Level</span></span>|<span data-ttu-id="082a7-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="082a7-109">Information</span></span>|  
|<span data-ttu-id="082a7-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="082a7-110">Channel</span></span>|<span data-ttu-id="082a7-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="082a7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="082a7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="082a7-112">Description</span></span>  
 <span data-ttu-id="082a7-113">Označuje, že vyrovnávací pamětí příjmu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="082a7-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="082a7-114">Operaci se pokusí znovu po připravený na zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="082a7-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="082a7-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="082a7-115">Message</span></span>  
 <span data-ttu-id="082a7-116">Operaci '%1' nelze v tuto chvíli provést.</span><span class="sxs-lookup"><span data-stu-id="082a7-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="082a7-117">Další pokus bude provádět, pokud je připraven ke zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="082a7-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="082a7-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="082a7-118">Details</span></span>  
  
|<span data-ttu-id="082a7-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="082a7-119">Data Item Name</span></span>|<span data-ttu-id="082a7-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="082a7-120">Data Item Type</span></span>|<span data-ttu-id="082a7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="082a7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="082a7-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="082a7-122">OperationName</span></span>|<span data-ttu-id="082a7-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="082a7-123">xs:string</span></span>|<span data-ttu-id="082a7-124">Název operace.</span><span class="sxs-lookup"><span data-stu-id="082a7-124">The name of the operation.</span></span>|  
|<span data-ttu-id="082a7-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="082a7-125">AppDomain</span></span>|<span data-ttu-id="082a7-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="082a7-126">xs:string</span></span>|<span data-ttu-id="082a7-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="082a7-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
