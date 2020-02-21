---
title: ASP.NET Core gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: Úvod k vytváření gRPC Services v ASP.NET Core 3,0 pro vývojáře WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543232"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="d7576-103">gRPC ASP.NET Core pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="d7576-103">ASP.NET Core gRPC for WCF Developers</span></span>

![titulní obrázek](./media/cover.png)

<span data-ttu-id="d7576-105">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="d7576-105">PUBLISHED BY</span></span>

<span data-ttu-id="d7576-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7576-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="d7576-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d7576-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="d7576-108">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="d7576-108">One Microsoft Way</span></span>

<span data-ttu-id="d7576-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="d7576-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="d7576-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d7576-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="d7576-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="d7576-111">All rights reserved.</span></span> <span data-ttu-id="d7576-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="d7576-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="d7576-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="d7576-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="d7576-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="d7576-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="d7576-115">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="d7576-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="d7576-116">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="d7576-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="d7576-117">Microsoft a ochranné známky uvedené na adrese https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d7576-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="d7576-118">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d7576-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="d7576-119">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="d7576-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="d7576-120">Autoři:</span><span class="sxs-lookup"><span data-stu-id="d7576-120">Authors:</span></span>

> <span data-ttu-id="d7576-121">**Označení Rendle** -ředitel technického důstojníka – [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="d7576-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="d7576-122">**Miranda Steiner** – technický autor</span><span class="sxs-lookup"><span data-stu-id="d7576-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="d7576-123">Redaktor:</span><span class="sxs-lookup"><span data-stu-id="d7576-123">Editor:</span></span>

> <span data-ttu-id="d7576-124">**Maira Wenzel** – SR. Content – vývojář – Microsoft</span><span class="sxs-lookup"><span data-stu-id="d7576-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="d7576-125">Úvod</span><span class="sxs-lookup"><span data-stu-id="d7576-125">Introduction</span></span>

<span data-ttu-id="d7576-126">gRPC je moderní architektura pro vytváření síťových služeb a distribuovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7576-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="d7576-127">Představte si Windows Communication Foundation výkon NetTCPch vazeb WCF (WCF) v kombinaci s interoperabilitou pro různé platformy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7576-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="d7576-128">gRPC vytváří na HTTP/2 a protokol pro kódování zpráv Protobuf pro zajištění vysokého výkonu a komunikace s malou šířkou pásma mezi aplikacemi a službami.</span><span class="sxs-lookup"><span data-stu-id="d7576-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="d7576-129">Podporuje generování kódu serveru a klienta napříč nejoblíbenějšími programovacími jazyky a platformami, jako jsou .NET, Java, Python, Node. js, přejít C++a.</span><span class="sxs-lookup"><span data-stu-id="d7576-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="d7576-130">Díky špičkové podpoře pro gRPC v ASP.NET Core 3,0 společně s existujícími nástroji gRPC a knihovnami pro .NET 4. x je to vynikající alternativou WCF pro vývojové týmy, které chtějí přijmout .NET Core ve svých organizacích.</span><span class="sxs-lookup"><span data-stu-id="d7576-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="d7576-131">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="d7576-131">Who should use this guide</span></span>

<span data-ttu-id="d7576-132">Tato příručka je určená pro vývojáře, kteří pracují v .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří chtějí migrovat své aplikace do moderního prostředí RPC pro .NET Core 3,0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="d7576-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="d7576-133">Obecně platí, že pokud upgradujete nebo zvažujete upgrade, na .NET Core 3,0 a chcete použít integrované nástroje gRPC, je tato příručka také užitečná.</span><span class="sxs-lookup"><span data-stu-id="d7576-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="d7576-134">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="d7576-134">How you can use this guide</span></span>

<span data-ttu-id="d7576-135">Toto je krátký úvod k sestavování služeb gRPC v ASP.NET Core 3,0, se specifickou referencí na WCF jako s obdobnou platformou.</span><span class="sxs-lookup"><span data-stu-id="d7576-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="d7576-136">Vysvětluje principy gRPC, vztahující se k jednotlivým konceptům ekvivalentních funkcí WCF a poskytuje pokyny pro migraci existující aplikace WCF na gRPC.</span><span class="sxs-lookup"><span data-stu-id="d7576-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="d7576-137">Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby.</span><span class="sxs-lookup"><span data-stu-id="d7576-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="d7576-138">Ukázkové aplikace můžete použít jako šablonu nebo odkaz pro vlastní projekty a vy můžete zkopírovat a znovu použít kód z knihy nebo jejích ukázek.</span><span class="sxs-lookup"><span data-stu-id="d7576-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="d7576-139">Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d7576-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="d7576-140">Díky tomu, že všichni pracují se společnou sadou podmínek a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.</span><span class="sxs-lookup"><span data-stu-id="d7576-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="d7576-141">Odkazy</span><span class="sxs-lookup"><span data-stu-id="d7576-141">References</span></span>

- <span data-ttu-id="d7576-142">**Web gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="d7576-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="d7576-143">**Výběr mezi .NET Core a .NET Framework pro serverové aplikace**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="d7576-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d7576-144">Next</span><span class="sxs-lookup"><span data-stu-id="d7576-144">Next</span></span>](introduction.md)
