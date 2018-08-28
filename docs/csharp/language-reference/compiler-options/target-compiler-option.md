---
title: -target (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 7736b8850a7b09f7212e83e05acf0e1994bce0fe
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000001"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="04ff8-102">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="04ff8-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="04ff8-103">**-Target** – možnost kompilátoru je zadat v jednom ze čtyř formuláře:</span><span class="sxs-lookup"><span data-stu-id="04ff8-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="04ff8-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="04ff8-104">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="04ff8-105">Chcete-li vytvořit soubor s příponou .exe pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="04ff8-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="04ff8-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="04ff8-106">-target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="04ff8-107">Chcete-li vytvořit soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="04ff8-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="04ff8-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="04ff8-108">-target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="04ff8-109">Pro vytvoření knihovny kódu.</span><span class="sxs-lookup"><span data-stu-id="04ff8-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="04ff8-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="04ff8-110">-target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="04ff8-111">Jak vytvořit modul.</span><span class="sxs-lookup"><span data-stu-id="04ff8-111">To create a module.</span></span>  
  
 [<span data-ttu-id="04ff8-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="04ff8-112">-target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="04ff8-113">K vytvoření programu Windows.</span><span class="sxs-lookup"><span data-stu-id="04ff8-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="04ff8-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="04ff8-114">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="04ff8-115">Chcete-li vytvořit přechodného souboru .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="04ff8-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="04ff8-116">Pokud nezadáte **-target: module**, **-target** způsobí, že budou umístěny ve výstupním souboru manifestu sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04ff8-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="04ff8-117">Další informace najdete v tématu [sestavení v modulu Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) a [společné atributy](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="04ff8-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="04ff8-118">Manifest sestavení je umístěn v první výstupní soubor .exe v kompilaci nebo v rámci DLL. první, pokud neexistuje žádný výstupní soubor .exe.</span><span class="sxs-lookup"><span data-stu-id="04ff8-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="04ff8-119">Například v příkazovém řádku následující manifest budou umístěny v `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="04ff8-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="04ff8-120">Kompilátor vytvoří jenom jeden manifest sestavení za kompilace.</span><span class="sxs-lookup"><span data-stu-id="04ff8-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="04ff8-121">Informace o všech souborech v kompilaci je umístěn v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="04ff8-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="04ff8-122">Všechny výstupní soubory s výjimkou těch, vytvořené pomocí **-target: module** může obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="04ff8-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="04ff8-123">Při vytváření několika výstupních souborů na příkazovém řádku, je možné vytvořit pouze jeden manifest sestavení a musí přejít do první výstupní soubor zadán v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="04ff8-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="04ff8-124">Bez ohledu na to, co je první výstupní soubor (**-target: exe**, **-target: winexe**, **-target: library** nebo **-target: module**) ani jiné výstupní soubory vytvořené ve stejné kompilaci musí být moduly (**-target: module**).</span><span class="sxs-lookup"><span data-stu-id="04ff8-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="04ff8-125">Pokud vytvoříte sestavení, můžete určit, že všechny nebo část kódu je kompatibilní se Specifikací CLS se <xref:System.CLSCompliantAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="04ff8-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="04ff8-126">Další informace o nastavení této možnosti kompilátoru prostřednictvím kódu programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="04ff8-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ff8-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="04ff8-127">See Also</span></span>  
 [<span data-ttu-id="04ff8-128">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="04ff8-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="04ff8-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="04ff8-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="04ff8-130">-subsystemversion (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="04ff8-130">-subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
