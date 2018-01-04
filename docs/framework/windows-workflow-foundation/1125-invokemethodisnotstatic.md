---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8b5e255e9a753c6476a070609b0cbda189d37a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="ef501-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="ef501-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="ef501-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ef501-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef501-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef501-104">ID</span></span>|<span data-ttu-id="ef501-105">1125</span><span class="sxs-lookup"><span data-stu-id="ef501-105">1125</span></span>|  
|<span data-ttu-id="ef501-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ef501-106">Keywords</span></span>|<span data-ttu-id="ef501-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ef501-107">WFRuntime</span></span>|  
|<span data-ttu-id="ef501-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ef501-108">Level</span></span>|<span data-ttu-id="ef501-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="ef501-109">Information</span></span>|  
|<span data-ttu-id="ef501-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ef501-110">Channel</span></span>|<span data-ttu-id="ef501-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ef501-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef501-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ef501-112">Description</span></span>  
 <span data-ttu-id="ef501-113">Během kroku CacheMetadata InvokeMethod aktivity znamená, že metoda k vyvolání není statický.</span><span class="sxs-lookup"><span data-stu-id="ef501-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef501-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ef501-114">Message</span></span>  
 <span data-ttu-id="ef501-115">InvokeMethod '%1' - metoda nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="ef501-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef501-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ef501-116">Details</span></span>  
  
|<span data-ttu-id="ef501-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ef501-117">Data Item Name</span></span>|<span data-ttu-id="ef501-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ef501-118">Data Item Type</span></span>|<span data-ttu-id="ef501-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ef501-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef501-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="ef501-120">InvokeMethod</span></span>|<span data-ttu-id="ef501-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="ef501-121">xs:string</span></span>|<span data-ttu-id="ef501-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="ef501-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="ef501-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ef501-123">AppDomain</span></span>|<span data-ttu-id="ef501-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="ef501-124">xs:string</span></span>|<span data-ttu-id="ef501-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ef501-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
