---
title: Pokyny v knihovně .NET Open source
description: Doporučení osvědčených postupů pro vývojáře k vytvoření vysoce kvalitní knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: 85d76c8b2bd0f030e3fbc1987e6ff51d6da44e76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644389"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="345b7-103">Pokyny pro open-source knihovnu</span><span class="sxs-lookup"><span data-stu-id="345b7-103">Open-source library guidance</span></span>

<span data-ttu-id="345b7-104">Tento návod obsahuje doporučení pro vývojáře umožňující vytváření vysoce kvalitních knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="345b7-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="345b7-105">Tato dokumentace se zaměřuje na *co* a *proč* při sestavování knihovny .NET, ne *jak*.</span><span class="sxs-lookup"><span data-stu-id="345b7-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="345b7-106">Vysoce kvalitní knihoven .NET open-source aspekty:</span><span class="sxs-lookup"><span data-stu-id="345b7-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="345b7-107">**Inkluzivní** – knihovny .NET vhodné snažit se podporují mnoho platforem, programovacích jazyků a aplikací.</span><span class="sxs-lookup"><span data-stu-id="345b7-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="345b7-108">**Stabilní** – knihovny .NET dobré existovat vedle sebe v ekosystému .NET, používané aplikace sestavené s mnoha knihoven.</span><span class="sxs-lookup"><span data-stu-id="345b7-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="345b7-109">**Navržené tak, aby vyvíjí** – knihovny pro .NET by měl vylepšit a postupně při současné podpoře stávající uživatele.</span><span class="sxs-lookup"><span data-stu-id="345b7-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="345b7-110">**Laditelný** – knihovny pro .NET používali nejnovější nástroje potřebné k vytváření skvělé možnosti ladění pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="345b7-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="345b7-111">**Důvěryhodné** – knihovny pro .NET mají vztah důvěryhodnosti vývojářů verzi publikováním NuGet pomocí osvědčené postupy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="345b7-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="345b7-112">Začínáme</span><span class="sxs-lookup"><span data-stu-id="345b7-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="345b7-113">Typů doporučení</span><span class="sxs-lookup"><span data-stu-id="345b7-113">Types of recommendations</span></span>

<span data-ttu-id="345b7-114">Každý článek představuje čtyři typy doporučení: **Proveďte**, **vezměte v úvahu**, **vyhnout**, a **nepodporují**.</span><span class="sxs-lookup"><span data-stu-id="345b7-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="345b7-115">Typ doporučení se jedná Určuje, jak důrazně má následovat.</span><span class="sxs-lookup"><span data-stu-id="345b7-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="345b7-116">Téměř vždy měli byste postupovat podle **proveďte** doporučení.</span><span class="sxs-lookup"><span data-stu-id="345b7-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="345b7-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="345b7-117">For example:</span></span>

<span data-ttu-id="345b7-118">**PROVEĎTE ✔️** distribuovat knihovny pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="345b7-118">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="345b7-119">Na druhé straně **zvažte** byste obecně měli dodržet, doporučení, ale existují legitimní výjimky z pravidla a by neměl mít pocit chybný o není následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="345b7-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="345b7-120">**✔️ ZVAŽTE** pomocí [SemVer 2.0.0](https://semver.org/) verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="345b7-120">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="345b7-121">**Vyhněte se** doporučení zmiňovat věcí, které nejsou obecně vhodné, ale někdy zásadní pravidlo smysl:</span><span class="sxs-lookup"><span data-stu-id="345b7-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="345b7-122">**❌ Nepoužívejte** odkazy na balíčky NuGet, které vyžadují přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="345b7-122">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="345b7-123">A nakonec **nejsou** doporučení znamenat něco téměř nikdy byste měli dělat:</span><span class="sxs-lookup"><span data-stu-id="345b7-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="345b7-124">**❌ NEPODPORUJÍ** publikování silným názvem a jiných silným názvem verzí knihovny.</span><span class="sxs-lookup"><span data-stu-id="345b7-124">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="345b7-125">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="345b7-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="345b7-126">Next</span><span class="sxs-lookup"><span data-stu-id="345b7-126">Next</span></span>](get-started.md)
