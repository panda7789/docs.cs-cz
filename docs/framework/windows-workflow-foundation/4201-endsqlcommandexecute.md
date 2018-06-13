---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510218"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="f6c87-102">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="f6c87-102">4201 - EndSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="f6c87-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f6c87-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6c87-104">ID</span><span class="sxs-lookup"><span data-stu-id="f6c87-104">ID</span></span>|<span data-ttu-id="f6c87-105">4201</span><span class="sxs-lookup"><span data-stu-id="f6c87-105">4201</span></span>|  
|<span data-ttu-id="f6c87-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f6c87-106">Keywords</span></span>|<span data-ttu-id="f6c87-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f6c87-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f6c87-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f6c87-108">Level</span></span>|<span data-ttu-id="f6c87-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="f6c87-109">Verbose</span></span>|  
|<span data-ttu-id="f6c87-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f6c87-110">Channel</span></span>|<span data-ttu-id="f6c87-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="f6c87-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6c87-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f6c87-112">Description</span></span>  
 <span data-ttu-id="f6c87-113">Označuje, že příkaz SQL byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="f6c87-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6c87-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f6c87-114">Message</span></span>  
 <span data-ttu-id="f6c87-115">Ukončení provedení příkazu SQL: %1</span><span class="sxs-lookup"><span data-stu-id="f6c87-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6c87-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f6c87-116">Details</span></span>  
  
|<span data-ttu-id="f6c87-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f6c87-117">Data Item Name</span></span>|<span data-ttu-id="f6c87-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="f6c87-118">Data Item Type</span></span>|<span data-ttu-id="f6c87-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f6c87-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6c87-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="f6c87-120">SqlCommand</span></span>|<span data-ttu-id="f6c87-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="f6c87-121">xs:string</span></span>|<span data-ttu-id="f6c87-122">Příkaz SQL, která byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f6c87-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="f6c87-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f6c87-123">AppDomain</span></span>|<span data-ttu-id="f6c87-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="f6c87-124">xs:string</span></span>|<span data-ttu-id="f6c87-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f6c87-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
