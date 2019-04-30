---
title: 1125 – InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 692c5e56dac0a69ab5705acd284f048391145641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924256"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="3ba6c-102">1125 – InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="3ba6c-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="3ba6c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3ba6c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ba6c-104">ID</span><span class="sxs-lookup"><span data-stu-id="3ba6c-104">ID</span></span>|<span data-ttu-id="3ba6c-105">1125</span><span class="sxs-lookup"><span data-stu-id="3ba6c-105">1125</span></span>|  
|<span data-ttu-id="3ba6c-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3ba6c-106">Keywords</span></span>|<span data-ttu-id="3ba6c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3ba6c-107">WFRuntime</span></span>|  
|<span data-ttu-id="3ba6c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3ba6c-108">Level</span></span>|<span data-ttu-id="3ba6c-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="3ba6c-109">Information</span></span>|  
|<span data-ttu-id="3ba6c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3ba6c-110">Channel</span></span>|<span data-ttu-id="3ba6c-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="3ba6c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3ba6c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3ba6c-112">Description</span></span>  
 <span data-ttu-id="3ba6c-113">Během kroku metoda CacheMetadata aktivity InvokeMethod znamená, že má být volána metoda není statická.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3ba6c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3ba6c-114">Message</span></span>  
 <span data-ttu-id="3ba6c-115">InvokeMethod '%1' - metoda není statická.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3ba6c-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3ba6c-116">Details</span></span>  
  
|<span data-ttu-id="3ba6c-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3ba6c-117">Data Item Name</span></span>|<span data-ttu-id="3ba6c-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="3ba6c-118">Data Item Type</span></span>|<span data-ttu-id="3ba6c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3ba6c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3ba6c-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="3ba6c-120">InvokeMethod</span></span>|<span data-ttu-id="3ba6c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3ba6c-121">xs:string</span></span>|<span data-ttu-id="3ba6c-122">Zobrazovaný název aktivity InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="3ba6c-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="3ba6c-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3ba6c-123">AppDomain</span></span>|<span data-ttu-id="3ba6c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3ba6c-124">xs:string</span></span>|<span data-ttu-id="3ba6c-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
