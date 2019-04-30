---
title: 4202 – StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774371"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="8806d-102">4202 – StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="8806d-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="8806d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8806d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8806d-104">ID</span><span class="sxs-lookup"><span data-stu-id="8806d-104">ID</span></span>|<span data-ttu-id="8806d-105">4202</span><span class="sxs-lookup"><span data-stu-id="8806d-105">4202</span></span>|  
|<span data-ttu-id="8806d-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8806d-106">Keywords</span></span>|<span data-ttu-id="8806d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="8806d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8806d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8806d-108">Level</span></span>|<span data-ttu-id="8806d-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8806d-109">Verbose</span></span>|  
|<span data-ttu-id="8806d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8806d-110">Channel</span></span>|<span data-ttu-id="8806d-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="8806d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8806d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8806d-112">Description</span></span>  
 <span data-ttu-id="8806d-113">Označuje, že se zpracovává příkaz SQL.</span><span class="sxs-lookup"><span data-stu-id="8806d-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8806d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8806d-114">Message</span></span>  
 <span data-ttu-id="8806d-115">Spuštění příkazu SQL: %1</span><span class="sxs-lookup"><span data-stu-id="8806d-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="8806d-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8806d-116">Details</span></span>  
  
|<span data-ttu-id="8806d-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8806d-117">Data Item Name</span></span>|<span data-ttu-id="8806d-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="8806d-118">Data Item Type</span></span>|<span data-ttu-id="8806d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8806d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8806d-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="8806d-120">SqlCommand</span></span>|<span data-ttu-id="8806d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8806d-121">xs:string</span></span>|<span data-ttu-id="8806d-122">Příkaz SQL, který se spustil.</span><span class="sxs-lookup"><span data-stu-id="8806d-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="8806d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8806d-123">AppDomain</span></span>|<span data-ttu-id="8806d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8806d-124">xs:string</span></span>|<span data-ttu-id="8806d-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8806d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
