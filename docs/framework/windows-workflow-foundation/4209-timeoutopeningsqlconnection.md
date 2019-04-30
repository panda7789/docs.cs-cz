---
title: 4209 – TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774267"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="c513b-102">4209 – TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="c513b-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="c513b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c513b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c513b-104">ID</span><span class="sxs-lookup"><span data-stu-id="c513b-104">ID</span></span>|<span data-ttu-id="c513b-105">4209</span><span class="sxs-lookup"><span data-stu-id="c513b-105">4209</span></span>|  
|<span data-ttu-id="c513b-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c513b-106">Keywords</span></span>|<span data-ttu-id="c513b-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c513b-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c513b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="c513b-108">Level</span></span>|<span data-ttu-id="c513b-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="c513b-109">Error</span></span>|  
|<span data-ttu-id="c513b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="c513b-110">Channel</span></span>|<span data-ttu-id="c513b-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="c513b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c513b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c513b-112">Description</span></span>  
 <span data-ttu-id="c513b-113">Označuje, že při pokusu o otevření připojení SQL došlo k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="c513b-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c513b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c513b-114">Message</span></span>  
 <span data-ttu-id="c513b-115">Časový limit pokusu o otevření připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="c513b-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="c513b-116">Operace nebyla dokončena ve vyhrazeném časovém intervalu %1.</span><span class="sxs-lookup"><span data-stu-id="c513b-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="c513b-117">Čas přidělený této operaci pravděpodobně částí delšího časového limitu.</span><span class="sxs-lookup"><span data-stu-id="c513b-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c513b-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c513b-118">Details</span></span>  
  
|<span data-ttu-id="c513b-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="c513b-119">Data Item Name</span></span>|<span data-ttu-id="c513b-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="c513b-120">Data Item Type</span></span>|<span data-ttu-id="c513b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c513b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c513b-122">časový limit</span><span class="sxs-lookup"><span data-stu-id="c513b-122">Timeout</span></span>|<span data-ttu-id="c513b-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="c513b-123">xs:string</span></span>|<span data-ttu-id="c513b-124">Hodnota časového limitu pro otevření připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="c513b-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="c513b-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c513b-125">AppDomain</span></span>|<span data-ttu-id="c513b-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="c513b-126">xs:string</span></span>|<span data-ttu-id="c513b-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c513b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
