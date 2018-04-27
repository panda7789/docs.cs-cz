---
title: Pokyny pro pojmenování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 91b392c2fe895499b9da83cfd773edb1128a429b
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="naming-guidelines"></a><span data-ttu-id="ea9ef-102">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="ea9ef-102">Naming Guidelines</span></span>
<span data-ttu-id="ea9ef-103">Následující sadu konzistentní zásady vytváření názvů pro vývoj prostředí může být hlavní příspěvkem k rozhraní framework použitelnost.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="ea9ef-104">To umožňuje framework má být používána celá řada vývojářů na široce oddělených projekty.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="ea9ef-105">Nad rámec konzistence formuláře názvy elementů framework musí snadno pochopit a musí obsahovat funkci jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="ea9ef-106">Cílem této kapitoly je zajistit konzistentní sadu zásady vytváření názvů, jejímž výsledkem názvy, které okamžitou smysl pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="ea9ef-107">I když tyto zásady vytváření názvů přijetí jako pokyny pro vývoj obecné kódu by mělo za následek více konzistentní názvy v rámci vašeho kódu, je nutné pouze aplikovat na rozhraní API, které jsou viditelné veřejně (veřejné nebo chráněných typů a členů, a explicitně implementované rozhraní).</span><span class="sxs-lookup"><span data-stu-id="ea9ef-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea9ef-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ea9ef-108">In This Section</span></span>  
 [<span data-ttu-id="ea9ef-109">Konvence pro malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="ea9ef-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="ea9ef-110">Obecné zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="ea9ef-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="ea9ef-111">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="ea9ef-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="ea9ef-112">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="ea9ef-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="ea9ef-113">Názvy tříd, struktur a rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea9ef-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="ea9ef-114">Názvy členů typu</span><span class="sxs-lookup"><span data-stu-id="ea9ef-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="ea9ef-115">Parametry pojmenování</span><span class="sxs-lookup"><span data-stu-id="ea9ef-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="ea9ef-116">Prostředky pojmenování</span><span class="sxs-lookup"><span data-stu-id="ea9ef-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="ea9ef-117">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ea9ef-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ea9ef-118">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ea9ef-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9ef-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea9ef-119">See Also</span></span>  
 [<span data-ttu-id="ea9ef-120">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ea9ef-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
