---
title: Pokyny k knihovně .NET s otevřeným zdrojovým kódem
description: Doporučení osvědčených postupů pro vývojáře k vytvoření vysoce kvalitních knihoven .NET.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731434"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="2632c-103">Pokyny pro open-source knihovnu</span><span class="sxs-lookup"><span data-stu-id="2632c-103">Open-source library guidance</span></span>

<span data-ttu-id="2632c-104">Tento návod obsahuje doporučení pro vývojáře k vytvoření vysoce kvalitních knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="2632c-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="2632c-105">Tato dokumentace se zaměřuje na *co* a *proč* při vytváření *knihovny*.NET, nikoli jak .</span><span class="sxs-lookup"><span data-stu-id="2632c-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="2632c-106">Aspekty vysoce kvalitních open-source knihoven .NET:</span><span class="sxs-lookup"><span data-stu-id="2632c-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="2632c-107">**Včetně** - Dobré knihovny .NET se snaží podporovat mnoho platforem, programovacích jazyků a aplikací.</span><span class="sxs-lookup"><span data-stu-id="2632c-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="2632c-108">**Stable** - Good .NET knihovny koexistovat v ekosystému .NET, spuštěné v aplikacích vytvořených s mnoha knihovnami.</span><span class="sxs-lookup"><span data-stu-id="2632c-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="2632c-109">**Navrženo tak, aby se vyvíjelo** – knihovny .NET by se měly v průběhu času zlepšovat a vyvíjet a zároveň podporovat stávající uživatele.</span><span class="sxs-lookup"><span data-stu-id="2632c-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="2632c-110">**Laditelné** - knihovny .NET by měly používat nejnovější nástroje k vytvoření skvělého prostředí pro ladění pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="2632c-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="2632c-111">**Důvěryhodné** - knihovny .NET mají důvěryhodnost vývojářů publikováním na NuGet pomocí osvědčených postupů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2632c-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2632c-112">Začínáme</span><span class="sxs-lookup"><span data-stu-id="2632c-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="2632c-113">Typy doporučení</span><span class="sxs-lookup"><span data-stu-id="2632c-113">Types of recommendations</span></span>

<span data-ttu-id="2632c-114">Každý článek obsahuje čtyři typy doporučení: **Do**, **Zvažte**, **Vyhnout**, a **Ne**.</span><span class="sxs-lookup"><span data-stu-id="2632c-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="2632c-115">Typ doporučení označuje, jak silně by měl být dodržován.</span><span class="sxs-lookup"><span data-stu-id="2632c-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="2632c-116">Měli byste téměř vždy dodržovat doporučení **Do.**</span><span class="sxs-lookup"><span data-stu-id="2632c-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="2632c-117">Například:</span><span class="sxs-lookup"><span data-stu-id="2632c-117">For example:</span></span>

<span data-ttu-id="2632c-118">✔️ do distribuovat knihovnu pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2632c-118">✔️ DO distribute your library using a NuGet package.</span></span>

<span data-ttu-id="2632c-119">Na druhou stranu, **Zvažte** doporučení by měla být obecně dodržována, ale existují legitimní výjimky z pravidla a neměli byste se cítit špatně, že nedodržujete pokyny:</span><span class="sxs-lookup"><span data-stu-id="2632c-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="2632c-120">✔️ zvažte použití [SemVer 2.0.0](https://semver.org/) k verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2632c-120">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="2632c-121">**Vyhněte se** doporučení zmínit věci, které jsou obecně není dobrý nápad, ale porušení pravidla někdy dává smysl:</span><span class="sxs-lookup"><span data-stu-id="2632c-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="2632c-122">❌VYHNĚTE se NuGet odkazy na balíček, které vyžadují přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="2632c-122">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="2632c-123">A konečně, **Nepoužívejte** doporučení naznačují něco, co byste měli téměř nikdy dělat:</span><span class="sxs-lookup"><span data-stu-id="2632c-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="2632c-124">❌NEPublikujte verze knihovny se silným názvem a bez silného název.</span><span class="sxs-lookup"><span data-stu-id="2632c-124">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="2632c-125">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="2632c-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="2632c-126">Další</span><span class="sxs-lookup"><span data-stu-id="2632c-126">Next</span></span>](get-started.md)
