---
title: Pokyny pro open-source knihovnu
description: Doporučení osvědčených postupů pro vývojáře k vytvoření vysoce kvalitní knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: ca95cb5ba1ebf27464397b7850ac02aabded1a5b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188622"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="50dc4-103">Pokyny pro open-source knihovnu</span><span class="sxs-lookup"><span data-stu-id="50dc4-103">Open-source library guidance</span></span>

<span data-ttu-id="50dc4-104">Tento návod obsahuje doporučení pro vývojáře umožňující vytváření vysoce kvalitních knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="50dc4-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="50dc4-105">Tato dokumentace se zaměřuje na *co* a *proč* při sestavování knihovny .NET, ne *jak*.</span><span class="sxs-lookup"><span data-stu-id="50dc4-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="50dc4-106">Vysoce kvalitní knihoven .NET open-source aspekty:</span><span class="sxs-lookup"><span data-stu-id="50dc4-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="50dc4-107">**Inkluzivní** – knihovny .NET vhodné snažit se podporují mnoho platforem, programovacích jazyků a aplikací.</span><span class="sxs-lookup"><span data-stu-id="50dc4-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="50dc4-108">**Stabilní** – knihovny .NET dobré existovat vedle sebe v ekosystému .NET, používané aplikace sestavené s mnoha knihoven.</span><span class="sxs-lookup"><span data-stu-id="50dc4-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="50dc4-109">**Navržené tak, aby vyvíjí** – knihovny pro .NET by měl vylepšit a postupně při současné podpoře stávající uživatele.</span><span class="sxs-lookup"><span data-stu-id="50dc4-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="50dc4-110">**Laditelný** – knihovny pro .NET používali nejnovější nástroje potřebné k vytváření skvělé možnosti ladění pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="50dc4-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="50dc4-111">**Důvěryhodné** – knihovny pro .NET mají vztah důvěryhodnosti vývojářů verzi publikováním NuGet pomocí osvědčené postupy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="50dc4-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="50dc4-112">Začínáme</span><span class="sxs-lookup"><span data-stu-id="50dc4-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="50dc4-113">Typů doporučení</span><span class="sxs-lookup"><span data-stu-id="50dc4-113">Types of recommendations</span></span>

<span data-ttu-id="50dc4-114">Každý článek představuje čtyři typy doporučení: **proveďte**, **zvažte**, **nepoužívejte**, a **nepodporují**.</span><span class="sxs-lookup"><span data-stu-id="50dc4-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="50dc4-115">Typ doporučení se jedná Určuje, jak důrazně má následovat.</span><span class="sxs-lookup"><span data-stu-id="50dc4-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="50dc4-116">Téměř vždy měli byste postupovat podle **proveďte** doporučení.</span><span class="sxs-lookup"><span data-stu-id="50dc4-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="50dc4-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="50dc4-117">For example:</span></span>

<span data-ttu-id="50dc4-118">**PROVEĎTE ✔️** distribuovat knihovny pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="50dc4-118">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="50dc4-119">Na druhé straně **zvažte** byste obecně měli dodržet, doporučení, ale existují legitimní výjimky z pravidla a by neměl mít pocit chybný o není následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="50dc4-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="50dc4-120">**✔️ ZVAŽTE** pomocí [SemVer 2.0.0](https://semver.org/) verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="50dc4-120">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="50dc4-121">**Vyhněte se** doporučení zmiňovat věcí, které nejsou obecně vhodné, ale někdy zásadní pravidlo smysl:</span><span class="sxs-lookup"><span data-stu-id="50dc4-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="50dc4-122">**❌ Nepoužívejte** odkazy na balíčky NuGet, které vyžadují přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="50dc4-122">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="50dc4-123">A nakonec **nejsou** doporučení znamenat něco téměř nikdy byste měli dělat:</span><span class="sxs-lookup"><span data-stu-id="50dc4-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="50dc4-124">**❌ NEPODPORUJÍ** publikování silným názvem a jiných silným názvem verzí knihovny.</span><span class="sxs-lookup"><span data-stu-id="50dc4-124">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="50dc4-125">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="50dc4-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="50dc4-126">Next</span><span class="sxs-lookup"><span data-stu-id="50dc4-126">Next</span></span>](./get-started.md)
