---
title: Je vyžadován odkaz na sestavení '<assemblyname>' obsahující třídu Base '<classname>'.
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: 54848fdbd2547fe021f0386843f9666760396cb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013774"
---
# <a name="reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="39206-102">Odkaz vyžadoval sestavení '\<assemblyname >' obsahující základní třídu\<classname > "</span><span class="sxs-lookup"><span data-stu-id="39206-102">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>
<span data-ttu-id="39206-103">Odkaz vyžadoval sestavení '\<assemblyname >' obsahující základní třídu\<classname >'.</span><span class="sxs-lookup"><span data-stu-id="39206-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="39206-104">Přidejte jej do projektu.</span><span class="sxs-lookup"><span data-stu-id="39206-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="39206-105">Je třída definovaná v dynamická knihovna (DLL) nebo sestavení, které není přímo odkazován ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="39206-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="39206-106">Kompilátor jazyka Visual Basic vyžaduje přidání odkazu na-li předejít nejednoznačnosti v případě, že je třída definovaná ve více než jedna knihovna DLL nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="39206-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="39206-107">**ID chyby:** BC30007</span><span class="sxs-lookup"><span data-stu-id="39206-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39206-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="39206-108">To correct this error</span></span>  
  
- <span data-ttu-id="39206-109">Zahrnout název neodkazovaná sestavení nebo knihovny DLL odkazy projektu.</span><span class="sxs-lookup"><span data-stu-id="39206-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39206-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39206-110">See also</span></span>

- [<span data-ttu-id="39206-111">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="39206-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="39206-112">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="39206-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
