---
title: -Target (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 80cec001b27000e71b74f380a0f33e30602c01af
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473906"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="dfa45-102">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="dfa45-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="dfa45-103">Možnost kompilátoru **-target** lze zadat v jednom z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="dfa45-103">The **-target** compiler option can be specified in one of the following forms:</span></span>  
  
 [<span data-ttu-id="dfa45-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="dfa45-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="dfa45-105">Pro vytvoření souboru. exe pro aplikace Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="dfa45-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="dfa45-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="dfa45-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="dfa45-107">Pro vytvoření souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="dfa45-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="dfa45-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="dfa45-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="dfa45-109">Chcete-li vytvořit knihovnu kódu.</span><span class="sxs-lookup"><span data-stu-id="dfa45-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="dfa45-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="dfa45-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="dfa45-111">Vytvořit modul.</span><span class="sxs-lookup"><span data-stu-id="dfa45-111">To create a module.</span></span>  
  
 [<span data-ttu-id="dfa45-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="dfa45-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="dfa45-113">Pro vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="dfa45-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="dfa45-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="dfa45-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="dfa45-115">Pro vytvoření zprostředkujícího souboru. winmdobj.</span><span class="sxs-lookup"><span data-stu-id="dfa45-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="dfa45-116">Pokud nezadáte **cíl: modul**, **-target** způsobí umístění manifestu .NET Framework sestavení do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="dfa45-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="dfa45-117">Další informace naleznete v tématu [sestavení v rozhraní .NET](../../../standard/assembly/index.md) a [běžné atributy](../attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="dfa45-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="dfa45-118">Manifest sestavení je umístěn v prvním výstupním souboru. exe v kompilaci nebo v první knihovně DLL, pokud není k dispozici výstupní soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="dfa45-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="dfa45-119">Například v následujícím příkazovém řádku bude manifest umístěn v `1.exe` :</span><span class="sxs-lookup"><span data-stu-id="dfa45-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="dfa45-120">Kompilátor vytvoří pro každou kompilaci pouze jeden manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfa45-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="dfa45-121">Informace o všech souborech v kompilaci jsou umístěny v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfa45-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="dfa45-122">Všechny výstupní soubory kromě těch, které byly vytvořeny pomocí **-target: modul** může obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfa45-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="dfa45-123">Při vytváření více výstupních souborů na příkazovém řádku lze vytvořit pouze jeden manifest sestavení a musí přejít do prvního výstupního souboru zadaného v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="dfa45-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="dfa45-124">Bez ohledu na to, co je první výstupní soubor (**-target: exe**, **-target: winexe**, **-target: Library** nebo **-target: Module**), všechny ostatní výstupní soubory vytvořené ve stejné kompilaci musí být moduly (**-target: Module**).</span><span class="sxs-lookup"><span data-stu-id="dfa45-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="dfa45-125">Pokud vytvoříte sestavení, můžete určit, že veškerý nebo část kódu je kompatibilní se specifikací CLS s <xref:System.CLSCompliantAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="dfa45-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="dfa45-126">Další informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="dfa45-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa45-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfa45-127">See also</span></span>

- [<span data-ttu-id="dfa45-128">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="dfa45-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dfa45-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="dfa45-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="dfa45-130">-subsystemversion (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="dfa45-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
