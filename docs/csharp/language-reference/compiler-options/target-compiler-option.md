---
title: -target (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: ea5481810e629d911c4d5aba62e60c98d0783f34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644348"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="b71f7-102">-target (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b71f7-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="b71f7-103">Možnost kompilátoru **-target** lze zadat v jednom ze čtyř formulářů:</span><span class="sxs-lookup"><span data-stu-id="b71f7-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="b71f7-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="b71f7-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="b71f7-105">Vytvoření souboru EXE pro aplikace pro Windows 8.x Store.</span><span class="sxs-lookup"><span data-stu-id="b71f7-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="b71f7-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="b71f7-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="b71f7-107">Vytvoření souboru EXE.</span><span class="sxs-lookup"><span data-stu-id="b71f7-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="b71f7-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="b71f7-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="b71f7-109">Chcete-li vytvořit knihovnu kódu.</span><span class="sxs-lookup"><span data-stu-id="b71f7-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="b71f7-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="b71f7-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="b71f7-111">Chcete-li vytvořit modul.</span><span class="sxs-lookup"><span data-stu-id="b71f7-111">To create a module.</span></span>  
  
 [<span data-ttu-id="b71f7-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="b71f7-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="b71f7-113">Vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b71f7-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="b71f7-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="b71f7-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="b71f7-115">Chcete-li vytvořit zprostředkující soubor .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="b71f7-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="b71f7-116">Pokud nezadáte **-target:module**, **-target** způsobí, že manifest sestavení rozhraní .NET Framework bude umístěn do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="b71f7-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="b71f7-117">Další informace naleznete [v tématech Sestavení v rozhraní .NET](../../../standard/assembly/index.md) a [Common Attributes](../attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="b71f7-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="b71f7-118">Manifest sestavení je umístěn v prvním výstupním souboru EXE v kompilaci nebo v první dll, pokud neexistuje žádný výstupní soubor EXE.</span><span class="sxs-lookup"><span data-stu-id="b71f7-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="b71f7-119">Například v následujícím příkazovém řádku bude `1.exe`manifest umístěn do :</span><span class="sxs-lookup"><span data-stu-id="b71f7-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="b71f7-120">Kompilátor vytvoří pouze jeden manifest sestavení na kompilaci.</span><span class="sxs-lookup"><span data-stu-id="b71f7-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="b71f7-121">Informace o všech souborech v kompilaci jsou umístěny v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b71f7-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="b71f7-122">Všechny výstupní soubory s výjimkou těch, které byly vytvořeny pomocí **modulu -target:module,** mohou obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="b71f7-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="b71f7-123">Při vytváření více výstupních souborů na příkazovém řádku lze vytvořit pouze jeden manifest sestavení a musí přejít do prvního výstupního souboru určeného na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b71f7-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="b71f7-124">Bez ohledu na to, co je první výstupní soubor (**-target:exe**, **-target:winexe**, **-target:library** nebo **-target:module**), musí být všechny ostatní výstupní soubory vytvořené ve stejné kompilaci moduly (**-target:module**).</span><span class="sxs-lookup"><span data-stu-id="b71f7-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="b71f7-125">Pokud vytvoříte sestavení, můžete označit, že celý kód nebo jeho <xref:System.CLSCompliantAttribute> část je kompatibilní s atributem CLS.</span><span class="sxs-lookup"><span data-stu-id="b71f7-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="b71f7-126">Další informace o programovém nastavení této <xref:VSLangProj80.ProjectProperties3.OutputType%2A>možnosti kompilátoru naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="b71f7-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71f7-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b71f7-127">See also</span></span>

- [<span data-ttu-id="b71f7-128">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b71f7-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b71f7-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b71f7-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="b71f7-130">-subsystemversion (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b71f7-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
