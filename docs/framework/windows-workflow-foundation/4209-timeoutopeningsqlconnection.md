---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513162"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="ce831-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="ce831-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="ce831-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ce831-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce831-104">ID</span><span class="sxs-lookup"><span data-stu-id="ce831-104">ID</span></span>|<span data-ttu-id="ce831-105">4209</span><span class="sxs-lookup"><span data-stu-id="ce831-105">4209</span></span>|  
|<span data-ttu-id="ce831-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ce831-106">Keywords</span></span>|<span data-ttu-id="ce831-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ce831-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ce831-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ce831-108">Level</span></span>|<span data-ttu-id="ce831-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="ce831-109">Error</span></span>|  
|<span data-ttu-id="ce831-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ce831-110">Channel</span></span>|<span data-ttu-id="ce831-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ce831-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce831-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ce831-112">Description</span></span>  
 <span data-ttu-id="ce831-113">Označuje, že při pokusu o otevření připojení SQL došlo k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="ce831-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce831-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ce831-114">Message</span></span>  
 <span data-ttu-id="ce831-115">Časový limit pokusu o otevření připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="ce831-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="ce831-116">Operace nebyla dokončena v přiděleném časovém limitu % 1.</span><span class="sxs-lookup"><span data-stu-id="ce831-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="ce831-117">Čas přidělený tato operace mohla být část delší časový limit.</span><span class="sxs-lookup"><span data-stu-id="ce831-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce831-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ce831-118">Details</span></span>  
  
|<span data-ttu-id="ce831-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ce831-119">Data Item Name</span></span>|<span data-ttu-id="ce831-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ce831-120">Data Item Type</span></span>|<span data-ttu-id="ce831-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ce831-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce831-122">Časový limit</span><span class="sxs-lookup"><span data-stu-id="ce831-122">Timeout</span></span>|<span data-ttu-id="ce831-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="ce831-123">xs:string</span></span>|<span data-ttu-id="ce831-124">Hodnota časového limitu pro otevření připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="ce831-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="ce831-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ce831-125">AppDomain</span></span>|<span data-ttu-id="ce831-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="ce831-126">xs:string</span></span>|<span data-ttu-id="ce831-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ce831-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
