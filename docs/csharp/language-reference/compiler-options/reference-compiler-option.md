---
title: "-reference (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b3995cd22f50aa8a3a329b22a4fbe4e9b8ffa4ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reference-c-compiler-options"></a><span data-ttu-id="2278a-102">/reference (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="2278a-102">/reference (C# Compiler Options)</span></span>
<span data-ttu-id="2278a-103">**/Reference** možnost způsobí, že kompilátor importuje [veřejné](../../../csharp/language-reference/keywords/public.md) informací o typu do zadaného souboru do aktuálního projektu, a umožňuje odkazování na metadata ze zadaných souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-103">The **/reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2278a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2278a-104">Syntax</span></span>  
  
```console  
/reference:[alias=]filename  
/reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="2278a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2278a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2278a-106">Název souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="2278a-107">K importu více než jeden soubor, zahrnují samostatný **/reference** možnost pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="2278a-107">To import more than one file, include a separate **/reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="2278a-108">Platný C# identifikátor představující kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2278a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2278a-109">Remarks</span></span>  
 <span data-ttu-id="2278a-110">Chcete-li importovat z více než jeden soubor, zahrňte **/reference** možnost pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="2278a-110">To import from more than one file, include a **/reference** option for each file.</span></span>  
  
 <span data-ttu-id="2278a-111">Soubory, které importujete musí obsahovat manifest; výstupní soubor musí být zkompilován s jedním z [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možnosti jiné než [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2278a-111">The files you import must contain a manifest; the output file must have been compiled with one of the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="2278a-112">**/r** je zkratka pro **/reference**.</span><span class="sxs-lookup"><span data-stu-id="2278a-112">**/r** is the short form of **/reference**.</span></span>  
  
 <span data-ttu-id="2278a-113">Použití [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) Import metadat z výstupního souboru, který neobsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-113">Use [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="2278a-114">Pokud odkazujete na sestavení (sestavení A), který odkazuje na jiné sestavení (sestavení B), bude muset odkaz na sestavení B pokud:</span><span class="sxs-lookup"><span data-stu-id="2278a-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="2278a-115">Typ, který ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="2278a-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="2278a-116">Vyvolání polí, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="2278a-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="2278a-117">Použití [/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-117">Use [/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="2278a-118">**/Lib** téma také popisuje adresáře, ve kterých kompilátor vyhledává sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-118">The **/lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="2278a-119">Aby kompilátoru rozpoznat typu v sestavení a není v modulu je nutné vynutit pro vyřešení typu, což lze provést tak, že definujete instance typu.</span><span class="sxs-lookup"><span data-stu-id="2278a-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="2278a-120">Existují jiné způsoby přeložit názvy typů v sestavení pro kompilátor: například pokud jste dědí od typu v sestavení, název typu pak rozpozná pomocí kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2278a-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="2278a-121">Někdy je nezbytné k odkazování dvě různé verze stejné komponenty z v jednom sestavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="2278a-122">K tomu použít alias přepínači na **/reference** pro každý soubor k rozlišení dvou souborech.</span><span class="sxs-lookup"><span data-stu-id="2278a-122">To do this, use the alias suboption on the **/reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="2278a-123">Tento alias se použije jako kvalifikátor pro název součásti a bude odkazující na komponentu v jeden ze souborů.</span><span class="sxs-lookup"><span data-stu-id="2278a-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="2278a-124">Soubor odpovědí (.rsp) csc, jehož odkazy běžně používají sestavení rozhraní .NET Framework, se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2278a-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="2278a-125">Použít [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Pokud nechcete, aby kompilátor používal csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="2278a-125">Use [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2278a-126">V sadě Visual Studio, použijte **přidat odkaz na** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2278a-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="2278a-127">Další informace najdete v tématu [postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="2278a-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="2278a-128">Zajistit ekvivalentní chování mezi přidání odkazů pomocí `/reference` a přidání odkazů pomocí **přidat odkaz na** dialogové okno, sada **vložit zprostředkovatel komunikace s objekty typy** vlastnost **False** pro sestavení, které přidáváte.</span><span class="sxs-lookup"><span data-stu-id="2278a-128">To ensure equivalent behavior between adding references by using `/reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="2278a-129">**Hodnota TRUE,** je výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2278a-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2278a-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="2278a-130">Example</span></span>  
 <span data-ttu-id="2278a-131">Tento příklad ukazuje způsob použití [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="2278a-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="2278a-132">Kompilaci zdrojového souboru a importovat metadata z `grid.dll` a `grid20.dll`, které byly zkompilovány dříve.</span><span class="sxs-lookup"><span data-stu-id="2278a-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`,which have been compiled previously.</span></span> <span data-ttu-id="2278a-133">Tyto dvě knihovny obsahují samostatné verze stejné komponenty, a použijte dva **/reference** s možnostmi alias pro kompilaci zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="2278a-133">The two DLLs contain separate versions of the same component, and you use two **/reference** with alias options to compile the source file.</span></span> <span data-ttu-id="2278a-134">Možnosti vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="2278a-134">The options look like this:</span></span>  
  
 <span data-ttu-id="2278a-135">/Reference:GridV1=grid.dll a /reference:GridV2=grid20.dll</span><span class="sxs-lookup"><span data-stu-id="2278a-135">/reference:GridV1=grid.dll and /reference:GridV2=grid20.dll</span></span>  
  
 <span data-ttu-id="2278a-136">Toto nastaví externí aliasy "GridV1" a "GridV2", které použijete v programu prostřednictvím externího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2278a-136">This sets up the external aliases "GridV1" and "GridV2," which you use in your program by means of an extern statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="2278a-137">Až bude vše Hotovo, najdete do ovládacího prvku mřížky z grid.dll pomocí prefixu název ovládacího prvku s GridV1, například takto:</span><span class="sxs-lookup"><span data-stu-id="2278a-137">Once this is done, you can refer to the grid control from grid.dll by prefixing the control name with GridV1, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="2278a-138">Kromě toho najdete do ovládacího prvku mřížky z grid20.dll pomocí prefixu název ovládacího prvku GridV2 takto:</span><span class="sxs-lookup"><span data-stu-id="2278a-138">In addition, you can refer to the grid control from grid20.dll by prefixing the control name with GridV2 like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="2278a-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="2278a-139">See Also</span></span>  
 [<span data-ttu-id="2278a-140">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="2278a-140">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="2278a-141">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="2278a-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
