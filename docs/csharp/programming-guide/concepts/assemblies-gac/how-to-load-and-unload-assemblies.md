---
title: 'Postupy: Zavedení a uvolnění sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 52f7173efe497ab286c607db681f256983adc077
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342034"
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="6b0b5-102">Postupy: Zavedení a uvolnění sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="6b0b5-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="6b0b5-103">Sestavení odkazuje váš program bude automaticky načtených v okamžiku sestavení, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="6b0b5-104">Další informace najdete v tématu [jak: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="6b0b5-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="6b0b5-105">Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="6b0b5-106">I v případě, sestavení dostane mimo rozsah, zůstane soubor skutečné sestavení načteno, dokud jsou uvolněna, všechny aplikační domény, které obsahují.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="6b0b5-107">Pokud chcete uvolnit, některá sestavení, ale ne pro jiné, zvažte vytvoření nové aplikační doméně, spouštění kódu v této doméně a pak uvolnění této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="6b0b5-108">Další informace najdete v tématu [jak: Uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="6b0b5-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="6b0b5-109">Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6b0b5-109">To load an assembly into an application domain</span></span>  
  
1. <span data-ttu-id="6b0b5-110">Použijte jednu z několik načíst metody obsažené v třídách <xref:System.AppDomain> a <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="6b0b5-111">Další informace najdete v tématu [jak: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="6b0b5-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="6b0b5-112">K uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6b0b5-112">To unload an application domain</span></span>  
  
1. <span data-ttu-id="6b0b5-113">Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="6b0b5-114">Použití `Unload` metodu z <xref:System.AppDomain> uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b0b5-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="6b0b5-115">Další informace najdete v tématu [jak: Uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="6b0b5-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b0b5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b0b5-116">See also</span></span>

- [<span data-ttu-id="6b0b5-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6b0b5-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6b0b5-118">Sestavení v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="6b0b5-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="6b0b5-119">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6b0b5-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
