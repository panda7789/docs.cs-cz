---
title: 3551 – BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755529"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="de366-102">3551 – BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="de366-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="de366-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="de366-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de366-104">ID</span><span class="sxs-lookup"><span data-stu-id="de366-104">ID</span></span>|<span data-ttu-id="de366-105">3551</span><span class="sxs-lookup"><span data-stu-id="de366-105">3551</span></span>|  
|<span data-ttu-id="de366-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="de366-106">Keywords</span></span>|<span data-ttu-id="de366-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="de366-107">WFServices</span></span>|  
|<span data-ttu-id="de366-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="de366-108">Level</span></span>|<span data-ttu-id="de366-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="de366-109">Information</span></span>|  
|<span data-ttu-id="de366-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="de366-110">Channel</span></span>|<span data-ttu-id="de366-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="de366-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de366-112">Popis</span><span class="sxs-lookup"><span data-stu-id="de366-112">Description</span></span>  
 <span data-ttu-id="de366-113">Označuje, že záložku obnovení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="de366-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="de366-114">Operace přijetí ve vyrovnávací paměti se znovu pokusí Jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.</span><span class="sxs-lookup"><span data-stu-id="de366-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="de366-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="de366-115">Message</span></span>  
 <span data-ttu-id="de366-116">V tuto chvíli nejde provést operaci "%2" na instanci služby '%1'.</span><span class="sxs-lookup"><span data-stu-id="de366-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="de366-117">Další pokus bude proveden, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.</span><span class="sxs-lookup"><span data-stu-id="de366-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="de366-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="de366-118">Details</span></span>  
  
|<span data-ttu-id="de366-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="de366-119">Data Item Name</span></span>|<span data-ttu-id="de366-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="de366-120">Data Item Type</span></span>|<span data-ttu-id="de366-121">Popis</span><span class="sxs-lookup"><span data-stu-id="de366-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="de366-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="de366-122">OperationName</span></span>|<span data-ttu-id="de366-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="de366-123">xs:string</span></span>|<span data-ttu-id="de366-124">Název operace.</span><span class="sxs-lookup"><span data-stu-id="de366-124">The name of the operation.</span></span>|  
|<span data-ttu-id="de366-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="de366-125">ServiceInstanceId</span></span>|<span data-ttu-id="de366-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="de366-126">xs:string</span></span>|<span data-ttu-id="de366-127">Id instance služby.</span><span class="sxs-lookup"><span data-stu-id="de366-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="de366-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="de366-128">AppDomain</span></span>|<span data-ttu-id="de366-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="de366-129">xs:string</span></span>|<span data-ttu-id="de366-130">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="de366-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
