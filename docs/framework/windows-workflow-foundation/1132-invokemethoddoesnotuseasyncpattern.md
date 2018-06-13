---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511866"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="bae1e-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="bae1e-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="bae1e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bae1e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bae1e-104">ID</span><span class="sxs-lookup"><span data-stu-id="bae1e-104">ID</span></span>|<span data-ttu-id="bae1e-105">1132</span><span class="sxs-lookup"><span data-stu-id="bae1e-105">1132</span></span>|  
|<span data-ttu-id="bae1e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bae1e-106">Keywords</span></span>|<span data-ttu-id="bae1e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bae1e-107">WFRuntime</span></span>|  
|<span data-ttu-id="bae1e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="bae1e-108">Level</span></span>|<span data-ttu-id="bae1e-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="bae1e-109">Information</span></span>|  
|<span data-ttu-id="bae1e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="bae1e-110">Channel</span></span>|<span data-ttu-id="bae1e-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="bae1e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bae1e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bae1e-112">Description</span></span>  
 <span data-ttu-id="bae1e-113">Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho není vzoru async při volání metody.</span><span class="sxs-lookup"><span data-stu-id="bae1e-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bae1e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bae1e-114">Message</span></span>  
 <span data-ttu-id="bae1e-115">InvokeMethod '%1' - metoda nepoužívá asynchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="bae1e-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bae1e-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bae1e-116">Details</span></span>  
  
|<span data-ttu-id="bae1e-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="bae1e-117">Data Item Name</span></span>|<span data-ttu-id="bae1e-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="bae1e-118">Data Item Type</span></span>|<span data-ttu-id="bae1e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="bae1e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bae1e-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="bae1e-120">InvokeMethod</span></span>|<span data-ttu-id="bae1e-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="bae1e-121">xs:string</span></span>|<span data-ttu-id="bae1e-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="bae1e-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="bae1e-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bae1e-123">AppDomain</span></span>|<span data-ttu-id="bae1e-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="bae1e-124">xs:string</span></span>|<span data-ttu-id="bae1e-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bae1e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
