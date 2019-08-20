---
title: -Target (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 0630639433aed4c8dfddbf0144e9802ed3f4ee73
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606446"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="0ce55-102">-Target (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="0ce55-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="0ce55-103">Možnost kompilátoru **-target** lze zadat v jednom ze čtyř forem:</span><span class="sxs-lookup"><span data-stu-id="0ce55-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="0ce55-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="0ce55-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="0ce55-105">Pro vytvoření souboru. exe pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="0ce55-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="0ce55-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="0ce55-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="0ce55-107">Pro vytvoření souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="0ce55-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="0ce55-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="0ce55-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="0ce55-109">Chcete-li vytvořit knihovnu kódu.</span><span class="sxs-lookup"><span data-stu-id="0ce55-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="0ce55-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="0ce55-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="0ce55-111">Vytvořit modul.</span><span class="sxs-lookup"><span data-stu-id="0ce55-111">To create a module.</span></span>  
  
 [<span data-ttu-id="0ce55-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="0ce55-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="0ce55-113">Pro vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0ce55-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="0ce55-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="0ce55-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="0ce55-115">Pro vytvoření zprostředkujícího souboru. winmdobj.</span><span class="sxs-lookup"><span data-stu-id="0ce55-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="0ce55-116">Pokud nezadáte **cíl: modul**, **-target** způsobí umístění manifestu .NET Framework sestavení do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0ce55-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="0ce55-117">Další informace naleznete v tématu [sestavení v modulu CLR (Common Language Runtime)](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) a [běžné atributy](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0ce55-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="0ce55-118">Manifest sestavení je umístěn v prvním výstupním souboru. exe v kompilaci nebo v první knihovně DLL, pokud není k dispozici výstupní soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="0ce55-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="0ce55-119">Například v následujícím příkazovém řádku bude manifest umístěn v `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="0ce55-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="0ce55-120">Kompilátor vytvoří pro každou kompilaci pouze jeden manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ce55-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="0ce55-121">Informace o všech souborech v kompilaci jsou umístěny v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ce55-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="0ce55-122">Všechny výstupní soubory kromě těch, které byly vytvořeny pomocí **-target: modul** může obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ce55-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="0ce55-123">Při vytváření více výstupních souborů na příkazovém řádku lze vytvořit pouze jeden manifest sestavení a musí přejít do prvního výstupního souboru zadaného v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0ce55-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="0ce55-124">Bez ohledu na to, co je první výstupní soubor ( **-target: exe**, **-target: winexe**, **-target: Library** nebo **-target: Module**), všechny ostatní výstupní soubory vytvořené ve stejné kompilaci musí být moduly ( **-target: Module**).</span><span class="sxs-lookup"><span data-stu-id="0ce55-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="0ce55-125">Pokud vytvoříte sestavení, můžete určit, že veškerý nebo část kódu je kompatibilní se specifikací CLS s <xref:System.CLSCompliantAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="0ce55-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="0ce55-126">Další informace o tom, jak nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.ProjectProperties3.OutputType%2A>, najdete v tématu.</span><span class="sxs-lookup"><span data-stu-id="0ce55-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce55-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ce55-127">See also</span></span>

- [<span data-ttu-id="0ce55-128">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0ce55-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0ce55-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0ce55-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="0ce55-130">-subsystemversion (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="0ce55-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
