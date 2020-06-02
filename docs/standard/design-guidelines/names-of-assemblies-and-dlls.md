---
title: Názvy sestavení a knihoven DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 138ae8154b0d10fb813f0c98ceb7c58a2471b780
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291952"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="ebc05-102">Názvy sestavení a knihoven DLL</span><span class="sxs-lookup"><span data-stu-id="ebc05-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="ebc05-103">Sestavení je jednotka nasazení a identita pro programy spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ebc05-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="ebc05-104">Přestože sestavení mohou zahrnovat jeden nebo více souborů, obvykle sestavení mapuje 1:1 pomocí knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="ebc05-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="ebc05-105">Proto tato část popisuje pouze konvence vytváření názvů knihoven DLL, které je možné namapovat na zásady vytváření názvů sestavení.</span><span class="sxs-lookup"><span data-stu-id="ebc05-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="ebc05-106">✔️ zvolit názvy pro knihovny DLL sestavení, které navrhují velké bloky funkčnosti, jako je System. data.</span><span class="sxs-lookup"><span data-stu-id="ebc05-106">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="ebc05-107">Názvy sestavení a knihoven DLL nemusí odpovídat názvům oboru názvů, ale při pojmenování sestavení je vhodné použít název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ebc05-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="ebc05-108">Dobrým pravidlem obsluhy je pojmenování knihovny DLL na základě společné předpony oborů názvů obsažených v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ebc05-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="ebc05-109">Například sestavení se dvěma obory názvů `MyCompany.MyTechnology.FirstFeature` a, lze `MyCompany.MyTechnology.SecondFeature` volat `MyCompany.MyTechnology.dll` .</span><span class="sxs-lookup"><span data-stu-id="ebc05-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="ebc05-110">✔️ Zvažte pojmenování knihoven DLL podle následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="ebc05-110">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="ebc05-111">kde `<Component>` obsahuje jednu nebo více klauzulí oddělených tečkou.</span><span class="sxs-lookup"><span data-stu-id="ebc05-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="ebc05-112">Například:</span><span class="sxs-lookup"><span data-stu-id="ebc05-112">For example:</span></span>

 <span data-ttu-id="ebc05-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="ebc05-113">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="ebc05-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ebc05-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ebc05-115">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="ebc05-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ebc05-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebc05-116">See also</span></span>

- [<span data-ttu-id="ebc05-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ebc05-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ebc05-118">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="ebc05-118">Naming Guidelines</span></span>](naming-guidelines.md)
