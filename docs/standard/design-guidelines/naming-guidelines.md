---
title: Pokyny k pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: 1b137be60f4c8c1c7cf1fa1f807841d4bc209089
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290172"
---
# <a name="naming-guidelines"></a><span data-ttu-id="2e91e-102">Pokyny k pojmenování</span><span class="sxs-lookup"><span data-stu-id="2e91e-102">Naming Guidelines</span></span>
<span data-ttu-id="2e91e-103">Po konzistentní sadě konvencí pojmenování v rámci vývoje architektury může být hlavním příspěvkem k použitelnosti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2e91e-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="2e91e-104">Umožňuje, aby rozhraní používalo mnoho vývojářů v široce oddělených projektech.</span><span class="sxs-lookup"><span data-stu-id="2e91e-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="2e91e-105">Nad rámec konzistence formuláře musí být názvy elementů architektury snadno pochopitelné a musí vyjádřit funkci každého prvku.</span><span class="sxs-lookup"><span data-stu-id="2e91e-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="2e91e-106">Cílem této kapitoly je poskytnout konzistentní sadu konvencí pojmenování, která má za následek názvy, které vývojářům dávají bezprostřední smysl.</span><span class="sxs-lookup"><span data-stu-id="2e91e-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="2e91e-107">I když se tyto konvence pojmenování používají jako obecné pokyny pro vývoj kódu, budou mít za následek jednotnější pojmenování v celém kódu. je potřeba, abyste je mohli použít jenom na rozhraní API, která jsou veřejně vystavená (veřejné nebo chráněné typy a členy a explicitně implementovaná rozhraní).</span><span class="sxs-lookup"><span data-stu-id="2e91e-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e91e-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2e91e-108">In This Section</span></span>  
 [<span data-ttu-id="2e91e-109">Konvence psaní velkých písmen</span><span class="sxs-lookup"><span data-stu-id="2e91e-109">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="2e91e-110">Obecné zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="2e91e-110">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="2e91e-111">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="2e91e-111">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="2e91e-112">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="2e91e-112">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="2e91e-113">Názvy tříd, struktur a rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e91e-113">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="2e91e-114">Názvy členů typu</span><span class="sxs-lookup"><span data-stu-id="2e91e-114">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="2e91e-115">Parametry pojmenování</span><span class="sxs-lookup"><span data-stu-id="2e91e-115">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="2e91e-116">Pojmenovávání prostředků</span><span class="sxs-lookup"><span data-stu-id="2e91e-116">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="2e91e-117">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="2e91e-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2e91e-118">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="2e91e-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e91e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e91e-119">See also</span></span>

- [<span data-ttu-id="2e91e-120">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="2e91e-120">Framework Design Guidelines</span></span>](index.md)
