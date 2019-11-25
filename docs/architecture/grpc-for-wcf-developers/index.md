---
title: ASP.NET Core gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: Úvod k vytváření gRPC Services v ASP.NET Core 3,0 pro vývojáře WCF
ms.date: 09/02/2019
ms.openlocfilehash: 3ef513d2397b6f282591dfe6c9b25cd178372a28
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967751"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="f34b3-103">gRPC ASP.NET Core pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="f34b3-103">ASP.NET Core gRPC for WCF Developers</span></span>

![titulní obrázek](./media/cover.png)

<span data-ttu-id="f34b3-105">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="f34b3-105">PUBLISHED BY</span></span>

<span data-ttu-id="f34b3-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f34b3-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="f34b3-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f34b3-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="f34b3-108">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="f34b3-108">One Microsoft Way</span></span>

<span data-ttu-id="f34b3-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="f34b3-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="f34b3-110">Copyright © 2019 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f34b3-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="f34b3-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="f34b3-111">All rights reserved.</span></span> <span data-ttu-id="f34b3-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="f34b3-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="f34b3-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="f34b3-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="f34b3-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="f34b3-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="f34b3-115">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="f34b3-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="f34b3-116">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="f34b3-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="f34b3-117">Microsoft a ochranné známky uvedené na adrese https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f34b3-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="f34b3-118">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f34b3-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="f34b3-119">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="f34b3-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="f34b3-120">Autorizova</span><span class="sxs-lookup"><span data-stu-id="f34b3-120">Author:</span></span>

> <span data-ttu-id="f34b3-121">**Označení Rendle** -ředitel technického důstojníka – [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="f34b3-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="f34b3-122">**Miranda Steiner** – technický autor</span><span class="sxs-lookup"><span data-stu-id="f34b3-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="f34b3-123">Editory</span><span class="sxs-lookup"><span data-stu-id="f34b3-123">Editors:</span></span>

> <span data-ttu-id="f34b3-124">**Maira Wenzel** – vývojář obsahu SR – Microsoft</span><span class="sxs-lookup"><span data-stu-id="f34b3-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="f34b3-125">Úvod</span><span class="sxs-lookup"><span data-stu-id="f34b3-125">Introduction</span></span>

<span data-ttu-id="f34b3-126">gRPC je moderní architektura pro vytváření síťových služeb a distribuovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="f34b3-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="f34b3-127">Představte si výkon vazeb NetTCP WCF s interoperabilitou pro různé platformy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f34b3-127">Imagine the performance of WCF's NetTCP bindings with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="f34b3-128">gRPC vytváří na HTTP/2 a protokol pro kódování zpráv Protobuf pro zajištění vysokého výkonu a komunikace s malou šířkou pásma mezi aplikacemi a službami.</span><span class="sxs-lookup"><span data-stu-id="f34b3-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="f34b3-129">Podporuje generování kódu serveru a klienta napříč nejoblíbenějšími programovacími jazyky a platformami, včetně .NET, Java, Pythonu, Node. js, C++ a dalších.</span><span class="sxs-lookup"><span data-stu-id="f34b3-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, C++ and more.</span></span> <span data-ttu-id="f34b3-130">Díky špičkové podpoře pro gRPC v ASP.NET Core 3,0 společně s existujícími nástroji gRPC a knihovnami pro .NET 4. x si myslíme, že se jedná o skvělou alternativu ke službě WCF pro vývojové týmy, které chtějí přijmout .NET Core ve svých organizacích.</span><span class="sxs-lookup"><span data-stu-id="f34b3-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, we think it is an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="f34b3-131">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="f34b3-131">Who should use this guide</span></span>

<span data-ttu-id="f34b3-132">Tato příručka je určená pro vývojáře, kteří pracují v .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří chtějí migrovat své aplikace do moderního prostředí RPC pro .NET Core 3,0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="f34b3-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="f34b3-133">Průvodce může být také obecně používán pro vývojáře, kteří upgradují nebo berou v úvahách o upgradu na rozhraní .NET Core 3,0, kteří chtějí používat integrované nástroje gRPC.</span><span class="sxs-lookup"><span data-stu-id="f34b3-133">The guide may also be of use more generally for developers upgrading or considering upgrading to .NET Core 3.0 who want to use the built-in gRPC tools.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="f34b3-134">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="f34b3-134">How you can use this guide</span></span>

<span data-ttu-id="f34b3-135">Toto je krátký úvod k sestavování služeb gRPC v ASP.NET Core 3,0 s konkrétní referencí na WCF jako podobnou platformou.</span><span class="sxs-lookup"><span data-stu-id="f34b3-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="f34b3-136">Vysvětluje principy gRPC, vztahující se k jednotlivým konceptům ekvivalentních funkcí WCF a poskytuje pokyny pro migraci existující aplikace WCF na gRPC.</span><span class="sxs-lookup"><span data-stu-id="f34b3-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="f34b3-137">Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby.</span><span class="sxs-lookup"><span data-stu-id="f34b3-137">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="f34b3-138">Ukázkové aplikace lze použít jako šablonu nebo odkaz pro vlastní projekty a vy můžete kopírovat a znovu použít kód z knihy nebo jejích ukázek.</span><span class="sxs-lookup"><span data-stu-id="f34b3-138">The sample applications can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="f34b3-139">Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f34b3-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="f34b3-140">Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.</span><span class="sxs-lookup"><span data-stu-id="f34b3-140">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="f34b3-141">Odkazy</span><span class="sxs-lookup"><span data-stu-id="f34b3-141">References</span></span>

- <span data-ttu-id="f34b3-142">**Web gRPC**</span><span class="sxs-lookup"><span data-stu-id="f34b3-142">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="f34b3-143">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="f34b3-143">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="f34b3-144">Next</span><span class="sxs-lookup"><span data-stu-id="f34b3-144">Next</span></span>](introduction.md)
