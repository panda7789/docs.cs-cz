---
title: 1132 – InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924212"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="4fd56-102">1132 – InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="4fd56-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="4fd56-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4fd56-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4fd56-104">ID</span><span class="sxs-lookup"><span data-stu-id="4fd56-104">ID</span></span>|<span data-ttu-id="4fd56-105">1132</span><span class="sxs-lookup"><span data-stu-id="4fd56-105">1132</span></span>|  
|<span data-ttu-id="4fd56-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4fd56-106">Keywords</span></span>|<span data-ttu-id="4fd56-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4fd56-107">WFRuntime</span></span>|  
|<span data-ttu-id="4fd56-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="4fd56-108">Level</span></span>|<span data-ttu-id="4fd56-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="4fd56-109">Information</span></span>|  
|<span data-ttu-id="4fd56-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="4fd56-110">Channel</span></span>|<span data-ttu-id="4fd56-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="4fd56-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4fd56-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4fd56-112">Description</span></span>  
 <span data-ttu-id="4fd56-113">Během kroku CacheMetadata aktivity InvokeMethod označuje, že ho nepoužívá asynchronní vzorek, při volání metody.</span><span class="sxs-lookup"><span data-stu-id="4fd56-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4fd56-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="4fd56-114">Message</span></span>  
 <span data-ttu-id="4fd56-115">InvokeMethod '%1' - metoda nepoužívá asynchronní vzorek.</span><span class="sxs-lookup"><span data-stu-id="4fd56-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4fd56-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4fd56-116">Details</span></span>  
  
|<span data-ttu-id="4fd56-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="4fd56-117">Data Item Name</span></span>|<span data-ttu-id="4fd56-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="4fd56-118">Data Item Type</span></span>|<span data-ttu-id="4fd56-119">Popis</span><span class="sxs-lookup"><span data-stu-id="4fd56-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4fd56-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="4fd56-120">InvokeMethod</span></span>|<span data-ttu-id="4fd56-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fd56-121">xs:string</span></span>|<span data-ttu-id="4fd56-122">Zobrazovaný název aktivity InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="4fd56-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="4fd56-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4fd56-123">AppDomain</span></span>|<span data-ttu-id="4fd56-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fd56-124">xs:string</span></span>|<span data-ttu-id="4fd56-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4fd56-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
