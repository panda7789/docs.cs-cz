---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="30e2a-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="30e2a-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="30e2a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="30e2a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30e2a-104">ID</span><span class="sxs-lookup"><span data-stu-id="30e2a-104">ID</span></span>|<span data-ttu-id="30e2a-105">1126</span><span class="sxs-lookup"><span data-stu-id="30e2a-105">1126</span></span>|  
|<span data-ttu-id="30e2a-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="30e2a-106">Keywords</span></span>|<span data-ttu-id="30e2a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="30e2a-107">WFRuntime</span></span>|  
|<span data-ttu-id="30e2a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="30e2a-108">Level</span></span>|<span data-ttu-id="30e2a-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="30e2a-109">Information</span></span>|  
|<span data-ttu-id="30e2a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="30e2a-110">Channel</span></span>|<span data-ttu-id="30e2a-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="30e2a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30e2a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="30e2a-112">Description</span></span>  
 <span data-ttu-id="30e2a-113">Označuje, že metoda volána aktivitou InvokeMethod došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="30e2a-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30e2a-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30e2a-114">Message</span></span>  
 <span data-ttu-id="30e2a-115">V metodě volá aktivita '%1' došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="30e2a-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="30e2a-116">%2</span><span class="sxs-lookup"><span data-stu-id="30e2a-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="30e2a-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="30e2a-117">Details</span></span>  
  
|<span data-ttu-id="30e2a-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="30e2a-118">Data Item Name</span></span>|<span data-ttu-id="30e2a-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="30e2a-119">Data Item Type</span></span>|<span data-ttu-id="30e2a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="30e2a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30e2a-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="30e2a-121">InvokeMethod</span></span>|<span data-ttu-id="30e2a-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="30e2a-122">xs:string</span></span>|<span data-ttu-id="30e2a-123">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="30e2a-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="30e2a-124">Výjimka</span><span class="sxs-lookup"><span data-stu-id="30e2a-124">Exception</span></span>|<span data-ttu-id="30e2a-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="30e2a-125">xs:string</span></span>|<span data-ttu-id="30e2a-126">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="30e2a-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="30e2a-127">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="30e2a-127">AppDomain</span></span>|<span data-ttu-id="30e2a-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="30e2a-128">xs:string</span></span>|<span data-ttu-id="30e2a-129">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="30e2a-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
