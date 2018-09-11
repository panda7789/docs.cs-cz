---
title: Návrh statické třídy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367363"
---
# <a name="static-class-design"></a><span data-ttu-id="4cb89-102">Návrh statické třídy</span><span class="sxs-lookup"><span data-stu-id="4cb89-102">Static Class Design</span></span>
<span data-ttu-id="4cb89-103">Statická třída je definována jako třída, která obsahuje pouze statické členy (samozřejmě kromě instance členy zděděné z <xref:System.Object?displayProperty=nameWithType> a pravděpodobně soukromého konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="4cb89-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="4cb89-104">Některé jazyky poskytují integrovanou podporu pro statické třídy.</span><span class="sxs-lookup"><span data-stu-id="4cb89-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="4cb89-105">V jazyce C# 2.0 nebo novější Pokud třída je deklarován jako statický, je zapečetěná, abstraktní a žádné členy instance můžete přepisu nebo deklarován.</span><span class="sxs-lookup"><span data-stu-id="4cb89-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="4cb89-106">Statické třídy jsou kompromis mezi čistě objektově orientovaný návrh a jednoduchost.</span><span class="sxs-lookup"><span data-stu-id="4cb89-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="4cb89-107">Se běžně používají k zajištění klávesové zkratky pro jiné operace (například <xref:System.IO.File?displayProperty=nameWithType>), držitele rozšiřující metody nebo funkce, pro kterou negarantované celý objekt objektově orientovanou obálku (například <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="4cb89-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="4cb89-108">**✓ DO** statické třídy používejte opatrně.</span><span class="sxs-lookup"><span data-stu-id="4cb89-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="4cb89-109">Statické třídy by měl používat pouze jako pomocných tříd pro objektově orientované core Framework.</span><span class="sxs-lookup"><span data-stu-id="4cb89-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="4cb89-110">**X DO NOT** statické třídy považovat za různé sady.</span><span class="sxs-lookup"><span data-stu-id="4cb89-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="4cb89-111">**X DO NOT** deklarovat nebo přepsání instance členové statické třídy.</span><span class="sxs-lookup"><span data-stu-id="4cb89-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="4cb89-112">**✓ DO** deklarovat statické třídy jako zapečetěné, abstraktní a přidejte konstruktor privátní instance, pokud si programovací jazyk nemá integrovanou podporu pro statické třídy.</span><span class="sxs-lookup"><span data-stu-id="4cb89-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="4cb89-113">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4cb89-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4cb89-114">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="4cb89-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb89-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cb89-115">See also</span></span>

- [<span data-ttu-id="4cb89-116">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="4cb89-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="4cb89-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="4cb89-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
