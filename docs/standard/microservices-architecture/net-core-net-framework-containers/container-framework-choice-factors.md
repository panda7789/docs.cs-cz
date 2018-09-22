---
title: Rozhodovací tabulky. Rozhraní .NET Framework pro Docker
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Tabulka rozhodnutí, rozhraní .NET Framework pro Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 74b3749077fdb375f84ddacd98221aa4afcf2f67
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577845"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="96edd-104">Tabulka rozhodnutí: rozhraní .NET Framework pro Docker</span><span class="sxs-lookup"><span data-stu-id="96edd-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="96edd-105">Následující rozhodnutí tabulka shrnuje, jestli chcete používat rozhraní .NET Framework nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96edd-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="96edd-106">Nezapomeňte, že pro kontejnery Linuxu, budete potřebovat hostitele Dockeru založených na Linuxu (virtuální počítače nebo servery) a že pro kontejnery Windows je třeba Windows Server na základě hostitelů Docker (virtuální počítače nebo servery).</span><span class="sxs-lookup"><span data-stu-id="96edd-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96edd-107">Vaše vývojové počítače spustí jednoho hostitele Docker, Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="96edd-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="96edd-108">Související mikroslužeb, kterou chcete spustit a otestovat společně v jednom řešení bude nutné ke spuštění v rámci téže platformy kontejneru.</span><span class="sxs-lookup"><span data-stu-id="96edd-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="96edd-109"><strong>Architektura / typ aplikace</strong></span><span class="sxs-lookup"><span data-stu-id="96edd-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="96edd-110"><strong>Kontejnery Linuxu</strong></span><span class="sxs-lookup"><span data-stu-id="96edd-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="96edd-111"><strong>Kontejnery Windows</strong></span><span class="sxs-lookup"><span data-stu-id="96edd-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="96edd-112">Mikroslužby v kontejnerech</span><span class="sxs-lookup"><span data-stu-id="96edd-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="96edd-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-113">.NET Core</span></span></td>
<td><span data-ttu-id="96edd-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="96edd-115">Monolitické aplikace</span><span class="sxs-lookup"><span data-stu-id="96edd-115">Monolithic app</span></span></td>
<td><span data-ttu-id="96edd-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="96edd-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-117">.NET Framework</span></span></p>
<p><span data-ttu-id="96edd-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="96edd-119">Ve své třídě nejlepší výkon a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="96edd-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="96edd-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-120">.NET Core</span></span></td>
<td><span data-ttu-id="96edd-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="96edd-122">Migrace starších verzí aplikací ("brown – pole") Windows serveru do kontejnerů</span><span class="sxs-lookup"><span data-stu-id="96edd-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="96edd-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="96edd-124">Vývoj nových založených na kontejnerech ("zelená pole")</span><span class="sxs-lookup"><span data-stu-id="96edd-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="96edd-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-125">.NET Core</span></span></td>
<td><span data-ttu-id="96edd-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="96edd-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="96edd-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="96edd-129">.NET core (doporučeno)</span><span class="sxs-lookup"><span data-stu-id="96edd-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="96edd-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="96edd-131">ASP.NET 4 (MVC 5, webové rozhraní API 2 a webové formuláře)</span><span class="sxs-lookup"><span data-stu-id="96edd-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="96edd-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="96edd-133">Služby SignalR</span><span class="sxs-lookup"><span data-stu-id="96edd-133">SignalR services</span></span></td>
<td><span data-ttu-id="96edd-134">.NET core 2.1 nebo vyšší verzi rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="96edd-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="96edd-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-135">.NET Framework</span></span></p>
<p><span data-ttu-id="96edd-136">.NET core 2.1 nebo vyšší verzi rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="96edd-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="96edd-137">WCF, WF a jiné starší verze architektury</span><span class="sxs-lookup"><span data-stu-id="96edd-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="96edd-138">WCF v .NET Core (pouze klientské knihovny WCF)</span><span class="sxs-lookup"><span data-stu-id="96edd-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="96edd-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-139">.NET Framework</span></span></p>
<p><span data-ttu-id="96edd-140">WCF v .NET Core (pouze klientské knihovny WCF)</span><span class="sxs-lookup"><span data-stu-id="96edd-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="96edd-141">Spotřeba služeb Azure</span><span class="sxs-lookup"><span data-stu-id="96edd-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="96edd-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-142">.NET Core</span></span></p>
<p><span data-ttu-id="96edd-143">(případně všech služeb Azure bude poskytovat klientské sady SDK pro .NET Core)</span><span class="sxs-lookup"><span data-stu-id="96edd-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="96edd-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96edd-144">.NET Framework</span></span></p>
<p><span data-ttu-id="96edd-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96edd-145">.NET Core</span></span></p>
<p><span data-ttu-id="96edd-146">(případně všech služeb Azure bude poskytovat klientské sady SDK pro .NET Core)</span><span class="sxs-lookup"><span data-stu-id="96edd-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
<span data-ttu-id="96edd-147">[Předchozí](net-framework-container-scenarios.md)
[další](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="96edd-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
