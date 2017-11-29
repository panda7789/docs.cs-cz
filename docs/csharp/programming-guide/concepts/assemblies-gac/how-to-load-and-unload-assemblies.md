---
title: "Postupy: zavedení a uvolnění sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="4c757-102">Postupy: zavedení a uvolnění sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="4c757-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="4c757-103">Sestavení odkazuje vašeho programu bude automaticky načíst v čase vytvoření buildu, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="4c757-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="4c757-104">Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="4c757-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="4c757-105">Neexistuje žádný způsob, jak uvolnit jednotlivých sestavení bez uvolnění všech aplikací domén, které ji obsahují.</span><span class="sxs-lookup"><span data-stu-id="4c757-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="4c757-106">I v případě, že sestavení ocitne mimo obor, skutečný sestavení soubor zůstane načíst, dokud se všechny domény aplikace, které ji obsahují odpojen.</span><span class="sxs-lookup"><span data-stu-id="4c757-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="4c757-107">Pokud chcete uvolnit některá sestavení a jiné ne, zvažte vytvoření nové domény aplikace, provádění kódu v této doméně a pak uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c757-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="4c757-108">Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="4c757-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="4c757-109">Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="4c757-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="4c757-110">Použijte jeden z několik metod, které jsou součástí třídy načíst <xref:System.AppDomain> a <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="4c757-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="4c757-111">Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="4c757-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="4c757-112">K uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="4c757-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="4c757-113">Neexistuje žádný způsob, jak uvolnit jednotlivých sestavení bez uvolnění všech aplikací domén, které ji obsahují.</span><span class="sxs-lookup"><span data-stu-id="4c757-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="4c757-114">Použití `Unload` metoda z <xref:System.AppDomain> uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c757-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="4c757-115">Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="4c757-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c757-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c757-116">See Also</span></span>  
 [<span data-ttu-id="4c757-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4c757-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4c757-118">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="4c757-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="4c757-119">Postupy: načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="4c757-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
