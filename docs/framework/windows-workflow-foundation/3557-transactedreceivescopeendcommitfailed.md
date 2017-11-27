---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f9f1066f1948411d584a2dee1af2129aa3a103
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="e035e-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="e035e-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="e035e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e035e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e035e-104">ID</span><span class="sxs-lookup"><span data-stu-id="e035e-104">ID</span></span>|<span data-ttu-id="e035e-105">3557</span><span class="sxs-lookup"><span data-stu-id="e035e-105">3557</span></span>|  
|<span data-ttu-id="e035e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e035e-106">Keywords</span></span>|<span data-ttu-id="e035e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e035e-107">WFServices</span></span>|  
|<span data-ttu-id="e035e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e035e-108">Level</span></span>|<span data-ttu-id="e035e-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e035e-109">Information</span></span>|  
|<span data-ttu-id="e035e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e035e-110">Channel</span></span>|<span data-ttu-id="e035e-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="e035e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e035e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e035e-112">Description</span></span>  
 <span data-ttu-id="e035e-113">Označuje, že volání EndCommit na CommittableTransaction došlo TransactionException –.</span><span class="sxs-lookup"><span data-stu-id="e035e-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e035e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e035e-114">Message</span></span>  
 <span data-ttu-id="e035e-115">Volání EndCommit na CommittableTransaction s id = "%1" způsobila TransactionException – s následující zprávou: '%2'.</span><span class="sxs-lookup"><span data-stu-id="e035e-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e035e-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e035e-116">Details</span></span>  
  
|<span data-ttu-id="e035e-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e035e-117">Data Item Name</span></span>|<span data-ttu-id="e035e-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e035e-118">Data Item Type</span></span>|<span data-ttu-id="e035e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e035e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e035e-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="e035e-120">TransactionId</span></span>|<span data-ttu-id="e035e-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e035e-121">xs:string</span></span>|<span data-ttu-id="e035e-122">Id CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="e035e-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="e035e-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="e035e-123">Exception</span></span>|<span data-ttu-id="e035e-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e035e-124">xs:string</span></span>|<span data-ttu-id="e035e-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="e035e-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="e035e-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e035e-126">AppDomain</span></span>|<span data-ttu-id="e035e-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="e035e-127">xs:string</span></span>|<span data-ttu-id="e035e-128">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e035e-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
