---
title: Architekt cloudových nativních aplikací .NET pro Azure
description: Příručka pro sestavování nativních aplikací cloudu využívajících kontejnery, mikroslužby a funkce bez serveru v Azure.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: ebef97fb355cbf682b37ee441a19fbbfdd2d0dc3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199817"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="cda0e-103">Architekt cloudových nativních aplikací .NET pro Azure</span><span class="sxs-lookup"><span data-stu-id="cda0e-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![titulní obrázek](./media/cover.png)

<span data-ttu-id="cda0e-105">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="cda0e-105">PUBLISHED BY</span></span>

<span data-ttu-id="cda0e-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cda0e-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="cda0e-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="cda0e-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="cda0e-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="cda0e-108">One Microsoft Way</span></span>

<span data-ttu-id="cda0e-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="cda0e-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="cda0e-110">Copyright &copy; 2019 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="cda0e-110">Copyright &copy; 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="cda0e-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="cda0e-111">All rights reserved.</span></span> <span data-ttu-id="cda0e-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="cda0e-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="cda0e-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="cda0e-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="cda0e-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="cda0e-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="cda0e-115">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="cda0e-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="cda0e-116">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="cda0e-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="cda0e-117">Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cda0e-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="cda0e-118">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="cda0e-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="cda0e-119">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cda0e-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="cda0e-120">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="cda0e-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="cda0e-121">Autoři</span><span class="sxs-lookup"><span data-stu-id="cda0e-121">Authors:</span></span>

> <span data-ttu-id="cda0e-122">**Rob Vettor**, hlavní architekt cloudového systému/architekt IP – [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="cda0e-122">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="cda0e-123">**Steve "ardalis" Smith**, software architekt a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="cda0e-123">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="cda0e-124">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="cda0e-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="cda0e-125">**Cesar de la Torre**, Principal program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="cda0e-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="cda0e-126">**Nish Anil**, vedoucí program, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="cda0e-126">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="cda0e-127">**Jeremy Likeness**, vedoucí program, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="cda0e-127">**Jeremy Likeness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="cda0e-128">**Cecil Phillip**, hlavní poradce pro Cloud, Microsoft</span><span class="sxs-lookup"><span data-stu-id="cda0e-128">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="cda0e-129">Další informace o eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="cda0e-129">Learn more about eShopOnContainers</span></span>

<span data-ttu-id="cda0e-130">Editory</span><span class="sxs-lookup"><span data-stu-id="cda0e-130">Editors:</span></span>

> <span data-ttu-id="cda0e-131">**Maira Wenzel**, programový manažer, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="cda0e-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="cda0e-132">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="cda0e-132">Who should use this guide</span></span>

<span data-ttu-id="cda0e-133">Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření aplikací určených pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="cda0e-133">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="cda0e-134">Sekundární cílová skupina je technickým rozhodnutím, které plánuje vybrat, jestli se mají vytvářet aplikace s využitím nativního přístupu v cloudu.</span><span class="sxs-lookup"><span data-stu-id="cda0e-134">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="cda0e-135">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="cda0e-135">How you can use this guide</span></span>

<span data-ttu-id="cda0e-136">Tato příručka začíná definováním cloudového nativního nasazení a představením referenční aplikace vytvořené pomocí cloudových nativních principů a technologií.</span><span class="sxs-lookup"><span data-stu-id="cda0e-136">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="cda0e-137">Kromě těchto prvních dvou kapitol se zbytek knihy rozdělí na konkrétní kapitoly zaměřené na témata, která jsou společná pro většinu cloudových nativních aplikací.</span><span class="sxs-lookup"><span data-stu-id="cda0e-137">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="cda0e-138">Pokud se chcete dozvědět víc o přístupech nativních ke cloudu, můžete přejít na libovolnou z těchto kapitol:</span><span class="sxs-lookup"><span data-stu-id="cda0e-138">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="cda0e-139">Data a přístup k datům</span><span class="sxs-lookup"><span data-stu-id="cda0e-139">Data and data access</span></span>
- <span data-ttu-id="cda0e-140">Vzory komunikace</span><span class="sxs-lookup"><span data-stu-id="cda0e-140">Communication patterns</span></span>
- <span data-ttu-id="cda0e-141">Škálování a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="cda0e-141">Scaling and scalability</span></span>
- <span data-ttu-id="cda0e-142">Odolnost aplikace</span><span class="sxs-lookup"><span data-stu-id="cda0e-142">Application resiliency</span></span>
- <span data-ttu-id="cda0e-143">Monitorování a stav</span><span class="sxs-lookup"><span data-stu-id="cda0e-143">Monitoring and health</span></span>
- <span data-ttu-id="cda0e-144">Identita a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cda0e-144">Identity and security</span></span>
- <span data-ttu-id="cda0e-145">DevOps</span><span class="sxs-lookup"><span data-stu-id="cda0e-145">DevOps</span></span>

<span data-ttu-id="cda0e-146">Tato příručka je k dispozici ve formátu PDF i v online režimu.</span><span class="sxs-lookup"><span data-stu-id="cda0e-146">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="cda0e-147">Nebojte se, že tento dokument předáte nebo odkazuje na jeho online verzi týmu, aby se zajistilo běžné porozumění těmto tématům.</span><span class="sxs-lookup"><span data-stu-id="cda0e-147">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="cda0e-148">Většina těchto témat přináší konzistentní porozumění základním principům a vzorům a kompromisům, které se týkají rozhodnutí souvisejících s těmito tématy.</span><span class="sxs-lookup"><span data-stu-id="cda0e-148">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="cda0e-149">Naším cílem tohoto dokumentu je vybavit týmy a jejich vedoucími informacemi, které potřebují k rozhodování o jejich architektuře, vývoji a hostování svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="cda0e-149">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="cda0e-150">Další</span><span class="sxs-lookup"><span data-stu-id="cda0e-150">Next</span></span>](introduction.md)
