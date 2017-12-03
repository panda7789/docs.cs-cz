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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ea57cc60f9626763308267a98624c825f8312b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="59e12-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="59e12-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="59e12-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="59e12-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59e12-104">ID</span><span class="sxs-lookup"><span data-stu-id="59e12-104">ID</span></span>|<span data-ttu-id="59e12-105">3557</span><span class="sxs-lookup"><span data-stu-id="59e12-105">3557</span></span>|  
|<span data-ttu-id="59e12-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="59e12-106">Keywords</span></span>|<span data-ttu-id="59e12-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="59e12-107">WFServices</span></span>|  
|<span data-ttu-id="59e12-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="59e12-108">Level</span></span>|<span data-ttu-id="59e12-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="59e12-109">Information</span></span>|  
|<span data-ttu-id="59e12-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="59e12-110">Channel</span></span>|<span data-ttu-id="59e12-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="59e12-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="59e12-112">Popis</span><span class="sxs-lookup"><span data-stu-id="59e12-112">Description</span></span>  
 <span data-ttu-id="59e12-113">Označuje, že volání EndCommit na CommittableTransaction došlo TransactionException –.</span><span class="sxs-lookup"><span data-stu-id="59e12-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="59e12-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="59e12-114">Message</span></span>  
 <span data-ttu-id="59e12-115">Volání EndCommit na CommittableTransaction s id = "%1" způsobila TransactionException – s následující zprávou: '%2'.</span><span class="sxs-lookup"><span data-stu-id="59e12-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="59e12-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="59e12-116">Details</span></span>  
  
|<span data-ttu-id="59e12-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="59e12-117">Data Item Name</span></span>|<span data-ttu-id="59e12-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="59e12-118">Data Item Type</span></span>|<span data-ttu-id="59e12-119">Popis</span><span class="sxs-lookup"><span data-stu-id="59e12-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="59e12-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="59e12-120">TransactionId</span></span>|<span data-ttu-id="59e12-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="59e12-121">xs:string</span></span>|<span data-ttu-id="59e12-122">Id CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="59e12-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="59e12-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="59e12-123">Exception</span></span>|<span data-ttu-id="59e12-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="59e12-124">xs:string</span></span>|<span data-ttu-id="59e12-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="59e12-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="59e12-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="59e12-126">AppDomain</span></span>|<span data-ttu-id="59e12-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="59e12-127">xs:string</span></span>|<span data-ttu-id="59e12-128">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="59e12-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
