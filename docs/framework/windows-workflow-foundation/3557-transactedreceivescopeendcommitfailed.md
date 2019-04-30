---
title: 3557 – TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774449"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="8258e-102">3557 – TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="8258e-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="8258e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8258e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8258e-104">ID</span><span class="sxs-lookup"><span data-stu-id="8258e-104">ID</span></span>|<span data-ttu-id="8258e-105">3557</span><span class="sxs-lookup"><span data-stu-id="8258e-105">3557</span></span>|  
|<span data-ttu-id="8258e-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8258e-106">Keywords</span></span>|<span data-ttu-id="8258e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8258e-107">WFServices</span></span>|  
|<span data-ttu-id="8258e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8258e-108">Level</span></span>|<span data-ttu-id="8258e-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="8258e-109">Information</span></span>|  
|<span data-ttu-id="8258e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8258e-110">Channel</span></span>|<span data-ttu-id="8258e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8258e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8258e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8258e-112">Description</span></span>  
 <span data-ttu-id="8258e-113">Označuje, že volání metody endcommit na CommittableTransaction vygenerovalo výjimku TransactionException.</span><span class="sxs-lookup"><span data-stu-id="8258e-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8258e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8258e-114">Message</span></span>  
 <span data-ttu-id="8258e-115">Volání metody EndCommit na třídě CommittableTransaction s id = '%1' vygenerovalo výjimku TransactionException s touto zprávou: '%2'.</span><span class="sxs-lookup"><span data-stu-id="8258e-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8258e-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8258e-116">Details</span></span>  
  
|<span data-ttu-id="8258e-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8258e-117">Data Item Name</span></span>|<span data-ttu-id="8258e-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="8258e-118">Data Item Type</span></span>|<span data-ttu-id="8258e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8258e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8258e-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="8258e-120">TransactionId</span></span>|<span data-ttu-id="8258e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8258e-121">xs:string</span></span>|<span data-ttu-id="8258e-122">Id třídy CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="8258e-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="8258e-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="8258e-123">Exception</span></span>|<span data-ttu-id="8258e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8258e-124">xs:string</span></span>|<span data-ttu-id="8258e-125">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="8258e-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="8258e-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8258e-126">AppDomain</span></span>|<span data-ttu-id="8258e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8258e-127">xs:string</span></span>|<span data-ttu-id="8258e-128">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8258e-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
