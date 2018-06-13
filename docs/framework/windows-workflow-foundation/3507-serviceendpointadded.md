---
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: c787a1a5af752a3d08e2049cfa0b600b7739e56c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512057"
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="1a01c-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="1a01c-102">3507 - ServiceEndpointAdded</span></span>
## <a name="properties"></a><span data-ttu-id="1a01c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1a01c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a01c-104">ID</span><span class="sxs-lookup"><span data-stu-id="1a01c-104">ID</span></span>|<span data-ttu-id="1a01c-105">3507</span><span class="sxs-lookup"><span data-stu-id="1a01c-105">3507</span></span>|  
|<span data-ttu-id="1a01c-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1a01c-106">Keywords</span></span>|<span data-ttu-id="1a01c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1a01c-107">WFServices</span></span>|  
|<span data-ttu-id="1a01c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1a01c-108">Level</span></span>|<span data-ttu-id="1a01c-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="1a01c-109">Information</span></span>|  
|<span data-ttu-id="1a01c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1a01c-110">Channel</span></span>|<span data-ttu-id="1a01c-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1a01c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1a01c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1a01c-112">Description</span></span>  
 <span data-ttu-id="1a01c-113">Označuje, že byl přidán koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="1a01c-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1a01c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1a01c-114">Message</span></span>  
 <span data-ttu-id="1a01c-115">Koncový bod služby byla přidána ke adresu '%1', vazby: %2' a kontrakt '%3'.</span><span class="sxs-lookup"><span data-stu-id="1a01c-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1a01c-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1a01c-116">Details</span></span>  
  
|<span data-ttu-id="1a01c-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1a01c-117">Data Item Name</span></span>|<span data-ttu-id="1a01c-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1a01c-118">Data Item Type</span></span>|<span data-ttu-id="1a01c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1a01c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1a01c-120">Adresa</span><span class="sxs-lookup"><span data-stu-id="1a01c-120">Address</span></span>|<span data-ttu-id="1a01c-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="1a01c-121">xs:string</span></span>|<span data-ttu-id="1a01c-122">Adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1a01c-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="1a01c-123">Vazba</span><span class="sxs-lookup"><span data-stu-id="1a01c-123">Binding</span></span>|<span data-ttu-id="1a01c-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="1a01c-124">xs:string</span></span>|<span data-ttu-id="1a01c-125">Vazba koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1a01c-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="1a01c-126">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="1a01c-126">Contract</span></span>|<span data-ttu-id="1a01c-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="1a01c-127">xs:string</span></span>|<span data-ttu-id="1a01c-128">Kontrakt koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1a01c-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="1a01c-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1a01c-129">AppDomain</span></span>|<span data-ttu-id="1a01c-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="1a01c-130">xs:string</span></span>|<span data-ttu-id="1a01c-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1a01c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
