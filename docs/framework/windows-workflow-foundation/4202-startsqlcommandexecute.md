---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510348"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="aaef0-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="aaef0-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="aaef0-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aaef0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aaef0-104">ID</span><span class="sxs-lookup"><span data-stu-id="aaef0-104">ID</span></span>|<span data-ttu-id="aaef0-105">4202</span><span class="sxs-lookup"><span data-stu-id="aaef0-105">4202</span></span>|  
|<span data-ttu-id="aaef0-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="aaef0-106">Keywords</span></span>|<span data-ttu-id="aaef0-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="aaef0-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="aaef0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="aaef0-108">Level</span></span>|<span data-ttu-id="aaef0-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="aaef0-109">Verbose</span></span>|  
|<span data-ttu-id="aaef0-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="aaef0-110">Channel</span></span>|<span data-ttu-id="aaef0-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="aaef0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aaef0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aaef0-112">Description</span></span>  
 <span data-ttu-id="aaef0-113">Označuje, že se spouští příkaz SQL.</span><span class="sxs-lookup"><span data-stu-id="aaef0-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aaef0-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="aaef0-114">Message</span></span>  
 <span data-ttu-id="aaef0-115">Spouštění provedení příkazu SQL: %1</span><span class="sxs-lookup"><span data-stu-id="aaef0-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="aaef0-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aaef0-116">Details</span></span>  
  
|<span data-ttu-id="aaef0-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="aaef0-117">Data Item Name</span></span>|<span data-ttu-id="aaef0-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="aaef0-118">Data Item Type</span></span>|<span data-ttu-id="aaef0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="aaef0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aaef0-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="aaef0-120">SqlCommand</span></span>|<span data-ttu-id="aaef0-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="aaef0-121">xs:string</span></span>|<span data-ttu-id="aaef0-122">Příkaz SQL, která byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="aaef0-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="aaef0-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aaef0-123">AppDomain</span></span>|<span data-ttu-id="aaef0-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="aaef0-124">xs:string</span></span>|<span data-ttu-id="aaef0-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aaef0-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
