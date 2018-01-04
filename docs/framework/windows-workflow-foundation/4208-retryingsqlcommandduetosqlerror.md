---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51374a25ee11b3344e950670cc7882db42d39779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="1badf-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="1badf-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="1badf-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1badf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1badf-104">ID</span><span class="sxs-lookup"><span data-stu-id="1badf-104">ID</span></span>|<span data-ttu-id="1badf-105">4208</span><span class="sxs-lookup"><span data-stu-id="1badf-105">4208</span></span>|  
|<span data-ttu-id="1badf-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1badf-106">Keywords</span></span>|<span data-ttu-id="1badf-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="1badf-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="1badf-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1badf-108">Level</span></span>|<span data-ttu-id="1badf-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="1badf-109">Information</span></span>|  
|<span data-ttu-id="1badf-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1badf-110">Channel</span></span>|<span data-ttu-id="1badf-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="1badf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1badf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1badf-112">Description</span></span>  
 <span data-ttu-id="1badf-113">Označuje, že zprostředkovatel SQL je opakováním příkazu SQL z důvodu chyby systému SQL.</span><span class="sxs-lookup"><span data-stu-id="1badf-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1badf-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1badf-114">Message</span></span>  
 <span data-ttu-id="1badf-115">Opakováním příkazu SQL z důvodu SQL číslo chyby %1.</span><span class="sxs-lookup"><span data-stu-id="1badf-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1badf-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1badf-116">Details</span></span>  
  
|<span data-ttu-id="1badf-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1badf-117">Data Item Name</span></span>|<span data-ttu-id="1badf-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1badf-118">Data Item Type</span></span>|<span data-ttu-id="1badf-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1badf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1badf-120">Argument číslo chyby</span><span class="sxs-lookup"><span data-stu-id="1badf-120">ErrorNumber</span></span>|<span data-ttu-id="1badf-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="1badf-121">xs:string</span></span>|<span data-ttu-id="1badf-122">Číslo chyby SQL.</span><span class="sxs-lookup"><span data-stu-id="1badf-122">The SQL error number.</span></span>|  
|<span data-ttu-id="1badf-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1badf-123">AppDomain</span></span>|<span data-ttu-id="1badf-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="1badf-124">xs:string</span></span>|<span data-ttu-id="1badf-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1badf-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
