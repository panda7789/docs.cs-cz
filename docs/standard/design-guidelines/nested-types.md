---
title: Vnořené typy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 3467851aa767efcd0557e8a412cd36316a48b9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709150"
---
# <a name="nested-types"></a><span data-ttu-id="f0f6c-102">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="f0f6c-102">Nested Types</span></span>
<span data-ttu-id="f0f6c-103">Vnořený typ je typ definovaný v oboru jiného typu, který se nazývá nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="f0f6c-104">Vnořený typ má přístup ke všem členům svého nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="f0f6c-105">Má například přístup k soukromým polím definovaným v nadřazeném typu a chráněným polím definovaným ve všech nadřazených členů nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="f0f6c-106">Obecně platí, že vnořené typy by se měly používat zřídka.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="f0f6c-107">Z tohoto důvodu je k dispozici několik důvodů.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-107">There are several reasons for this.</span></span> <span data-ttu-id="f0f6c-108">Někteří vývojáři nejsou plně obeznámeni s konceptem.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="f0f6c-109">Tito vývojáři mohou mít například problémy s syntaxí deklarování proměnných vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="f0f6c-110">Vnořené typy jsou také velmi úzce spojeny s jejich nadřazenými typy a jako takové nejsou vhodné pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="f0f6c-111">Vnořené typy jsou nejvhodnější pro podrobnosti o implementaci modelování jejich nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="f0f6c-112">Koncový uživatel by měl definovat proměnné vnořeného typu zřídka a téměř nikdy by neměl muset explicitně vytvářet instance vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="f0f6c-113">Například enumerátor kolekce může být vnořeným typem kolekce.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="f0f6c-114">Enumerátory jsou obvykle vytvořeny pomocí jejich ohraničujícího typu a protože mnoho jazyků podporuje příkaz foreach, proměnné čítače výčtu zřídka musí být deklarovány koncovým uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="f0f6c-115">**✓ DO** použití vnořené typy vztah mezi vnořené typy a jeho vnější typ tak, aby člen usnadnění sémantika je žádoucí.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="f0f6c-116">**X DO NOT** použití veřejného vnořené typy jako logické seskupení vytvořit; pomocí oborů názvů pro tuto.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="f0f6c-117">**X AVOID** veřejně vystaven vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="f0f6c-118">Jedinou výjimkou je, že proměnné vnořeného typu musí být deklarovány pouze ve výjimečných scénářích, jako je například použití podtříd nebo jiné pokročilé scénáře přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="f0f6c-119">**X DO NOT** použijte vnořené typy, pokud typ je pravděpodobně bude odkazovat mimo nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="f0f6c-120">Například výčet předaný metodě definovanému pro třídu by neměl být definován jako vnořený typ ve třídě.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="f0f6c-121">**X DO NOT** použít vnořené typy, pokud je nutné vytvořit instanci kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="f0f6c-122">Má-li typ veřejný konstruktor, neměl by být pravděpodobně vnořený.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="f0f6c-123">Pokud lze vytvořit instanci typu, která označuje, že typ má místo v rozhraní vlastní (můžete ho vytvořit, pracovat s ním a zničit jej bez použití vnějšího typu), a proto by neměl být vnořen.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="f0f6c-124">Vnitřní typy by se neměly široce používat vně vnějšího typu bez jakéhokoli vztahu k vnějšímu typu.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="f0f6c-125">**X DO NOT** definovat vnořené typy jako člen rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="f0f6c-126">Mnohé jazyky tuto konstrukci nepodporují.</span><span class="sxs-lookup"><span data-stu-id="f0f6c-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="f0f6c-127">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="f0f6c-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f0f6c-128">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="f0f6c-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f6c-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0f6c-129">See also</span></span>

- [<span data-ttu-id="f0f6c-130">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="f0f6c-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="f0f6c-131">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="f0f6c-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
