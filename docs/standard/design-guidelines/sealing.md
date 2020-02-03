---
title: Zapečetění
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: ddf463e98fb6a9c5ccaae90e9cfc74b5691b13a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743623"
---
# <a name="sealing"></a><span data-ttu-id="37064-102">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="37064-102">Sealing</span></span>
<span data-ttu-id="37064-103">Jednou z funkcí objektů orientovaných na objekty je, že je vývojáři mohou roztáhnout a přizpůsobit způsobem, který neočekává návrháři rozhraní.</span><span class="sxs-lookup"><span data-stu-id="37064-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="37064-104">Jedná se o výkon i nebezpečí rozšiřitelného návrhu.</span><span class="sxs-lookup"><span data-stu-id="37064-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="37064-105">Při návrhu architektury je proto velmi důležité pečlivě navrhovat rozšiřitelnost, když je to žádoucí, a omezit rozšiřitelnost, pokud je to nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="37064-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="37064-106">Výkonný mechanismus, který brání rozšíření.</span><span class="sxs-lookup"><span data-stu-id="37064-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="37064-107">Můžete zapečetit buď třídu, nebo jednotlivé členy.</span><span class="sxs-lookup"><span data-stu-id="37064-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="37064-108">Zapečetění třídy brání uživatelům v dědění z třídy.</span><span class="sxs-lookup"><span data-stu-id="37064-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="37064-109">Uzavření člena zabrání uživatelům v přepsání určitého člena.</span><span class="sxs-lookup"><span data-stu-id="37064-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="37064-110">❌ nezapečetit třídy, aniž by to mělo dobrý důvod.</span><span class="sxs-lookup"><span data-stu-id="37064-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="37064-111">Zapečetění třídy, protože si nemůžete představit scénář rozšiřitelnosti není dobrým důvodem.</span><span class="sxs-lookup"><span data-stu-id="37064-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="37064-112">Uživatelé rozhraní, jako je dědění z tříd pro různé Nezřejmé důvody, jako je přidání praktických členů.</span><span class="sxs-lookup"><span data-stu-id="37064-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="37064-113">Příklady nezřejméch důvodů, které uživatelé chtějí zdědit z typu, naleznete v tématu [nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md) .</span><span class="sxs-lookup"><span data-stu-id="37064-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="37064-114">Mezi vhodné důvody pro zapečetění třídy patří následující:</span><span class="sxs-lookup"><span data-stu-id="37064-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="37064-115">Třída je statická třída.</span><span class="sxs-lookup"><span data-stu-id="37064-115">The class is a static class.</span></span> <span data-ttu-id="37064-116">Viz [design statické třídy](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="37064-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>

- <span data-ttu-id="37064-117">Třída ukládá tajné klíče citlivé na zabezpečení ve zděděných chráněných členech.</span><span class="sxs-lookup"><span data-stu-id="37064-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="37064-118">Třída zdědí mnoho virtuálních členů a náklady na jejich zapečetění, by převažují nad výhodami opustit třídu, která není zapečetěná.</span><span class="sxs-lookup"><span data-stu-id="37064-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="37064-119">Třída je atribut, který vyžaduje velmi rychlé vyhledání za běhu.</span><span class="sxs-lookup"><span data-stu-id="37064-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="37064-120">Zapečetěné atributy mají mírně vyšší úroveň výkonu než nezapečetěné.</span><span class="sxs-lookup"><span data-stu-id="37064-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="37064-121">Viz [atributy](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="37064-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>

 <span data-ttu-id="37064-122">❌ Nedeklarujte chráněné ani virtuální členy u zapečetěných typů.</span><span class="sxs-lookup"><span data-stu-id="37064-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="37064-123">Podle definice nemůže být zapečetěné typy děděny.</span><span class="sxs-lookup"><span data-stu-id="37064-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="37064-124">To znamená, že nelze volat chráněné členy pro zapečetěné typy a virtuální metody pro zapečetěné typy nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="37064-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="37064-125">✔️ Zvažte uzavření členů, které jste přepsali.</span><span class="sxs-lookup"><span data-stu-id="37064-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="37064-126">Problémy, které mohou vést k představení virtuálních členů (popsaných v tématu [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)), se vztahují i na přepsání, i když do mírně menšího stupně.</span><span class="sxs-lookup"><span data-stu-id="37064-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="37064-127">Z tohoto okamžiku v hierarchii dědičnosti zapečetí přepisy, které z těchto problémů začínají.</span><span class="sxs-lookup"><span data-stu-id="37064-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="37064-128">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="37064-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="37064-129">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="37064-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="37064-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="37064-130">See also</span></span>

- [<span data-ttu-id="37064-131">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="37064-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="37064-132">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="37064-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="37064-133">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="37064-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
