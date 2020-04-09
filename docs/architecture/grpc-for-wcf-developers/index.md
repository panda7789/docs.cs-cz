---
title: ASP.NET Core gRPC pro vývojáře WCF - gRPC pro vývojáře WCF
description: Úvod do budování služeb gRPC v ASP.NET Core 3.0 pro vývojáře WCF
ms.date: 09/02/2019
ms.openlocfilehash: 175dfbf1880a0937615543c248fba3bed0e25c23
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988957"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="aa757-103">gRPC ASP.NET Core pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="aa757-103">ASP.NET Core gRPC for WCF Developers</span></span>

![obrázek obálky](./media/cover.png)

<span data-ttu-id="aa757-105">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="aa757-105">PUBLISHED BY</span></span>

<span data-ttu-id="aa757-106">Produktové týmy Microsoft Developer Division, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aa757-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="aa757-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="aa757-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="aa757-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="aa757-108">One Microsoft Way</span></span>

<span data-ttu-id="aa757-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="aa757-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="aa757-110">Autorská práva © 2019 společností Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="aa757-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="aa757-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="aa757-111">All rights reserved.</span></span> <span data-ttu-id="aa757-112">Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="aa757-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="aa757-113">Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora.</span><span class="sxs-lookup"><span data-stu-id="aa757-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="aa757-114">Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="aa757-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="aa757-115">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="aa757-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="aa757-116">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="aa757-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="aa757-117">Společnost Microsoft a ochranné https://www.microsoft.com známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="aa757-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="aa757-118">Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.</span><span class="sxs-lookup"><span data-stu-id="aa757-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="aa757-119">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="aa757-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="aa757-120">Autoři:</span><span class="sxs-lookup"><span data-stu-id="aa757-120">Authors:</span></span>

> <span data-ttu-id="aa757-121">**Mark Rendle** - Technický ředitel - [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="aa757-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="aa757-122">**Miranda Steiner** - Technický autor</span><span class="sxs-lookup"><span data-stu-id="aa757-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="aa757-123">Editor:</span><span class="sxs-lookup"><span data-stu-id="aa757-123">Editor:</span></span>

> <span data-ttu-id="aa757-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span><span class="sxs-lookup"><span data-stu-id="aa757-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="aa757-125">Úvod</span><span class="sxs-lookup"><span data-stu-id="aa757-125">Introduction</span></span>

<span data-ttu-id="aa757-126">gRPC je moderní rámec pro budování síťových služeb a distribuovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="aa757-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="aa757-127">Představte si výkon vazby NetTCP platformy Windows Communication Foundation (WCF) v kombinaci s interoperabilitou soap napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="aa757-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="aa757-128">gRPC staví na PROTOKOLU HTTP/2 a protokolu kódování zpráv Protobuf, který poskytuje vysoce výkonnou komunikaci s malou šířkou pásma mezi aplikacemi a službami.</span><span class="sxs-lookup"><span data-stu-id="aa757-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="aa757-129">Podporuje generování systému serveru a klientského kódu napříč nejoblíbenějšími programovacími jazyky a platformami, včetně .NET, Java, Python, Node.js, Go a C++.</span><span class="sxs-lookup"><span data-stu-id="aa757-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="aa757-130">S prvotřídní podporou gRPC v ASP.NET Core 3.0, spolu se stávajícími gRPC nástroji a knihovnami pro .NET 4.x, je to vynikající alternativa k WCF pro vývojové týmy, které chtějí přijmout .NET Core ve svých organizacích.</span><span class="sxs-lookup"><span data-stu-id="aa757-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="aa757-131">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="aa757-131">Who should use this guide</span></span>

<span data-ttu-id="aa757-132">Tato příručka byla napsána pro vývojáře pracující v rozhraní .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří se snaží migrovat své aplikace do moderního prostředí RPC pro .NET Core 3.0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="aa757-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="aa757-133">Obecněji platí, že pokud upgradujete nebo zvažujete upgrade na .NET Core 3.0 a chcete použít vestavěné nástroje gRPC, je tato příručka také užitečná.</span><span class="sxs-lookup"><span data-stu-id="aa757-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="aa757-134">Jak můžete tuto příručku používat</span><span class="sxs-lookup"><span data-stu-id="aa757-134">How you can use this guide</span></span>

<span data-ttu-id="aa757-135">Toto je krátký úvod do budování gRPC Services v ASP.NET Core 3.0, se zvláštním odkazem na WCF jako analogická platforma.</span><span class="sxs-lookup"><span data-stu-id="aa757-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="aa757-136">Vysvětluje principy gRPC, vztahující se ke každému konceptu ekvivalentních funkcí WCF, a nabízí pokyny pro migraci existující aplikace WCF do gRPC.</span><span class="sxs-lookup"><span data-stu-id="aa757-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="aa757-137">Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby.</span><span class="sxs-lookup"><span data-stu-id="aa757-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="aa757-138">Ukázkové aplikace můžete použít jako šablonu nebo odkaz pro vlastní projekty a můžete zkopírovat a znovu použít kód z knihy nebo jejích ukázek.</span><span class="sxs-lookup"><span data-stu-id="aa757-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="aa757-139">Neváhejte a předat tuto příručku svému týmu, abyste zajistili společné porozumění těmto úvahám a příležitostem.</span><span class="sxs-lookup"><span data-stu-id="aa757-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="aa757-140">Mít všechny, kteří pracují ze společného souboru pojmů a základních principů, pomáhá zajistit konzistentní uplatňování architektonických vzorů a postupů.</span><span class="sxs-lookup"><span data-stu-id="aa757-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="aa757-141">Odkazy</span><span class="sxs-lookup"><span data-stu-id="aa757-141">References</span></span>

- <span data-ttu-id="aa757-142">**webové stránky gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="aa757-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="aa757-143">**Výběr mezi rozhraním .NET Core a rozhraním .NET Framework pro serverové aplikace**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="aa757-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="aa757-144">Další</span><span class="sxs-lookup"><span data-stu-id="aa757-144">Next</span></span>](introduction.md)
