---
title: 4201 – EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774358"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="5e6a5-102">4201 – EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="5e6a5-102">4201 - EndSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="5e6a5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5e6a5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e6a5-104">ID</span><span class="sxs-lookup"><span data-stu-id="5e6a5-104">ID</span></span>|<span data-ttu-id="5e6a5-105">4201</span><span class="sxs-lookup"><span data-stu-id="5e6a5-105">4201</span></span>|  
|<span data-ttu-id="5e6a5-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5e6a5-106">Keywords</span></span>|<span data-ttu-id="5e6a5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5e6a5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5e6a5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5e6a5-108">Level</span></span>|<span data-ttu-id="5e6a5-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5e6a5-109">Verbose</span></span>|  
|<span data-ttu-id="5e6a5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5e6a5-110">Channel</span></span>|<span data-ttu-id="5e6a5-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="5e6a5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5e6a5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5e6a5-112">Description</span></span>  
 <span data-ttu-id="5e6a5-113">Označuje, že příkaz SQL byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="5e6a5-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5e6a5-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5e6a5-114">Message</span></span>  
 <span data-ttu-id="5e6a5-115">Ukončení příkazu SQL: %1</span><span class="sxs-lookup"><span data-stu-id="5e6a5-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="5e6a5-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5e6a5-116">Details</span></span>  
  
|<span data-ttu-id="5e6a5-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5e6a5-117">Data Item Name</span></span>|<span data-ttu-id="5e6a5-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="5e6a5-118">Data Item Type</span></span>|<span data-ttu-id="5e6a5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5e6a5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5e6a5-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="5e6a5-120">SqlCommand</span></span>|<span data-ttu-id="5e6a5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5e6a5-121">xs:string</span></span>|<span data-ttu-id="5e6a5-122">Příkaz SQL, který se spustil.</span><span class="sxs-lookup"><span data-stu-id="5e6a5-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="5e6a5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5e6a5-123">AppDomain</span></span>|<span data-ttu-id="5e6a5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5e6a5-124">xs:string</span></span>|<span data-ttu-id="5e6a5-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5e6a5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
