---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511589"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="6fc72-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="6fc72-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="6fc72-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6fc72-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6fc72-104">ID</span><span class="sxs-lookup"><span data-stu-id="6fc72-104">ID</span></span>|<span data-ttu-id="6fc72-105">3550</span><span class="sxs-lookup"><span data-stu-id="6fc72-105">3550</span></span>|  
|<span data-ttu-id="6fc72-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6fc72-106">Keywords</span></span>|<span data-ttu-id="6fc72-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="6fc72-107">WFServices</span></span>|  
|<span data-ttu-id="6fc72-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6fc72-108">Level</span></span>|<span data-ttu-id="6fc72-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="6fc72-109">Information</span></span>|  
|<span data-ttu-id="6fc72-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6fc72-110">Channel</span></span>|<span data-ttu-id="6fc72-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6fc72-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6fc72-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6fc72-112">Description</span></span>  
 <span data-ttu-id="6fc72-113">Označuje, že vyrovnávací pamětí příjmu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6fc72-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="6fc72-114">Operaci se pokusí znovu po připravený na zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="6fc72-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6fc72-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6fc72-115">Message</span></span>  
 <span data-ttu-id="6fc72-116">Operaci '%1' nelze v tuto chvíli provést.</span><span class="sxs-lookup"><span data-stu-id="6fc72-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="6fc72-117">Další pokus bude provádět, pokud je připraven ke zpracování této konkrétní operace v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="6fc72-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6fc72-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6fc72-118">Details</span></span>  
  
|<span data-ttu-id="6fc72-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6fc72-119">Data Item Name</span></span>|<span data-ttu-id="6fc72-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="6fc72-120">Data Item Type</span></span>|<span data-ttu-id="6fc72-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6fc72-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6fc72-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="6fc72-122">OperationName</span></span>|<span data-ttu-id="6fc72-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fc72-123">xs:string</span></span>|<span data-ttu-id="6fc72-124">Název operace.</span><span class="sxs-lookup"><span data-stu-id="6fc72-124">The name of the operation.</span></span>|  
|<span data-ttu-id="6fc72-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6fc72-125">AppDomain</span></span>|<span data-ttu-id="6fc72-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fc72-126">xs:string</span></span>|<span data-ttu-id="6fc72-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6fc72-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
