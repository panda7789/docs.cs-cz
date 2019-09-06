---
title: Tabulka rozhodnutí Rozhraní .NET Framework, která se mají použít pro Docker
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Tabulka rozhodnutí, rozhraní .NET Framework, které se má použít pro Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296534"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="1d6fd-104">Tabulka rozhodnutí: Rozhraní .NET Framework, která se mají použít pro Docker</span><span class="sxs-lookup"><span data-stu-id="1d6fd-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="1d6fd-105">Následující rozhodovací tabulka shrnuje, jestli se má použít .NET Framework nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d6fd-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="1d6fd-106">Pamatujte na to, že pro kontejnery Linux potřebujete hostitele Docker (virtuální počítače nebo servery) založené na systému Linux a to pro kontejnery Windows, které potřebujete pro hostitele Docker (virtuální počítače nebo servery) založené na Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="1d6fd-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d6fd-107">Ve vývojových počítačích se spustí jeden hostitel Docker, buď Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="1d6fd-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="1d6fd-108">Související mikroslužby, které chcete spustit a testovat společně v jednom řešení, je potřeba spustit na stejné platformě kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1d6fd-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="1d6fd-109"><strong>Architektura/typ aplikace</strong></span><span class="sxs-lookup"><span data-stu-id="1d6fd-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="1d6fd-110"><strong>Kontejnery Linuxu</strong></span><span class="sxs-lookup"><span data-stu-id="1d6fd-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="1d6fd-111"><strong>Kontejnery Windows</strong></span><span class="sxs-lookup"><span data-stu-id="1d6fd-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="1d6fd-112">Mikroslužby na kontejnerech</span><span class="sxs-lookup"><span data-stu-id="1d6fd-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="1d6fd-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-113">.NET Core</span></span></td>
<td><span data-ttu-id="1d6fd-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1d6fd-115">Aplikace monolitické</span><span class="sxs-lookup"><span data-stu-id="1d6fd-115">Monolithic app</span></span></td>
<td><span data-ttu-id="1d6fd-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="1d6fd-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-117">.NET Framework</span></span></p>
<p><span data-ttu-id="1d6fd-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1d6fd-119">Nejlepší výkon a škálovatelnost ve své třídě</span><span class="sxs-lookup"><span data-stu-id="1d6fd-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="1d6fd-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-120">.NET Core</span></span></td>
<td><span data-ttu-id="1d6fd-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1d6fd-122">Migrace do kontejnerů starší verze aplikace ("hnědá-Field") Windows serveru</span><span class="sxs-lookup"><span data-stu-id="1d6fd-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="1d6fd-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1d6fd-124">Nový vývoj založený na kontejneru (zelená-Field)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="1d6fd-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-125">.NET Core</span></span></td>
<td><span data-ttu-id="1d6fd-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1d6fd-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="1d6fd-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="1d6fd-129">.NET Core (doporučeno)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="1d6fd-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1d6fd-131">ASP.NET 4 (MVC 5, webové rozhraní API 2 a webové formuláře)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="1d6fd-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1d6fd-133">Služby Signal</span><span class="sxs-lookup"><span data-stu-id="1d6fd-133">SignalR services</span></span></td>
<td><span data-ttu-id="1d6fd-134">Verze .NET Core 2,1 nebo vyšší</span><span class="sxs-lookup"><span data-stu-id="1d6fd-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="1d6fd-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-135">.NET Framework</span></span></p>
<p><span data-ttu-id="1d6fd-136">Verze .NET Core 2,1 nebo vyšší</span><span class="sxs-lookup"><span data-stu-id="1d6fd-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1d6fd-137">WCF, WF a další starší verze platforem</span><span class="sxs-lookup"><span data-stu-id="1d6fd-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="1d6fd-138">WCF v .NET Core (jenom knihovna klienta WCF)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="1d6fd-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-139">.NET Framework</span></span></p>
<p><span data-ttu-id="1d6fd-140">WCF v .NET Core (jenom knihovna klienta WCF)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1d6fd-141">Spotřeba služeb Azure</span><span class="sxs-lookup"><span data-stu-id="1d6fd-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="1d6fd-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-142">.NET Core</span></span></p>
<p><span data-ttu-id="1d6fd-143">(nakonec všechny služby Azure budou poskytovat klientské sady SDK pro .NET Core)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="1d6fd-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d6fd-144">.NET Framework</span></span></p>
<p><span data-ttu-id="1d6fd-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6fd-145">.NET Core</span></span></p>
<p><span data-ttu-id="1d6fd-146">(nakonec všechny služby Azure budou poskytovat klientské sady SDK pro .NET Core)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="1d6fd-147">[Předchozí](net-framework-container-scenarios.md)Další
>[](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="1d6fd-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
