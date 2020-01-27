---
title: Návrh abstraktní třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 018dd353024e75e9819f5a97008f2f422ecad291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739057"
---
# <a name="abstract-class-design"></a><span data-ttu-id="5448d-102">Návrh abstraktní třídy</span><span class="sxs-lookup"><span data-stu-id="5448d-102">Abstract Class Design</span></span>

<span data-ttu-id="5448d-103">❌ v abstraktních typech nedefinujte veřejné nebo chráněné interní konstruktory.</span><span class="sxs-lookup"><span data-stu-id="5448d-103">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="5448d-104">Konstruktory by měly být veřejné pouze v případě, že uživatelé budou muset vytvořit instance daného typu.</span><span class="sxs-lookup"><span data-stu-id="5448d-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="5448d-105">Vzhledem k tomu, že nemůžete vytvořit instance abstraktního typu, je abstraktní typ s veřejným konstruktorem pro uživatele nesprávně navržený a zavádějící.</span><span class="sxs-lookup"><span data-stu-id="5448d-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="5448d-106">✔️ v abstraktních třídách definujte chráněný nebo interní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5448d-106">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="5448d-107">Chráněný konstruktor je běžnější a jednoduše umožňuje základní třídě provádět vlastní inicializaci při vytváření podtypů.</span><span class="sxs-lookup"><span data-stu-id="5448d-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="5448d-108">Vnitřní konstruktor lze použít k omezení konkrétní implementace abstraktní třídy na sestavení, které definuje třídu.</span><span class="sxs-lookup"><span data-stu-id="5448d-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="5448d-109">✔️ Zadejte alespoň jeden konkrétní typ, který dědí ze všech abstraktních tříd, které dodáváte.</span><span class="sxs-lookup"><span data-stu-id="5448d-109">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="5448d-110">To pomáhá ověřit návrh abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="5448d-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="5448d-111">Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementace <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="5448d-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="5448d-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="5448d-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5448d-113">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="5448d-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5448d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5448d-114">See also</span></span>

- [<span data-ttu-id="5448d-115">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="5448d-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="5448d-116">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="5448d-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
