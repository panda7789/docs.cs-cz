---
title: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
description: Získejte podrobný přehled procesu vývoje a nasazení pro vývoj a nasazování kontejnerových aplikací s využitím Docker a platformy a nástrojů Microsoftu.
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915169"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="e4313-103">Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4313-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Titulní kniha](./media/devops-book-cover-large-we.png)

<span data-ttu-id="e4313-105">**Edice verze 3.1** – aktualizace na ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e4313-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="e4313-106">Tato příručka je obecným přehledem pro vývoj a nasazování kontejnerových ASP.NET Core aplikací pomocí Docker s využitím platformy a nástrojů Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="e4313-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="e4313-107">Příručka obsahuje základní Úvod do Azure DevOps, implementaci kanálů CI/CD a také Azure Container Registry (ACR) a služby Azure Kubernetes Services AKS pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="e4313-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="e4313-108">Podrobnosti o nízké úrovni, které souvisejí s vývojem, najdete v části [mikroslužby .NET: architektura pro kontejnerové aplikace .NET](https://docs.microsoft.com/dotnet/architecture/microservices/) a v referenčních aplikacích [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)souvisejících s odkazem.</span><span class="sxs-lookup"><span data-stu-id="e4313-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="e4313-109">Pošlete nám svůj názor.</span><span class="sxs-lookup"><span data-stu-id="e4313-109">Send us your feedback!</span></span>

<span data-ttu-id="e4313-110">Tento průvodce jsme napsali a pomohli vám pochopit architekturu kontejnerových aplikací a mikroslužeb v .NET.</span><span class="sxs-lookup"><span data-stu-id="e4313-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="e4313-111">Bude vyvíjena příručka a související referenční aplikace, takže jsme Vítejte na vašem názoru.</span><span class="sxs-lookup"><span data-stu-id="e4313-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="e4313-112">Pokud máte komentáře o tom, jak tento průvodce můžete zlepšit, pošlete nám svůj názor na <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="e4313-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="e4313-113">Kredity</span><span class="sxs-lookup"><span data-stu-id="e4313-113">Credits</span></span>

<span data-ttu-id="e4313-114">Autor:</span><span class="sxs-lookup"><span data-stu-id="e4313-114">Author:</span></span>

> <span data-ttu-id="e4313-115">**Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="e4313-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="e4313-116">Editor získání:</span><span class="sxs-lookup"><span data-stu-id="e4313-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="e4313-117">**Janine**</span><span class="sxs-lookup"><span data-stu-id="e4313-117">**Janine Patrick**</span></span>

<span data-ttu-id="e4313-118">Vývojový Editor:</span><span class="sxs-lookup"><span data-stu-id="e4313-118">Developmental Editor:</span></span>

> <span data-ttu-id="e4313-119">**Bob Russell**, Solutions Professional v Microsoftu</span><span class="sxs-lookup"><span data-stu-id="e4313-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="e4313-120">**Osmičkové publikování, Inc.**</span><span class="sxs-lookup"><span data-stu-id="e4313-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="e4313-121">Redakční produkce:</span><span class="sxs-lookup"><span data-stu-id="e4313-121">Editorial Production:</span></span>

> [<span data-ttu-id="e4313-122">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="e4313-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="e4313-123">**Osmičkové publikování, Inc.**</span><span class="sxs-lookup"><span data-stu-id="e4313-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="e4313-124">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="e4313-124">Copyeditor:</span></span>

> <span data-ttu-id="e4313-125">**Bob Russell**, Solutions Professional v Microsoftu</span><span class="sxs-lookup"><span data-stu-id="e4313-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="e4313-126">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="e4313-126">Participants and reviewers:</span></span>

> <span data-ttu-id="e4313-127">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4313-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="e4313-128">**Miguel Veloso**, inženýr pro vývoj softwaru v jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="e4313-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="e4313-129">**Sumit Ghosh**, hlavní konzultant na Neudesic</span><span class="sxs-lookup"><span data-stu-id="e4313-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="e4313-130">Copyright</span><span class="sxs-lookup"><span data-stu-id="e4313-130">Copyright</span></span>

<span data-ttu-id="e4313-131">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="e4313-131">PUBLISHED BY</span></span>

<span data-ttu-id="e4313-132">Microsoft Developer divize, .NET a Visual Studio Product teams</span><span class="sxs-lookup"><span data-stu-id="e4313-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="e4313-133">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4313-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e4313-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e4313-134">One Microsoft Way</span></span>

<span data-ttu-id="e4313-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e4313-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e4313-136">Copyright &copy; 2020 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4313-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="e4313-137">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="e4313-137">All rights reserved.</span></span> <span data-ttu-id="e4313-138">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="e4313-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e4313-139">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="e4313-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="e4313-140">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="e4313-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e4313-141">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="e4313-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e4313-142">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="e4313-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e4313-143">Microsoft a ochranné známky uvedené na <https://www.microsoft.com> webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4313-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e4313-144">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="e4313-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="e4313-145">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e4313-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e4313-146">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="e4313-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="e4313-147">Další</span><span class="sxs-lookup"><span data-stu-id="e4313-147">Next</span></span>](introduction-to-containers-and-docker.md)
