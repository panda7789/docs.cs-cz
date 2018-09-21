---
title: Pokyny pro pojmenování
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70888e068782add5ebe5ae1c7da3bdee842faea8
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46518269"
---
# <a name="naming-guidelines"></a><span data-ttu-id="cc52f-102">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="cc52f-102">Naming Guidelines</span></span>
<span data-ttu-id="cc52f-103">Následující konzistentní sadu konvence pojmenování ve vývoji rozhraní může být hlavní příspěvek do rozhraní framework použitelnost.</span><span class="sxs-lookup"><span data-stu-id="cc52f-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="cc52f-104">To umožňuje rozhraní pro mnoho vývojářů na široce oddělených projektech.</span><span class="sxs-lookup"><span data-stu-id="cc52f-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="cc52f-105">Nad rámec konzistence formuláře názvy prvků framework snadno pochopitelný a musí obsahovat funkci jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="cc52f-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="cc52f-106">Cílem této kapitole je sada konzistentní zásady vytváření názvů, jehož výsledkem názvy, které dávají smysl okamžité pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="cc52f-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="cc52f-107">I když tyto zásady vytváření názvů přijetí, jak kód obecné pokyny k vývoji by mělo za následek více konzistentní pojmenování v rámci kódu, je nutné pouze aplikovat na rozhraní API, která jsou veřejně přístupné (veřejné nebo chráněné typy a členy, a – explicitně implementovaná rozhraní).</span><span class="sxs-lookup"><span data-stu-id="cc52f-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc52f-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cc52f-108">In This Section</span></span>  
 [<span data-ttu-id="cc52f-109">Konvence pro malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="cc52f-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="cc52f-110">Obecné zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="cc52f-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="cc52f-111">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="cc52f-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="cc52f-112">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="cc52f-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="cc52f-113">Názvy tříd, struktur a rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc52f-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="cc52f-114">Názvy členů typu</span><span class="sxs-lookup"><span data-stu-id="cc52f-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="cc52f-115">Parametry pojmenování</span><span class="sxs-lookup"><span data-stu-id="cc52f-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="cc52f-116">Prostředky pojmenování</span><span class="sxs-lookup"><span data-stu-id="cc52f-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="cc52f-117">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="cc52f-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cc52f-118">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="cc52f-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc52f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc52f-119">See also</span></span>

- [<span data-ttu-id="cc52f-120">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="cc52f-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
