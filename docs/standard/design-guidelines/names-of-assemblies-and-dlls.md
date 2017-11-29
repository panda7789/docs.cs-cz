---
title: "Názvy sestavení a knihoven DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 071ca1547898b80440e86df0e4cb9c0667e462ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="ecc48-102">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="ecc48-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="ecc48-103">Sestavení je jednotka nasazení a identity pro spravovaný kód programy.</span><span class="sxs-lookup"><span data-stu-id="ecc48-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="ecc48-104">I když sestavení může mít rozsah jeden nebo více souborů, obvykle sestavení mapování typu 1: 1 s knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="ecc48-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="ecc48-105">Proto tato část popisuje pouze DLL zásady vytváření názvů, které lze poté mapovat na zásady vytváření názvů sestavení.</span><span class="sxs-lookup"><span data-stu-id="ecc48-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="ecc48-106">**PROVEĎTE ✓** zvolte názvy pro vaše sestavení knihovny DLL, které naznačují velké množství funkcí, jako je například System.Data.</span><span class="sxs-lookup"><span data-stu-id="ecc48-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="ecc48-107">Názvy sestavení a knihovny DLL nemají tak, aby odpovídaly názvy oborů názvů, ale je možné logicky podle oboru názvů v názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="ecc48-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="ecc48-108">Dobré pravidlo je název knihovny DLL na základě běžných předpony sestavení obsažený v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ecc48-108">A good rule of thumb is to name the DLL based on the common prefix of the assemblies contained in the assembly.</span></span> <span data-ttu-id="ecc48-109">Například sestavení s dva obory názvů, `MyCompany.MyTechnology.FirstFeature` a `MyCompany.MyTechnology.SecondFeature`, může být volána `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="ecc48-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="ecc48-110">**✓ ZVAŽTE** pojmenování knihovny DLL podle vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="ecc48-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="ecc48-111">kde `<Component>` obsahuje jeden nebo více klauzulích oddělené tečkou.</span><span class="sxs-lookup"><span data-stu-id="ecc48-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="ecc48-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ecc48-112">For example:</span></span>  
  
 <span data-ttu-id="ecc48-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="ecc48-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="ecc48-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ecc48-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ecc48-115">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ecc48-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc48-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecc48-116">See Also</span></span>  
 [<span data-ttu-id="ecc48-117">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="ecc48-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="ecc48-118">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="ecc48-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
