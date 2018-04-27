---
title: Statická třída návrhu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a6143b128442db1ac090f0b3680f94b1ac9a9cfc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="static-class-design"></a><span data-ttu-id="948e7-102">Statická třída návrhu</span><span class="sxs-lookup"><span data-stu-id="948e7-102">Static Class Design</span></span>
<span data-ttu-id="948e7-103">Statická třída je definovaný jako třída, která obsahuje jenom statické členy (samozřejmě kromě členů instance zděděno z <xref:System.Object?displayProperty=nameWithType> a které by mohly mít soukromý konstruktor).</span><span class="sxs-lookup"><span data-stu-id="948e7-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="948e7-104">Některé jazyky poskytují integrovanou podporu pro statické třídy.</span><span class="sxs-lookup"><span data-stu-id="948e7-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="948e7-105">V C# 2.0 nebo novější Pokud třída je deklarován jako statický, zapečetěné, je abstraktní a žádní členové instance můžete přepsat nebo deklarován.</span><span class="sxs-lookup"><span data-stu-id="948e7-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="948e7-106">Statické třídy jsou kompromis mezi čistý objektově orientované návrhu a jednoduchost.</span><span class="sxs-lookup"><span data-stu-id="948e7-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="948e7-107">Běžně se používají k poskytování zástupce dalších operací (například <xref:System.IO.File?displayProperty=nameWithType>), držitele rozšiřující metody nebo funkce, pro které je úplné objektově orientované obálku bude vyplacena neoprávněně (například <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="948e7-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="948e7-108">**PROVEĎTE ✓** statické třídy používejte opatrně.</span><span class="sxs-lookup"><span data-stu-id="948e7-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="948e7-109">Statické třídy má být použit pouze jako podpora třídy pro základní objektově orientované rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="948e7-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="948e7-110">**X nesmí** statické třídy považovat za různé sady.</span><span class="sxs-lookup"><span data-stu-id="948e7-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="948e7-111">**X nesmí** deklarovat nebo přepsání instance členové statické třídy.</span><span class="sxs-lookup"><span data-stu-id="948e7-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="948e7-112">**PROVEĎTE ✓** deklarovat statické třídy jako zapečetěné, abstraktní a přidejte konstruktor privátní instance, pokud si programovací jazyk nemá integrovanou podporu pro statické třídy.</span><span class="sxs-lookup"><span data-stu-id="948e7-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="948e7-113">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="948e7-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="948e7-114">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="948e7-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="948e7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="948e7-115">See Also</span></span>  
 [<span data-ttu-id="948e7-116">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="948e7-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="948e7-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="948e7-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
