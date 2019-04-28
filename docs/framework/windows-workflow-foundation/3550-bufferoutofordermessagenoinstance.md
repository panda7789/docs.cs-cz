---
title: 3550 – BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755581"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="e2590-102">3550 – BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="e2590-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="e2590-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e2590-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2590-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2590-104">ID</span></span>|<span data-ttu-id="e2590-105">3550</span><span class="sxs-lookup"><span data-stu-id="e2590-105">3550</span></span>|  
|<span data-ttu-id="e2590-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e2590-106">Keywords</span></span>|<span data-ttu-id="e2590-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e2590-107">WFServices</span></span>|  
|<span data-ttu-id="e2590-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e2590-108">Level</span></span>|<span data-ttu-id="e2590-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e2590-109">Information</span></span>|  
|<span data-ttu-id="e2590-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e2590-110">Channel</span></span>|<span data-ttu-id="e2590-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e2590-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2590-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e2590-112">Description</span></span>  
 <span data-ttu-id="e2590-113">Označuje, že ve vyrovnávací paměti receive se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e2590-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="e2590-114">Operace se znovu pokusí, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.</span><span class="sxs-lookup"><span data-stu-id="e2590-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2590-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e2590-115">Message</span></span>  
 <span data-ttu-id="e2590-116">V tuto chvíli nejde provést operaci '%1'.</span><span class="sxs-lookup"><span data-stu-id="e2590-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="e2590-117">Další pokus bude proveden, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.</span><span class="sxs-lookup"><span data-stu-id="e2590-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2590-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e2590-118">Details</span></span>  
  
|<span data-ttu-id="e2590-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e2590-119">Data Item Name</span></span>|<span data-ttu-id="e2590-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e2590-120">Data Item Type</span></span>|<span data-ttu-id="e2590-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e2590-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2590-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="e2590-122">OperationName</span></span>|<span data-ttu-id="e2590-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2590-123">xs:string</span></span>|<span data-ttu-id="e2590-124">Název operace.</span><span class="sxs-lookup"><span data-stu-id="e2590-124">The name of the operation.</span></span>|  
|<span data-ttu-id="e2590-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2590-125">AppDomain</span></span>|<span data-ttu-id="e2590-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2590-126">xs:string</span></span>|<span data-ttu-id="e2590-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2590-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
