---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510721"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="a9d62-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="a9d62-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="a9d62-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9d62-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9d62-104">ID</span><span class="sxs-lookup"><span data-stu-id="a9d62-104">ID</span></span>|<span data-ttu-id="a9d62-105">2577</span><span class="sxs-lookup"><span data-stu-id="a9d62-105">2577</span></span>|  
|<span data-ttu-id="a9d62-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a9d62-106">Keywords</span></span>|<span data-ttu-id="a9d62-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="a9d62-107">WFActivities</span></span>|  
|<span data-ttu-id="a9d62-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a9d62-108">Level</span></span>|<span data-ttu-id="a9d62-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="a9d62-109">Warning</span></span>|  
|<span data-ttu-id="a9d62-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a9d62-110">Channel</span></span>|<span data-ttu-id="a9d62-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a9d62-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9d62-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a9d62-112">Description</span></span>  
 <span data-ttu-id="a9d62-113">Označuje, že podřízené aktivity TryCatch aktivity došlo k výjimce při zrušení.</span><span class="sxs-lookup"><span data-stu-id="a9d62-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9d62-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a9d62-114">Message</span></span>  
 <span data-ttu-id="a9d62-115">Aktivita podřízené aktivity TryCatch '%1' došlo k výjimce při zrušení.</span><span class="sxs-lookup"><span data-stu-id="a9d62-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9d62-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a9d62-116">Details</span></span>  
  
|<span data-ttu-id="a9d62-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a9d62-117">Data Item Name</span></span>|<span data-ttu-id="a9d62-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a9d62-118">Data Item Type</span></span>|<span data-ttu-id="a9d62-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a9d62-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9d62-120">displayName</span><span class="sxs-lookup"><span data-stu-id="a9d62-120">DisplayName</span></span>|<span data-ttu-id="a9d62-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="a9d62-121">xs:string</span></span>|<span data-ttu-id="a9d62-122">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="a9d62-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="a9d62-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a9d62-123">AppDomain</span></span>|<span data-ttu-id="a9d62-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="a9d62-124">xs:string</span></span>|<span data-ttu-id="a9d62-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a9d62-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
