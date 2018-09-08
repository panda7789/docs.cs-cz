---
title: Názvy sestavení a knihoven DLL
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97bd152cff53fb1c2edb107b6d6b34bd91ca1c49
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187647"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="06110-102">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="06110-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="06110-103">Sestavení je jednotka nasazení a identity pro programy pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="06110-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="06110-104">I když sestavení může zahrnovat jeden nebo více souborů, obvykle sestavení mapování 1: 1 s knihovnou DLL.</span><span class="sxs-lookup"><span data-stu-id="06110-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="06110-105">Proto tato část popisuje pouze knihovny DLL konvence, které pak můžou být mapované na zásady vytváření názvů sestavení.</span><span class="sxs-lookup"><span data-stu-id="06110-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="06110-106">**✓ DO** zvolte názvy pro vaše sestavení knihovny DLL, které naznačují velké množství funkcí, jako je například System.Data.</span><span class="sxs-lookup"><span data-stu-id="06110-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="06110-107">Názvy sestavení a knihovny DLL nemají tak, aby odpovídaly názvy oborů názvů, ale je možné logicky při pojmenování sestavení, postupujte podle názvu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="06110-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="06110-108">Základním pravidlem je název knihovny DLL, na základě běžných předpony oborů názvů obsaženy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="06110-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="06110-109">Například sestavení se dva obory názvů, `MyCompany.MyTechnology.FirstFeature` a `MyCompany.MyTechnology.SecondFeature`, může být volána `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="06110-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="06110-110">**✓ CONSIDER** pojmenování knihovny DLL podle vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="06110-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="06110-111">kde `<Component>` obsahuje jednu či více klauzulí oddělené tečkou.</span><span class="sxs-lookup"><span data-stu-id="06110-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="06110-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="06110-112">For example:</span></span>  
  
 <span data-ttu-id="06110-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="06110-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="06110-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="06110-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="06110-115">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="06110-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06110-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06110-116">See also</span></span>

- [<span data-ttu-id="06110-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="06110-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="06110-118">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="06110-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
