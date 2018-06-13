---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512002"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="aed2e-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="aed2e-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="aed2e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aed2e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aed2e-104">ID</span><span class="sxs-lookup"><span data-stu-id="aed2e-104">ID</span></span>|<span data-ttu-id="aed2e-105">3502</span><span class="sxs-lookup"><span data-stu-id="aed2e-105">3502</span></span>|  
|<span data-ttu-id="aed2e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="aed2e-106">Keywords</span></span>|<span data-ttu-id="aed2e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="aed2e-107">WFServices</span></span>|  
|<span data-ttu-id="aed2e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="aed2e-108">Level</span></span>|<span data-ttu-id="aed2e-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="aed2e-109">Information</span></span>|  
|<span data-ttu-id="aed2e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="aed2e-110">Channel</span></span>|<span data-ttu-id="aed2e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="aed2e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aed2e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aed2e-112">Description</span></span>  
 <span data-ttu-id="aed2e-113">Označuje, že že OperationDescription byla vyvozena z WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="aed2e-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aed2e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="aed2e-114">Message</span></span>  
 <span data-ttu-id="aed2e-115">OperationDescription s názvem = '%1' ve smlouvě se z WorkflowService odvodit '%2'.</span><span class="sxs-lookup"><span data-stu-id="aed2e-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="aed2e-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="aed2e-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aed2e-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aed2e-117">Details</span></span>  
  
|<span data-ttu-id="aed2e-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="aed2e-118">Data Item Name</span></span>|<span data-ttu-id="aed2e-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="aed2e-119">Data Item Type</span></span>|<span data-ttu-id="aed2e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="aed2e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aed2e-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="aed2e-121">OperationName</span></span>|<span data-ttu-id="aed2e-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="aed2e-122">xs:string</span></span>|<span data-ttu-id="aed2e-123">Název operace.</span><span class="sxs-lookup"><span data-stu-id="aed2e-123">The name of the operation.</span></span>|  
|<span data-ttu-id="aed2e-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="aed2e-124">ContractName</span></span>|<span data-ttu-id="aed2e-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="aed2e-125">xs:string</span></span>|<span data-ttu-id="aed2e-126">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="aed2e-126">The name of the contract.</span></span>|  
|<span data-ttu-id="aed2e-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="aed2e-127">IsOneWay</span></span>|<span data-ttu-id="aed2e-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="aed2e-128">xs:string</span></span>|<span data-ttu-id="aed2e-129">Hodnotu true nebo False indikující, pokud je jednosměrná kontrakt.</span><span class="sxs-lookup"><span data-stu-id="aed2e-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="aed2e-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aed2e-130">AppDomain</span></span>|<span data-ttu-id="aed2e-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="aed2e-131">xs:string</span></span>|<span data-ttu-id="aed2e-132">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aed2e-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
