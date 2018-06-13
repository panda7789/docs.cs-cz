---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512158"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="e9fc0-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="e9fc0-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="e9fc0-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e9fc0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9fc0-104">ID</span><span class="sxs-lookup"><span data-stu-id="e9fc0-104">ID</span></span>|<span data-ttu-id="e9fc0-105">3557</span><span class="sxs-lookup"><span data-stu-id="e9fc0-105">3557</span></span>|  
|<span data-ttu-id="e9fc0-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e9fc0-106">Keywords</span></span>|<span data-ttu-id="e9fc0-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e9fc0-107">WFServices</span></span>|  
|<span data-ttu-id="e9fc0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e9fc0-108">Level</span></span>|<span data-ttu-id="e9fc0-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e9fc0-109">Information</span></span>|  
|<span data-ttu-id="e9fc0-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e9fc0-110">Channel</span></span>|<span data-ttu-id="e9fc0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e9fc0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e9fc0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e9fc0-112">Description</span></span>  
 <span data-ttu-id="e9fc0-113">Označuje, že volání EndCommit na CommittableTransaction došlo TransactionException –.</span><span class="sxs-lookup"><span data-stu-id="e9fc0-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e9fc0-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e9fc0-114">Message</span></span>  
 <span data-ttu-id="e9fc0-115">Volání EndCommit na CommittableTransaction s id = "%1" způsobila TransactionException – s následující zprávou: '%2'.</span><span class="sxs-lookup"><span data-stu-id="e9fc0-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e9fc0-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e9fc0-116">Details</span></span>  
  
|<span data-ttu-id="e9fc0-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e9fc0-117">Data Item Name</span></span>|<span data-ttu-id="e9fc0-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e9fc0-118">Data Item Type</span></span>|<span data-ttu-id="e9fc0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e9fc0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e9fc0-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="e9fc0-120">TransactionId</span></span>|<span data-ttu-id="e9fc0-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9fc0-121">xs:string</span></span>|<span data-ttu-id="e9fc0-122">Id CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="e9fc0-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="e9fc0-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="e9fc0-123">Exception</span></span>|<span data-ttu-id="e9fc0-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9fc0-124">xs:string</span></span>|<span data-ttu-id="e9fc0-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="e9fc0-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="e9fc0-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e9fc0-126">AppDomain</span></span>|<span data-ttu-id="e9fc0-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9fc0-127">xs:string</span></span>|<span data-ttu-id="e9fc0-128">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e9fc0-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
