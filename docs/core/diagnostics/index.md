---
title: Přehled diagnostických nástrojů – .NET Core
description: Přehled nástrojů a technik, které jsou k dispozici pro diagnostiku aplikací .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974126"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="1b3e1-103">Jaké diagnostické nástroje jsou k dispozici v .NET Core?</span><span class="sxs-lookup"><span data-stu-id="1b3e1-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="1b3e1-104">Software se vždy chová podle očekávání, ale rozhraní .NET Core obsahuje nástroje a rozhraní API, které vám pomohou rychle a efektivně diagnostikovat tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="1b3e1-105">Tento článek vám pomůže najít různé nástroje, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggersmanaged-debuggersmd"></a>[<span data-ttu-id="1b3e1-106">Spravované ladicí programy</span><span class="sxs-lookup"><span data-stu-id="1b3e1-106">Managed debuggers</span></span>](managed-debuggers.md)
<span data-ttu-id="1b3e1-107">Spravované ladicí programy umožňují pracovat s programem.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-107">Managed debuggers allow you to interact with your program.</span></span> <span data-ttu-id="1b3e1-108">Pozastavení, přírůstkové provádění, prozkoumání a obnovení, vám poskytne přehled o chování kódu.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="1b3e1-109">Ladicí program je první volbou pro diagnostiku funkčních problémů, které je možné snadno reprodukovat.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracinglogging-tracingmd"></a>[<span data-ttu-id="1b3e1-110">Protokolování a trasování</span><span class="sxs-lookup"><span data-stu-id="1b3e1-110">Logging and tracing</span></span>](logging-tracing.md)
<span data-ttu-id="1b3e1-111">Protokolování a trasování jsou související techniky.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-111">Logging and tracing are related techniques.</span></span> <span data-ttu-id="1b3e1-112">Odkazují na instrumentaci kódu k vytváření souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="1b3e1-113">Soubory zaznamenávají podrobnosti o tom, co program dělá.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-113">The files record the details of what a program does.</span></span> <span data-ttu-id="1b3e1-114">Pomocí těchto podrobností lze diagnostikovat nejsložitější problémy.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="1b3e1-115">V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testingtestingindexmd"></a>[<span data-ttu-id="1b3e1-116">Testování jednotek</span><span class="sxs-lookup"><span data-stu-id="1b3e1-116">Unit testing</span></span>](../testing/index.md)
<span data-ttu-id="1b3e1-117">Testování částí je klíčovou součástí kontinuální integrace a nasazování vysoce kvalitního softwaru.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-117">Unit testing is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="1b3e1-118">Testy jednotek jsou navržené tak, aby vám při přerušení nějakého upozornění poskytovala včasné varování.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-118">Unit tests are designed to give you an early warning when you break something.</span></span>
