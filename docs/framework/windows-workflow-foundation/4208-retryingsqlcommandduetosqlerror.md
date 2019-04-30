---
title: 4208 – RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774293"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="c9800-102">4208 – RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="c9800-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="c9800-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9800-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9800-104">ID</span><span class="sxs-lookup"><span data-stu-id="c9800-104">ID</span></span>|<span data-ttu-id="c9800-105">4208</span><span class="sxs-lookup"><span data-stu-id="c9800-105">4208</span></span>|  
|<span data-ttu-id="c9800-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c9800-106">Keywords</span></span>|<span data-ttu-id="c9800-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c9800-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c9800-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="c9800-108">Level</span></span>|<span data-ttu-id="c9800-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="c9800-109">Information</span></span>|  
|<span data-ttu-id="c9800-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="c9800-110">Channel</span></span>|<span data-ttu-id="c9800-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="c9800-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9800-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c9800-112">Description</span></span>  
 <span data-ttu-id="c9800-113">Označuje, že zprostředkovatel SQL je opakováním příkazu SQL kvůli chybě SQL.</span><span class="sxs-lookup"><span data-stu-id="c9800-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9800-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c9800-114">Message</span></span>  
 <span data-ttu-id="c9800-115">Opakováním příkazu SQL kvůli chybě SQL s číslem %1.</span><span class="sxs-lookup"><span data-stu-id="c9800-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9800-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c9800-116">Details</span></span>  
  
|<span data-ttu-id="c9800-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="c9800-117">Data Item Name</span></span>|<span data-ttu-id="c9800-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="c9800-118">Data Item Type</span></span>|<span data-ttu-id="c9800-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c9800-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9800-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="c9800-120">ErrorNumber</span></span>|<span data-ttu-id="c9800-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9800-121">xs:string</span></span>|<span data-ttu-id="c9800-122">Číslo chyby SQL.</span><span class="sxs-lookup"><span data-stu-id="c9800-122">The SQL error number.</span></span>|  
|<span data-ttu-id="c9800-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9800-123">AppDomain</span></span>|<span data-ttu-id="c9800-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9800-124">xs:string</span></span>|<span data-ttu-id="c9800-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c9800-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
