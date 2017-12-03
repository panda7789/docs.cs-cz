---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="f482e-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="f482e-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="f482e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f482e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f482e-104">ID</span><span class="sxs-lookup"><span data-stu-id="f482e-104">ID</span></span>|<span data-ttu-id="f482e-105">4209</span><span class="sxs-lookup"><span data-stu-id="f482e-105">4209</span></span>|  
|<span data-ttu-id="f482e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f482e-106">Keywords</span></span>|<span data-ttu-id="f482e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f482e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f482e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f482e-108">Level</span></span>|<span data-ttu-id="f482e-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="f482e-109">Error</span></span>|  
|<span data-ttu-id="f482e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f482e-110">Channel</span></span>|<span data-ttu-id="f482e-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="f482e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f482e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f482e-112">Description</span></span>  
 <span data-ttu-id="f482e-113">Označuje, že při pokusu o otevření připojení SQL došlo k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="f482e-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f482e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f482e-114">Message</span></span>  
 <span data-ttu-id="f482e-115">Časový limit pokusu o otevření připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="f482e-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="f482e-116">Operace nebyla dokončena v přiděleném časovém limitu % 1.</span><span class="sxs-lookup"><span data-stu-id="f482e-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="f482e-117">Čas přidělený tato operace mohla být část delší časový limit.</span><span class="sxs-lookup"><span data-stu-id="f482e-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f482e-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f482e-118">Details</span></span>  
  
|<span data-ttu-id="f482e-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f482e-119">Data Item Name</span></span>|<span data-ttu-id="f482e-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="f482e-120">Data Item Type</span></span>|<span data-ttu-id="f482e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f482e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f482e-122">Časový limit</span><span class="sxs-lookup"><span data-stu-id="f482e-122">Timeout</span></span>|<span data-ttu-id="f482e-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="f482e-123">xs:string</span></span>|<span data-ttu-id="f482e-124">Hodnota časového limitu pro otevření připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="f482e-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="f482e-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f482e-125">AppDomain</span></span>|<span data-ttu-id="f482e-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="f482e-126">xs:string</span></span>|<span data-ttu-id="f482e-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f482e-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
