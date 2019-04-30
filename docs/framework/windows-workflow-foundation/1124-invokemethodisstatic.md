---
title: 1124 – InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 49a9dec73392681fd4150c611f78399a1e15dd48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924056"
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="f233a-102">1124 – InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="f233a-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="f233a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f233a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f233a-104">ID</span><span class="sxs-lookup"><span data-stu-id="f233a-104">ID</span></span>|<span data-ttu-id="f233a-105">1124</span><span class="sxs-lookup"><span data-stu-id="f233a-105">1124</span></span>|  
|<span data-ttu-id="f233a-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f233a-106">Keywords</span></span>|<span data-ttu-id="f233a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f233a-107">WFRuntime</span></span>|  
|<span data-ttu-id="f233a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f233a-108">Level</span></span>|<span data-ttu-id="f233a-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="f233a-109">Information</span></span>|  
|<span data-ttu-id="f233a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f233a-110">Channel</span></span>|<span data-ttu-id="f233a-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="f233a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f233a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f233a-112">Description</span></span>  
 <span data-ttu-id="f233a-113">Během kroku metoda CacheMetadata aktivity InvokeMethod značí, že má být volána metoda je statická.</span><span class="sxs-lookup"><span data-stu-id="f233a-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f233a-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f233a-114">Message</span></span>  
 <span data-ttu-id="f233a-115">InvokeMethod '%1' - metoda je statická.</span><span class="sxs-lookup"><span data-stu-id="f233a-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f233a-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f233a-116">Details</span></span>  
  
|<span data-ttu-id="f233a-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f233a-117">Data Item Name</span></span>|<span data-ttu-id="f233a-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="f233a-118">Data Item Type</span></span>|<span data-ttu-id="f233a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f233a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f233a-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f233a-120">InvokeMethod</span></span>|<span data-ttu-id="f233a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f233a-121">xs:string</span></span>|<span data-ttu-id="f233a-122">Zobrazovaný název aktivity InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f233a-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f233a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f233a-123">AppDomain</span></span>|<span data-ttu-id="f233a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f233a-124">xs:string</span></span>|<span data-ttu-id="f233a-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f233a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
