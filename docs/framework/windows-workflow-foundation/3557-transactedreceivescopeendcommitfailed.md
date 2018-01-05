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
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="e284f-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="e284f-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="e284f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e284f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e284f-104">ID</span><span class="sxs-lookup"><span data-stu-id="e284f-104">ID</span></span>|<span data-ttu-id="e284f-105">3557</span><span class="sxs-lookup"><span data-stu-id="e284f-105">3557</span></span>|  
|<span data-ttu-id="e284f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e284f-106">Keywords</span></span>|<span data-ttu-id="e284f-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e284f-107">WFServices</span></span>|  
|<span data-ttu-id="e284f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e284f-108">Level</span></span>|<span data-ttu-id="e284f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e284f-109">Information</span></span>|  
|<span data-ttu-id="e284f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e284f-110">Channel</span></span>|<span data-ttu-id="e284f-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="e284f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e284f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e284f-112">Description</span></span>  
 <span data-ttu-id="e284f-113">Označuje, že volání EndCommit na CommittableTransaction došlo TransactionException –.</span><span class="sxs-lookup"><span data-stu-id="e284f-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e284f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e284f-114">Message</span></span>  
 <span data-ttu-id="e284f-115">Volání EndCommit na CommittableTransaction s id = "%1" způsobila TransactionException – s následující zprávou: '%2'.</span><span class="sxs-lookup"><span data-stu-id="e284f-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e284f-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e284f-116">Details</span></span>  
  
|<span data-ttu-id="e284f-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e284f-117">Data Item Name</span></span>|<span data-ttu-id="e284f-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e284f-118">Data Item Type</span></span>|<span data-ttu-id="e284f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e284f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e284f-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="e284f-120">TransactionId</span></span>|<span data-ttu-id="e284f-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e284f-121">xs:string</span></span>|<span data-ttu-id="e284f-122">Id CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="e284f-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="e284f-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="e284f-123">Exception</span></span>|<span data-ttu-id="e284f-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e284f-124">xs:string</span></span>|<span data-ttu-id="e284f-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="e284f-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="e284f-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e284f-126">AppDomain</span></span>|<span data-ttu-id="e284f-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="e284f-127">xs:string</span></span>|<span data-ttu-id="e284f-128">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e284f-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
