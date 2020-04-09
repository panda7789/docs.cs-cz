---
title: Navrhování cloudových nativních aplikací .NET pro Azure
description: Průvodce pro vytváření cloudnativních aplikací využívajících kontejnery, mikroslužby a funkce Bez serveru Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: cf3be07f0d37aacf4f0252ef2f4d922b7be93eee
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989061"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="b5c02-103">Navrhování cloudových nativních aplikací .NET pro Azure</span><span class="sxs-lookup"><span data-stu-id="b5c02-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![obrázek obálky](./media/cover.png)

<span data-ttu-id="b5c02-105">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="b5c02-105">PUBLISHED BY</span></span>

<span data-ttu-id="b5c02-106">Produktové týmy Microsoft Developer Division, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b5c02-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="b5c02-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="b5c02-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="b5c02-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="b5c02-108">One Microsoft Way</span></span>

<span data-ttu-id="b5c02-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="b5c02-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="b5c02-110">Copyright &copy; 2019 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="b5c02-110">Copyright &copy; 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="b5c02-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b5c02-111">All rights reserved.</span></span> <span data-ttu-id="b5c02-112">Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="b5c02-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="b5c02-113">Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora.</span><span class="sxs-lookup"><span data-stu-id="b5c02-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="b5c02-114">Názory, názory a informace vyjádřené v této knize, včetně url a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="b5c02-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="b5c02-115">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="b5c02-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="b5c02-116">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="b5c02-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="b5c02-117">Společnost Microsoft a ochranné https://www.microsoft.com známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b5c02-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="b5c02-118">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="b5c02-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="b5c02-119">Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.</span><span class="sxs-lookup"><span data-stu-id="b5c02-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="b5c02-120">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="b5c02-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="b5c02-121">Autoři:</span><span class="sxs-lookup"><span data-stu-id="b5c02-121">Authors:</span></span>

> <span data-ttu-id="b5c02-122">**Steve "ardalis" Smith** - softwarový architekt a trenér - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="b5c02-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="b5c02-123">**Rob Vettor** - Microsoft - hlavní architekt cloudového systému / ARCHITEKT IP - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)</span><span class="sxs-lookup"><span data-stu-id="b5c02-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)</span></span>

<span data-ttu-id="b5c02-124">Účastníci a recenzenti:</span><span class="sxs-lookup"><span data-stu-id="b5c02-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="b5c02-125">**Cesar De la Torre**, hlavní programový manažer, .NET tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5c02-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="b5c02-126">**Nish Anil**, Sr. Program Manager, .NET tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5c02-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="b5c02-127">Editory:</span><span class="sxs-lookup"><span data-stu-id="b5c02-127">Editors:</span></span>

> <span data-ttu-id="b5c02-128">**Maira Wenzel**, Sr. Content Developer, .NET tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5c02-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="b5c02-129">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="b5c02-129">Who should use this guide</span></span>

<span data-ttu-id="b5c02-130">Okruhy uživatelů tohoto průvodce jsou především vývojáři, vedoucí vývoje a architekti, kteří se zajímají o to, jak vytvářet aplikace navržené pro cloud.</span><span class="sxs-lookup"><span data-stu-id="b5c02-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="b5c02-131">Sekundární publikum je technická rozhodnutí, kteří plánují zvolit, zda mají vytvářet své aplikace pomocí přístupu nativního pro cloud.</span><span class="sxs-lookup"><span data-stu-id="b5c02-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="b5c02-132">Jak můžete tuto příručku používat</span><span class="sxs-lookup"><span data-stu-id="b5c02-132">How you can use this guide</span></span>

<span data-ttu-id="b5c02-133">Tato příručka začíná definováním cloudnativní a zavedení referenční aplikace vytvořené pomocí zásad a technologií nativní pro cloud.</span><span class="sxs-lookup"><span data-stu-id="b5c02-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="b5c02-134">Kromě těchto prvních dvou kapitol je zbytek knihy rozdělen na konkrétní kapitoly zaměřené na témata společná pro většinu aplikací nativních pro cloud.</span><span class="sxs-lookup"><span data-stu-id="b5c02-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="b5c02-135">Můžete přejít na některou z těchto kapitol a dozvědět se o přístupech nativních pro cloud:</span><span class="sxs-lookup"><span data-stu-id="b5c02-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="b5c02-136">Přístup k datům a datům</span><span class="sxs-lookup"><span data-stu-id="b5c02-136">Data and data access</span></span>
- <span data-ttu-id="b5c02-137">Vzory komunikace</span><span class="sxs-lookup"><span data-stu-id="b5c02-137">Communication patterns</span></span>
- <span data-ttu-id="b5c02-138">Škálování a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="b5c02-138">Scaling and scalability</span></span>
- <span data-ttu-id="b5c02-139">Odolnost aplikace</span><span class="sxs-lookup"><span data-stu-id="b5c02-139">Application resiliency</span></span>
- <span data-ttu-id="b5c02-140">Monitorování a stav</span><span class="sxs-lookup"><span data-stu-id="b5c02-140">Monitoring and health</span></span>
- <span data-ttu-id="b5c02-141">Identita a bezpečnost</span><span class="sxs-lookup"><span data-stu-id="b5c02-141">Identity and security</span></span>
- <span data-ttu-id="b5c02-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="b5c02-142">DevOps</span></span>

<span data-ttu-id="b5c02-143">Tato příručka je k dispozici jak ve formátu PDF, tak online.</span><span class="sxs-lookup"><span data-stu-id="b5c02-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="b5c02-144">Neváhejte a předat tento dokument nebo odkazy na jeho online verzi svému týmu, abyste zajistili společné porozumění těmto tématům.</span><span class="sxs-lookup"><span data-stu-id="b5c02-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="b5c02-145">Většina těchto témat těží z důsledného porozumění základním zásadám a vzorcům, jakož i kompromisům spojeným s rozhodnutími týkajícími se těchto témat.</span><span class="sxs-lookup"><span data-stu-id="b5c02-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="b5c02-146">Naším cílem s tímto dokumentem je vybavit týmy a jejich vedoucí informace, které potřebují k tomu, aby se mohli informovaně rozhodovat o architektuře, vývoji a hostování svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="b5c02-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="b5c02-147">Další</span><span class="sxs-lookup"><span data-stu-id="b5c02-147">Next</span></span>](introduction.md)
