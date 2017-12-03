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
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="fbfc8-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="fbfc8-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="fbfc8-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fbfc8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fbfc8-104">ID</span><span class="sxs-lookup"><span data-stu-id="fbfc8-104">ID</span></span>|<span data-ttu-id="fbfc8-105">4208</span><span class="sxs-lookup"><span data-stu-id="fbfc8-105">4208</span></span>|  
|<span data-ttu-id="fbfc8-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fbfc8-106">Keywords</span></span>|<span data-ttu-id="fbfc8-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="fbfc8-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="fbfc8-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="fbfc8-108">Level</span></span>|<span data-ttu-id="fbfc8-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="fbfc8-109">Information</span></span>|  
|<span data-ttu-id="fbfc8-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="fbfc8-110">Channel</span></span>|<span data-ttu-id="fbfc8-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="fbfc8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fbfc8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fbfc8-112">Description</span></span>  
 <span data-ttu-id="fbfc8-113">Označuje, že zprostředkovatel SQL je opakováním příkazu SQL z důvodu chyby systému SQL.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fbfc8-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="fbfc8-114">Message</span></span>  
 <span data-ttu-id="fbfc8-115">Opakováním příkazu SQL z důvodu SQL číslo chyby %1.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fbfc8-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fbfc8-116">Details</span></span>  
  
|<span data-ttu-id="fbfc8-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="fbfc8-117">Data Item Name</span></span>|<span data-ttu-id="fbfc8-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="fbfc8-118">Data Item Type</span></span>|<span data-ttu-id="fbfc8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fbfc8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fbfc8-120">Argument číslo chyby</span><span class="sxs-lookup"><span data-stu-id="fbfc8-120">ErrorNumber</span></span>|<span data-ttu-id="fbfc8-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="fbfc8-121">xs:string</span></span>|<span data-ttu-id="fbfc8-122">Číslo chyby SQL.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-122">The SQL error number.</span></span>|  
|<span data-ttu-id="fbfc8-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="fbfc8-123">AppDomain</span></span>|<span data-ttu-id="fbfc8-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="fbfc8-124">xs:string</span></span>|<span data-ttu-id="fbfc8-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
