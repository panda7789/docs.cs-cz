---
title: 3502 – InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756088"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="50d37-102">3502 – InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="50d37-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="50d37-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="50d37-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50d37-104">ID</span><span class="sxs-lookup"><span data-stu-id="50d37-104">ID</span></span>|<span data-ttu-id="50d37-105">3502</span><span class="sxs-lookup"><span data-stu-id="50d37-105">3502</span></span>|  
|<span data-ttu-id="50d37-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="50d37-106">Keywords</span></span>|<span data-ttu-id="50d37-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="50d37-107">WFServices</span></span>|  
|<span data-ttu-id="50d37-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="50d37-108">Level</span></span>|<span data-ttu-id="50d37-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="50d37-109">Information</span></span>|  
|<span data-ttu-id="50d37-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="50d37-110">Channel</span></span>|<span data-ttu-id="50d37-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="50d37-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="50d37-112">Popis</span><span class="sxs-lookup"><span data-stu-id="50d37-112">Description</span></span>  
 <span data-ttu-id="50d37-113">Označuje, že že OperationDescription byl odvozen od implementace WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="50d37-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="50d37-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="50d37-114">Message</span></span>  
 <span data-ttu-id="50d37-115">Popis OperationDescription s názvem = '%1' v kontraktu "%2" byl odvozen od implementace WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="50d37-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="50d37-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="50d37-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="50d37-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="50d37-117">Details</span></span>  
  
|<span data-ttu-id="50d37-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="50d37-118">Data Item Name</span></span>|<span data-ttu-id="50d37-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="50d37-119">Data Item Type</span></span>|<span data-ttu-id="50d37-120">Popis</span><span class="sxs-lookup"><span data-stu-id="50d37-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="50d37-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="50d37-121">OperationName</span></span>|<span data-ttu-id="50d37-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="50d37-122">xs:string</span></span>|<span data-ttu-id="50d37-123">Název operace.</span><span class="sxs-lookup"><span data-stu-id="50d37-123">The name of the operation.</span></span>|  
|<span data-ttu-id="50d37-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="50d37-124">ContractName</span></span>|<span data-ttu-id="50d37-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="50d37-125">xs:string</span></span>|<span data-ttu-id="50d37-126">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="50d37-126">The name of the contract.</span></span>|  
|<span data-ttu-id="50d37-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="50d37-127">IsOneWay</span></span>|<span data-ttu-id="50d37-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="50d37-128">xs:string</span></span>|<span data-ttu-id="50d37-129">Hodnotu true nebo False určující, pokud kontrakt je jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="50d37-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="50d37-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="50d37-130">AppDomain</span></span>|<span data-ttu-id="50d37-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="50d37-131">xs:string</span></span>|<span data-ttu-id="50d37-132">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="50d37-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
