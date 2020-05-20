---
title: Architekt cloudových nativních aplikací .NET pro Azure
description: Příručka pro sestavování nativních aplikací cloudu využívajících kontejnery, mikroslužby a funkce bez serveru v Azure.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: 1607c1bbcc9bbb3c9fe19840a2827aa5ea083728
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613993"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="3fe6c-103">Architekt cloudových nativních aplikací .NET pro Azure</span><span class="sxs-lookup"><span data-stu-id="3fe6c-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![titulní obrázek](./media/cover.png)

<span data-ttu-id="3fe6c-105">**EDICE v. 1.0**</span><span class="sxs-lookup"><span data-stu-id="3fe6c-105">**EDITION v.1.0**</span></span>

<span data-ttu-id="3fe6c-106">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="3fe6c-106">PUBLISHED BY</span></span>

<span data-ttu-id="3fe6c-107">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3fe6c-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="3fe6c-108">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="3fe6c-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="3fe6c-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="3fe6c-109">One Microsoft Way</span></span>

<span data-ttu-id="3fe6c-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="3fe6c-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="3fe6c-111">Copyright &copy; 2020 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="3fe6c-111">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="3fe6c-112">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-112">All rights reserved.</span></span> <span data-ttu-id="3fe6c-113">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="3fe6c-114">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="3fe6c-115">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="3fe6c-116">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="3fe6c-117">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="3fe6c-118">Microsoft a ochranné známky uvedené na https://www.microsoft.com webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="3fe6c-119">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="3fe6c-120">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="3fe6c-121">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="3fe6c-122">Autoři</span><span class="sxs-lookup"><span data-stu-id="3fe6c-122">Authors:</span></span>

> <span data-ttu-id="3fe6c-123">**Rob Vettor**, hlavní architekt cloudového systému/architekt IP – [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe6c-123">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="3fe6c-124">**Steve "ardalis" Smith**, software architekt a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="3fe6c-124">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="3fe6c-125">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="3fe6c-125">Participants and Reviewers:</span></span>

> <span data-ttu-id="3fe6c-126">**Cesar de la Torre**, Principal program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe6c-126">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3fe6c-127">**Nish Anil**, vedoucí program, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe6c-127">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3fe6c-128">**Jeremy Likness**, vedoucí program, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe6c-128">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3fe6c-129">**Cecil Phillip**, hlavní poradce pro Cloud, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe6c-129">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="3fe6c-130">Editory</span><span class="sxs-lookup"><span data-stu-id="3fe6c-130">Editors:</span></span>

> <span data-ttu-id="3fe6c-131">**Maira Wenzel**, programový manažer, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe6c-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="3fe6c-132">Verze</span><span class="sxs-lookup"><span data-stu-id="3fe6c-132">Version</span></span>

<span data-ttu-id="3fe6c-133">Tato příručka se zapsala jako verze **.NET core 3,1** spolu s mnoha dalšími aktualizacemi, které se týkají stejných "Wave" technologií (tj. Azure a dalších technologií třetích stran), které se shodují v čase s verzí .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-133">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="3fe6c-134">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="3fe6c-134">Who should use this guide</span></span>

<span data-ttu-id="3fe6c-135">Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření aplikací určených pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-135">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="3fe6c-136">Sekundární cílová skupina je technickým rozhodnutím, které plánuje vybrat, jestli se mají vytvářet aplikace s využitím nativního přístupu v cloudu.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-136">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="3fe6c-137">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="3fe6c-137">How you can use this guide</span></span>

<span data-ttu-id="3fe6c-138">Tato příručka začíná definováním cloudového nativního nasazení a představením referenční aplikace vytvořené pomocí cloudových nativních principů a technologií.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-138">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="3fe6c-139">Kromě těchto prvních dvou kapitol se zbytek knihy rozdělí na konkrétní kapitoly zaměřené na témata, která jsou společná pro většinu cloudových nativních aplikací.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-139">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="3fe6c-140">Pokud se chcete dozvědět víc o přístupech nativních ke cloudu, můžete přejít na libovolnou z těchto kapitol:</span><span class="sxs-lookup"><span data-stu-id="3fe6c-140">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="3fe6c-141">Data a přístup k datům</span><span class="sxs-lookup"><span data-stu-id="3fe6c-141">Data and data access</span></span>
- <span data-ttu-id="3fe6c-142">Vzory komunikace</span><span class="sxs-lookup"><span data-stu-id="3fe6c-142">Communication patterns</span></span>
- <span data-ttu-id="3fe6c-143">Škálování a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="3fe6c-143">Scaling and scalability</span></span>
- <span data-ttu-id="3fe6c-144">Odolnost aplikace</span><span class="sxs-lookup"><span data-stu-id="3fe6c-144">Application resiliency</span></span>
- <span data-ttu-id="3fe6c-145">Monitorování a stav</span><span class="sxs-lookup"><span data-stu-id="3fe6c-145">Monitoring and health</span></span>
- <span data-ttu-id="3fe6c-146">Identita a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3fe6c-146">Identity and security</span></span>
- <span data-ttu-id="3fe6c-147">DevOps</span><span class="sxs-lookup"><span data-stu-id="3fe6c-147">DevOps</span></span>

<span data-ttu-id="3fe6c-148">Tato příručka je k dispozici ve formátu PDF i v online režimu.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-148">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="3fe6c-149">Nebojte se, že tento dokument předáte nebo odkazuje na jeho online verzi týmu, aby se zajistilo běžné porozumění těmto tématům.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-149">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="3fe6c-150">Většina těchto témat přináší konzistentní porozumění základním principům a vzorům a kompromisům, které se týkají rozhodnutí souvisejících s těmito tématy.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-150">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="3fe6c-151">Naším cílem tohoto dokumentu je vybavit týmy a jejich vedoucími informacemi, které potřebují k rozhodování o jejich architektuře, vývoji a hostování svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="3fe6c-151">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="3fe6c-152">Poslat svůj názor</span><span class="sxs-lookup"><span data-stu-id="3fe6c-152">Send your feedback</span></span>

<span data-ttu-id="3fe6c-153">Tato kniha a související ukázky se neustále vyvíjí, takže se vaše zpětná vazba vítá!</span><span class="sxs-lookup"><span data-stu-id="3fe6c-153">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="3fe6c-154">Pokud máte komentáře k tomu, jak se tato kniha dá zlepšit, použijte část zpětná vazba v dolní části každé stránky založené na [problémech na GitHubu](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="3fe6c-154">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="3fe6c-155">Další</span><span class="sxs-lookup"><span data-stu-id="3fe6c-155">Next</span></span>](introduction.md)
