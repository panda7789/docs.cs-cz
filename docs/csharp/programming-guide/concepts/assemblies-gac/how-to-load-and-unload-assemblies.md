---
title: 'Postupy: Zavedení a uvolnění sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 0ff3c494b40650da1e30e111b2e7f916e249d78a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748749"
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="8d045-102">Postupy: Zavedení a uvolnění sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="8d045-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="8d045-103">Sestavení odkazuje váš program bude automaticky načtených v okamžiku sestavení, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="8d045-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="8d045-104">Další informace najdete v tématu [jak: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="8d045-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="8d045-105">Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují.</span><span class="sxs-lookup"><span data-stu-id="8d045-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="8d045-106">I v případě, sestavení dostane mimo rozsah, zůstane soubor skutečné sestavení načteno, dokud jsou uvolněna, všechny aplikační domény, které obsahují.</span><span class="sxs-lookup"><span data-stu-id="8d045-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="8d045-107">Pokud chcete uvolnit, některá sestavení, ale ne pro jiné, zvažte vytvoření nové aplikační doméně, spouštění kódu v této doméně a pak uvolnění této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d045-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="8d045-108">Další informace najdete v tématu [jak: Uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="8d045-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="8d045-109">Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8d045-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="8d045-110">Použijte jednu z několik načíst metody obsažené v třídách <xref:System.AppDomain> a <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="8d045-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="8d045-111">Další informace najdete v tématu [jak: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="8d045-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="8d045-112">K uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8d045-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="8d045-113">Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují.</span><span class="sxs-lookup"><span data-stu-id="8d045-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="8d045-114">Použití `Unload` metodu z <xref:System.AppDomain> uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d045-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="8d045-115">Další informace najdete v tématu [jak: Uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="8d045-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d045-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d045-116">See also</span></span>

- [<span data-ttu-id="8d045-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8d045-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8d045-118">Sestavení v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="8d045-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="8d045-119">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8d045-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
