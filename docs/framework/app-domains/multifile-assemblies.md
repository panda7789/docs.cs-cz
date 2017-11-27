---
title: "Vícesouborová sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fead0a944b464ffd8f72dca6da33fd97404fe2d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="multifile-assemblies"></a><span data-ttu-id="47de5-102">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="47de5-102">Multifile Assemblies</span></span>
<span data-ttu-id="47de5-103">Můžete vytvořit vícesouborového sestavení s využitím kompilátory příkazového řádku nebo [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] s Visual C++.</span><span class="sxs-lookup"><span data-stu-id="47de5-103">You can create multifile assemblies using command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] with Visual C++.</span></span> <span data-ttu-id="47de5-104">Manifest sestavení musí obsahovat jeden soubor v sestavení.</span><span class="sxs-lookup"><span data-stu-id="47de5-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="47de5-105">Sestavení, které spustí aplikaci musí také obsahovat vstupní bod, jako je například Main nebo WinMain – metoda.</span><span class="sxs-lookup"><span data-stu-id="47de5-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>  
  
 <span data-ttu-id="47de5-106">Předpokládejme například, že máte aplikaci, která obsahuje dva moduly kódu, Client.cs a Stringer.cs.</span><span class="sxs-lookup"><span data-stu-id="47de5-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="47de5-107">Vytvoří Stringer.cs `myStringer` obor názvů, který je odkazován objektem kód v Client.cs.</span><span class="sxs-lookup"><span data-stu-id="47de5-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="47de5-108">Client.cs obsahuje `Main` metoda, která je vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="47de5-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="47de5-109">V tomto příkladu zkompilovat dva moduly kódu a pak vytvořte třetí soubor, který obsahuje manifest sestavení, který spouští aplikace.</span><span class="sxs-lookup"><span data-stu-id="47de5-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="47de5-110">Manifest sestavení odkazuje oba `Client` a `Stringer` moduly.</span><span class="sxs-lookup"><span data-stu-id="47de5-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47de5-111">Vícesouborová sestavení může mít pouze jeden vstupní bod, i když sestavení má více modulů kódu.</span><span class="sxs-lookup"><span data-stu-id="47de5-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>  
  
 <span data-ttu-id="47de5-112">Tady je několik důvodů, které že můžete vytvořit vícesouborového sestavení:</span><span class="sxs-lookup"><span data-stu-id="47de5-112">There are several reasons you might want to create a multifile assembly:</span></span>  
  
-   <span data-ttu-id="47de5-113">Kombinování moduly, které jsou napsané v různých jazycích.</span><span class="sxs-lookup"><span data-stu-id="47de5-113">To combine modules written in different languages.</span></span> <span data-ttu-id="47de5-114">Toto je nejběžnější důvod pro vytváření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="47de5-114">This is the most common reason for creating a multifile assembly.</span></span>  
  
-   <span data-ttu-id="47de5-115">Chcete-li optimalizovat stahování aplikace umístěním zřídka používaný typů v modulu, který byl stažen pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="47de5-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="47de5-116">Pokud vytváříte aplikace, které budou staženy pomocí `<object>` značky s Microsoft Internet Explorer, je důležité vytvořit vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="47de5-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="47de5-117">V tomto scénáři vytvoříte soubor odděleně od moduly kódu, které obsahuje pouze manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="47de5-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="47de5-118">Internet Explorer nejprve stáhne manifest sestavení a pak vytvoří pracovní vlákna ke stažení všechny další moduly nebo sestavení požadovaná.</span><span class="sxs-lookup"><span data-stu-id="47de5-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="47de5-119">Při stažení souboru, který obsahuje manifest sestavení aplikace Internet Explorer bude reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="47de5-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="47de5-120">Menší soubor obsahuje manifest sestavení, méně času aplikace Internet Explorer bude reagovat.</span><span class="sxs-lookup"><span data-stu-id="47de5-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>  
  
-   <span data-ttu-id="47de5-121">Kombinování moduly kódu napsaných několika vývojáři.</span><span class="sxs-lookup"><span data-stu-id="47de5-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="47de5-122">I když každý vývojář může zkompilovat každý modul kódu do sestavení, tato vynutí některé typy mají být exponovány veřejně, které nejsou vystaveny, pokud všechny moduly jsou vloženy do vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="47de5-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>  
  
 <span data-ttu-id="47de5-123">Jakmile vytvoříte sestavení, můžete si soubor, který obsahuje manifest sestavení (a tím i sestavení), nebo můžete poskytnout silným názvem souboru (a sestavení) a umístí jej v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="47de5-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47de5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="47de5-124">See Also</span></span>  
 [<span data-ttu-id="47de5-125">Postupy: vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="47de5-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="47de5-126">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="47de5-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
