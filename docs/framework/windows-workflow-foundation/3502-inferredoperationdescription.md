---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="76ab1-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="76ab1-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="76ab1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="76ab1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76ab1-104">ID</span><span class="sxs-lookup"><span data-stu-id="76ab1-104">ID</span></span>|<span data-ttu-id="76ab1-105">3502</span><span class="sxs-lookup"><span data-stu-id="76ab1-105">3502</span></span>|  
|<span data-ttu-id="76ab1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="76ab1-106">Keywords</span></span>|<span data-ttu-id="76ab1-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="76ab1-107">WFServices</span></span>|  
|<span data-ttu-id="76ab1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="76ab1-108">Level</span></span>|<span data-ttu-id="76ab1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="76ab1-109">Information</span></span>|  
|<span data-ttu-id="76ab1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="76ab1-110">Channel</span></span>|<span data-ttu-id="76ab1-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="76ab1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="76ab1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="76ab1-112">Description</span></span>  
 <span data-ttu-id="76ab1-113">Označuje, že že OperationDescription byla vyvozena z WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="76ab1-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="76ab1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="76ab1-114">Message</span></span>  
 <span data-ttu-id="76ab1-115">OperationDescription s názvem = '%1' ve smlouvě se z WorkflowService odvodit '%2'.</span><span class="sxs-lookup"><span data-stu-id="76ab1-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="76ab1-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="76ab1-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="76ab1-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="76ab1-117">Details</span></span>  
  
|<span data-ttu-id="76ab1-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="76ab1-118">Data Item Name</span></span>|<span data-ttu-id="76ab1-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="76ab1-119">Data Item Type</span></span>|<span data-ttu-id="76ab1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="76ab1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="76ab1-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="76ab1-121">OperationName</span></span>|<span data-ttu-id="76ab1-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="76ab1-122">xs:string</span></span>|<span data-ttu-id="76ab1-123">Název operace.</span><span class="sxs-lookup"><span data-stu-id="76ab1-123">The name of the operation.</span></span>|  
|<span data-ttu-id="76ab1-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="76ab1-124">ContractName</span></span>|<span data-ttu-id="76ab1-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="76ab1-125">xs:string</span></span>|<span data-ttu-id="76ab1-126">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="76ab1-126">The name of the contract.</span></span>|  
|<span data-ttu-id="76ab1-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="76ab1-127">IsOneWay</span></span>|<span data-ttu-id="76ab1-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="76ab1-128">xs:string</span></span>|<span data-ttu-id="76ab1-129">Hodnotu true nebo False indikující, pokud je jednosměrná kontrakt.</span><span class="sxs-lookup"><span data-stu-id="76ab1-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="76ab1-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="76ab1-130">AppDomain</span></span>|<span data-ttu-id="76ab1-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="76ab1-131">xs:string</span></span>|<span data-ttu-id="76ab1-132">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="76ab1-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
