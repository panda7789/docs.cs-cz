---
title: Názvy sestavení a knihoven DLL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ff14d3d804329e591486a7eb2a2ee7ed430f622c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="5472e-102">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="5472e-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="5472e-103">Sestavení je jednotka nasazení a identity pro spravovaný kód programy.</span><span class="sxs-lookup"><span data-stu-id="5472e-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="5472e-104">I když sestavení může mít rozsah jeden nebo více souborů, obvykle sestavení mapování typu 1: 1 s knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="5472e-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="5472e-105">Proto tato část popisuje pouze DLL zásady vytváření názvů, které lze poté mapovat na zásady vytváření názvů sestavení.</span><span class="sxs-lookup"><span data-stu-id="5472e-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="5472e-106">**PROVEĎTE ✓** zvolte názvy pro vaše sestavení knihovny DLL, které naznačují velké množství funkcí, jako je například System.Data.</span><span class="sxs-lookup"><span data-stu-id="5472e-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="5472e-107">Názvy sestavení a knihovny DLL nemají tak, aby odpovídaly názvy oborů názvů, ale je možné logicky podle oboru názvů v názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5472e-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="5472e-108">Dobré pravidlo je název knihovny DLL na základě předpony běžné obory názvů obsažené v sestavení.</span><span class="sxs-lookup"><span data-stu-id="5472e-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="5472e-109">Například sestavení s dva obory názvů, `MyCompany.MyTechnology.FirstFeature` a `MyCompany.MyTechnology.SecondFeature`, může být volána `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="5472e-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="5472e-110">**✓ ZVAŽTE** pojmenování knihovny DLL podle vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="5472e-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="5472e-111">kde `<Component>` obsahuje jeden nebo více klauzulích oddělené tečkou.</span><span class="sxs-lookup"><span data-stu-id="5472e-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="5472e-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5472e-112">For example:</span></span>  
  
 <span data-ttu-id="5472e-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="5472e-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="5472e-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="5472e-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5472e-115">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5472e-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5472e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5472e-116">See Also</span></span>  
 [<span data-ttu-id="5472e-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="5472e-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="5472e-118">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="5472e-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
