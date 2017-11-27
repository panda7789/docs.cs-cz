---
title: "-target (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4666f0305fc2de35c1fa594ccef3dd3a64c0f67c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="target-c-compiler-options"></a><span data-ttu-id="ae0ee-102">/target (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ae0ee-102">/target (C# Compiler Options)</span></span>
<span data-ttu-id="ae0ee-103">**/Target** – možnost kompilátoru lze zadat v jedné ze čtyř podob:</span><span class="sxs-lookup"><span data-stu-id="ae0ee-103">The **/target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="ae0ee-104">/ target: appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="ae0ee-104">/target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="ae0ee-105">Chcete-li vytvořit soubor .exe pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="ae0ee-106">/ target: exe</span><span class="sxs-lookup"><span data-stu-id="ae0ee-106">/target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="ae0ee-107">Chcete-li vytvořit soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="ae0ee-108">/ target: library</span><span class="sxs-lookup"><span data-stu-id="ae0ee-108">/target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="ae0ee-109">K vytvoření knihovny kódu.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="ae0ee-110">/ target: module</span><span class="sxs-lookup"><span data-stu-id="ae0ee-110">/target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="ae0ee-111">Chcete-li vytvořit modul.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-111">To create a module.</span></span>  
  
 [<span data-ttu-id="ae0ee-112">/ target: winexe</span><span class="sxs-lookup"><span data-stu-id="ae0ee-112">/target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="ae0ee-113">K vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="ae0ee-114">/ target: winmdobj</span><span class="sxs-lookup"><span data-stu-id="ae0ee-114">/target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="ae0ee-115">Vytvořit soubor zprostředkující .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="ae0ee-116">Pokud nezadáte **/target: Module**, **/target** způsobí umístit do výstupního souboru manifestu sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-116">Unless you specify **/target:module**, **/target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="ae0ee-117">Další informace najdete v tématu [sestavení v modulu Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) a [běžné atributy](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ae0ee-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="ae0ee-118">Manifest sestavení je umístěn v první výstupní soubor .exe v kompilace nebo v první knihovny DLL, pokud není dostupný žádný výstupní soubor .exe.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="ae0ee-119">Například v příkazovém řádku následující manifest bude uložena v umístění `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="ae0ee-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="ae0ee-120">Kompilátor vytvoří pouze jeden manifest sestavení kompilace.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="ae0ee-121">Informace o všechny soubory v kompilaci je umístěn v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="ae0ee-122">Všechny soubory kromě těch vytvořené pomocí výstup **/target: Module** může obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-122">All output files except those created with **/target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="ae0ee-123">Při vytváření více výstupních souborů na příkazovém řádku, lze vytvořit pouze jeden manifest sestavení a musí být umístěn do prvního výstupního souboru zadat na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="ae0ee-124">Bez ohledu na to, co je první výstupní soubor (**/target: exe**, **/target: winexe**, **/target: library** nebo **/target: Module**) ani jiné výstupní soubory vytvořené ve stejné kompilaci musí být moduly (**/target: Module**).</span><span class="sxs-lookup"><span data-stu-id="ae0ee-124">No matter what the first output file is (**/target:exe**, **/target:winexe**, **/target:library** or **/target:module**), any other output files produced in the same compilation must be modules (**/target:module**).</span></span>  
  
 <span data-ttu-id="ae0ee-125">Pokud vytvoříte sestavení, můžete určit, že nebo jeho část kódu je kompatibilní se specifikací CLS <xref:System.CLSCompliantAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="ae0ee-126">Další informace o nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae0ee-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0ee-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae0ee-127">See Also</span></span>  
 [<span data-ttu-id="ae0ee-128">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ae0ee-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ae0ee-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ae0ee-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="ae0ee-130">/ subsystemversion (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ae0ee-130">/subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
