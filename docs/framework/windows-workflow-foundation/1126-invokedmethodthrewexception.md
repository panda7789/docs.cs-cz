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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b11c2f167ce7afce992cddb2f32f840212d4ac8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="123b6-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="123b6-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="123b6-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="123b6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="123b6-104">ID</span><span class="sxs-lookup"><span data-stu-id="123b6-104">ID</span></span>|<span data-ttu-id="123b6-105">1126</span><span class="sxs-lookup"><span data-stu-id="123b6-105">1126</span></span>|  
|<span data-ttu-id="123b6-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="123b6-106">Keywords</span></span>|<span data-ttu-id="123b6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="123b6-107">WFRuntime</span></span>|  
|<span data-ttu-id="123b6-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="123b6-108">Level</span></span>|<span data-ttu-id="123b6-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="123b6-109">Information</span></span>|  
|<span data-ttu-id="123b6-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="123b6-110">Channel</span></span>|<span data-ttu-id="123b6-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="123b6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="123b6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="123b6-112">Description</span></span>  
 <span data-ttu-id="123b6-113">Označuje, že metoda volána aktivitou InvokeMethod došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="123b6-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="123b6-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="123b6-114">Message</span></span>  
 <span data-ttu-id="123b6-115">V metodě volá aktivita '%1' došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="123b6-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="123b6-116">%2</span><span class="sxs-lookup"><span data-stu-id="123b6-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="123b6-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="123b6-117">Details</span></span>  
  
|<span data-ttu-id="123b6-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="123b6-118">Data Item Name</span></span>|<span data-ttu-id="123b6-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="123b6-119">Data Item Type</span></span>|<span data-ttu-id="123b6-120">Popis</span><span class="sxs-lookup"><span data-stu-id="123b6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="123b6-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="123b6-121">InvokeMethod</span></span>|<span data-ttu-id="123b6-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="123b6-122">xs:string</span></span>|<span data-ttu-id="123b6-123">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="123b6-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="123b6-124">Výjimka</span><span class="sxs-lookup"><span data-stu-id="123b6-124">Exception</span></span>|<span data-ttu-id="123b6-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="123b6-125">xs:string</span></span>|<span data-ttu-id="123b6-126">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="123b6-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="123b6-127">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="123b6-127">AppDomain</span></span>|<span data-ttu-id="123b6-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="123b6-128">xs:string</span></span>|<span data-ttu-id="123b6-129">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="123b6-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
