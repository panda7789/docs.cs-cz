---
title: Pokyny k open source knihovně .NET
description: Doporučení pro osvědčené postupy pro vývojáře k vytváření vysoce kvalitních knihoven .NET.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731434"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="a1ca6-103">Pokyny pro open-source knihovnu</span><span class="sxs-lookup"><span data-stu-id="a1ca6-103">Open-source library guidance</span></span>

<span data-ttu-id="a1ca6-104">Tento průvodce poskytuje doporučení pro vývojáře k vytváření vysoce kvalitních knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="a1ca6-105">Tato dokumentace se zaměřuje na to, *co* a *Proč* při sestavování knihovny .NET, nikoli na *jak*.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="a1ca6-106">Aspekty vysoce kvalitních Open Source knihoven .NET:</span><span class="sxs-lookup"><span data-stu-id="a1ca6-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a1ca6-107">**Včetně** kvalitních knihoven .NET usiluje o podporu řady platforem, programovacích jazyků a aplikací.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="a1ca6-108">**Stabilní** knihovny .NET v ekosystému .NET společně fungují v aplikacích, které jsou sestavené s mnoha knihovnami.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="a1ca6-109">**Navrženo pro vývoj** – knihovny .NET by se měly zlepšovat a vyvíjet v průběhu času a podporovat stávající uživatele.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="a1ca6-110">**Laditelné** – knihovny .NET by měly používat nejnovější nástroje k vytvoření skvělého prostředí ladění pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="a1ca6-111">**Důvěryhodné** knihovny .NET mají důvěru vývojářů publikováním do NuGet pomocí osvědčených postupů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a1ca6-112">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a1ca6-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="a1ca6-113">Typy doporučení</span><span class="sxs-lookup"><span data-stu-id="a1ca6-113">Types of recommendations</span></span>

<span data-ttu-id="a1ca6-114">Každý článek nabízí čtyři typy doporučení: **udělejte**, **zvažte**, **Vyhněte**se a **nepoužívejte.**</span><span class="sxs-lookup"><span data-stu-id="a1ca6-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="a1ca6-115">Typ doporučení indikuje, jak by měl následovat.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="a1ca6-116">Měli byste téměř **vždy postupovat podle doporučení do** .</span><span class="sxs-lookup"><span data-stu-id="a1ca6-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="a1ca6-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1ca6-117">For example:</span></span>

<span data-ttu-id="a1ca6-118">✔️ k distribuci knihovny pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-118">✔️ DO distribute your library using a NuGet package.</span></span>

<span data-ttu-id="a1ca6-119">Na druhé **straně doporučujeme,** aby se obecně následovala doporučení, ale v tomto pravidle existují legitimní výjimky a neměli byste mít na starosti žádné informace o tom, co se s těmito pokyny nedaří:</span><span class="sxs-lookup"><span data-stu-id="a1ca6-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="a1ca6-120">✔️ Zvažte použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-120">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="a1ca6-121">**Vyhněte** se doporučením označení věcí, které obecně nejsou dobrý nápad, ale porušení pravidla je někdy vhodné:</span><span class="sxs-lookup"><span data-stu-id="a1ca6-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="a1ca6-122">❌ se vyhnout odkazům na balíček NuGet, které vyžadují přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-122">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="a1ca6-123">A nakonec nenaznačují doporučení, co byste měli skoro **nikdy dělat:**</span><span class="sxs-lookup"><span data-stu-id="a1ca6-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="a1ca6-124">❌ nepublikujte v knihovně silně pojmenované a nedostatečně pojmenované verze vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-124">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="a1ca6-125">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="a1ca6-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="a1ca6-126">Next</span><span class="sxs-lookup"><span data-stu-id="a1ca6-126">Next</span></span>](get-started.md)
