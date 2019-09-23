---
title: ASP.NET Core gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: BUDE URČENO K ZÁPISU
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7d02d7914aed39613b4a41da55515df80abddfe8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184447"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="e4c71-103">ASP.NET Core gRPC pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="e4c71-103">ASP.NET Core gRPC for WCF Developers</span></span>

![titulní obrázek](./media/cover.png)

<span data-ttu-id="e4c71-105">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="e4c71-105">PUBLISHED BY</span></span>

<span data-ttu-id="e4c71-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e4c71-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="e4c71-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4c71-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e4c71-108">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="e4c71-108">One Microsoft Way</span></span>

<span data-ttu-id="e4c71-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e4c71-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e4c71-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4c71-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="e4c71-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="e4c71-111">All rights reserved.</span></span> <span data-ttu-id="e4c71-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="e4c71-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e4c71-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="e4c71-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="e4c71-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="e4c71-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e4c71-115">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="e4c71-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e4c71-116">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="e4c71-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e4c71-117">Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4c71-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e4c71-118">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc. Používá se oprávněním.</span><span class="sxs-lookup"><span data-stu-id="e4c71-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e4c71-119">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="e4c71-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="e4c71-120">Autorizova</span><span class="sxs-lookup"><span data-stu-id="e4c71-120">Author:</span></span>

> <span data-ttu-id="e4c71-121">**Označení Rendle** -ředitel technického důstojníka – [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="e4c71-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="e4c71-122">**Miranda Steiner** – technický autor</span><span class="sxs-lookup"><span data-stu-id="e4c71-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="e4c71-123">Editory</span><span class="sxs-lookup"><span data-stu-id="e4c71-123">Editors:</span></span>

> <span data-ttu-id="e4c71-124">**Maira Wenzel** – vývojář obsahu SR – Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4c71-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="e4c71-125">Úvod</span><span class="sxs-lookup"><span data-stu-id="e4c71-125">Introduction</span></span>

<span data-ttu-id="e4c71-126">TODO</span><span class="sxs-lookup"><span data-stu-id="e4c71-126">TODO</span></span>

## <a name="purpose"></a><span data-ttu-id="e4c71-127">Účel</span><span class="sxs-lookup"><span data-stu-id="e4c71-127">Purpose</span></span>

<span data-ttu-id="e4c71-128">TODO</span><span class="sxs-lookup"><span data-stu-id="e4c71-128">TODO</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="e4c71-129">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="e4c71-129">Who should use this guide</span></span>

<span data-ttu-id="e4c71-130">**AKTUALIZOVAT**</span><span class="sxs-lookup"><span data-stu-id="e4c71-130">**UPDATE THIS**</span></span>

<span data-ttu-id="e4c71-131">Cílovou skupinou pro tento průvodce jsou vývojáři WCF, vedoucí vývoje a architekti, kteří mají zájem o migraci řešení WCF v rozhraní .NET 4 a starších ASP.NET Core 3,0 pomocí služeb gRPC.</span><span class="sxs-lookup"><span data-stu-id="e4c71-131">The audience for this guide is WCF developers, development leads, and architects who are interested in migrating WCF solutions on .NET 4 and earlier to ASP.NET Core 3.0 using gRPC services.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="e4c71-132">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="e4c71-132">How you can use this guide</span></span>

<span data-ttu-id="e4c71-133">**AKTUALIZOVAT**</span><span class="sxs-lookup"><span data-stu-id="e4c71-133">**UPDATE THIS**</span></span>

<span data-ttu-id="e4c71-134">Toto je krátký úvod k sestavování služeb gRPC v ASP.NET Core 3,0 s konkrétní referencí na WCF jako podobnou platformou.</span><span class="sxs-lookup"><span data-stu-id="e4c71-134">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="e4c71-135">Vysvětluje principy gRPC, vztahující se k jednotlivým konceptům ekvivalentních funkcí WCF a poskytuje pokyny pro migraci existující aplikace WCF na gRPC.</span><span class="sxs-lookup"><span data-stu-id="e4c71-135">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="e4c71-136">Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby.</span><span class="sxs-lookup"><span data-stu-id="e4c71-136">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="e4c71-137">Ukázkovou aplikaci lze použít jako šablonu nebo odkaz pro vlastní projekty a vy můžete kopírovat a znovu použít kód z knihy nebo jejích ukázek.</span><span class="sxs-lookup"><span data-stu-id="e4c71-137">The sample application can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="e4c71-138">Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="e4c71-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="e4c71-139">Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.</span><span class="sxs-lookup"><span data-stu-id="e4c71-139">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="e4c71-140">Odkazy</span><span class="sxs-lookup"><span data-stu-id="e4c71-140">References</span></span>

- <span data-ttu-id="e4c71-141">**Web gRPC**</span><span class="sxs-lookup"><span data-stu-id="e4c71-141">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="e4c71-142">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="e4c71-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="e4c71-143">Next</span><span class="sxs-lookup"><span data-stu-id="e4c71-143">Next</span></span>](introduction.md)
