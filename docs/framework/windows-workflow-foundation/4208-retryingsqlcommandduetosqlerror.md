---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511590"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="852a1-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="852a1-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="852a1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="852a1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="852a1-104">ID</span><span class="sxs-lookup"><span data-stu-id="852a1-104">ID</span></span>|<span data-ttu-id="852a1-105">4208</span><span class="sxs-lookup"><span data-stu-id="852a1-105">4208</span></span>|  
|<span data-ttu-id="852a1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="852a1-106">Keywords</span></span>|<span data-ttu-id="852a1-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="852a1-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="852a1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="852a1-108">Level</span></span>|<span data-ttu-id="852a1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="852a1-109">Information</span></span>|  
|<span data-ttu-id="852a1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="852a1-110">Channel</span></span>|<span data-ttu-id="852a1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="852a1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="852a1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="852a1-112">Description</span></span>  
 <span data-ttu-id="852a1-113">Označuje, že zprostředkovatel SQL je opakováním příkazu SQL z důvodu chyby systému SQL.</span><span class="sxs-lookup"><span data-stu-id="852a1-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="852a1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="852a1-114">Message</span></span>  
 <span data-ttu-id="852a1-115">Opakováním příkazu SQL z důvodu SQL číslo chyby %1.</span><span class="sxs-lookup"><span data-stu-id="852a1-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="852a1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="852a1-116">Details</span></span>  
  
|<span data-ttu-id="852a1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="852a1-117">Data Item Name</span></span>|<span data-ttu-id="852a1-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="852a1-118">Data Item Type</span></span>|<span data-ttu-id="852a1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="852a1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="852a1-120">Argument číslo chyby</span><span class="sxs-lookup"><span data-stu-id="852a1-120">ErrorNumber</span></span>|<span data-ttu-id="852a1-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="852a1-121">xs:string</span></span>|<span data-ttu-id="852a1-122">Číslo chyby SQL.</span><span class="sxs-lookup"><span data-stu-id="852a1-122">The SQL error number.</span></span>|  
|<span data-ttu-id="852a1-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="852a1-123">AppDomain</span></span>|<span data-ttu-id="852a1-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="852a1-124">xs:string</span></span>|<span data-ttu-id="852a1-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="852a1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
