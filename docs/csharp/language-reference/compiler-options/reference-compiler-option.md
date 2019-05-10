---
title: -reference (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /reference
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
ms.openlocfilehash: fbf93a87cede753ebd41c148f4fb4bb761846954
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593087"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="d3652-102">-reference (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d3652-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="d3652-103">**– Referenční dokumentace** možnost způsobí, že kompilátor importovat [veřejné](../../../csharp/language-reference/keywords/public.md) zadávat informace do zadaného souboru do aktuálního projektu, což umožní k odkazování na metadata ze zadaných souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-103">The **-reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3652-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3652-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3652-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3652-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d3652-106">Název souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="d3652-107">Pokud chcete importovat více než jeden soubor, zahrnují samostatný **-odkaz** možnost pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="d3652-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="d3652-108">Platným identifikátorem C#, která bude představovat kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3652-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3652-109">Remarks</span></span>  
 <span data-ttu-id="d3652-110">Pokud chcete importovat z více než jeden soubor, zahrňte **– referenční dokumentace** možnost pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="d3652-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="d3652-111">Soubory, které importujete, musí obsahovat manifest; výstupní soubor musí být zkompilovány s jedním z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možností jiných než [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d3652-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="d3652-112">**-r** je zkratka pro **– referenční dokumentace**.</span><span class="sxs-lookup"><span data-stu-id="d3652-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="d3652-113">Použití [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) importovat metadata z výstupního souboru, který nebude obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-113">Use [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="d3652-114">Pokud odkazujete na sestavení (sestavení A), který odkazuje na jiné sestavení (sestavení B), budete muset odkaz na sestavení B pokud:</span><span class="sxs-lookup"><span data-stu-id="d3652-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="d3652-115">Typ, který používáte v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="d3652-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="d3652-116">Vyvolání pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="d3652-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="d3652-117">Použití [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) určit adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-117">Use [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="d3652-118">**-Lib** téma také popisuje adresáře, ve kterých kompilátor hledá sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="d3652-119">Aby kompilátor rozpoznával typ v sestavení a ne v modulu je potřeba jej donutit k přeložení typu, což lze provést definováním instance typu.</span><span class="sxs-lookup"><span data-stu-id="d3652-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="d3652-120">Existují jiné způsoby přeložení názvů typů v sestavení pro kompilátor: například, pokud je zděděn z typu v sestavení, název typu se pak být rozpoznatelným kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="d3652-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="d3652-121">Někdy je potřeba odkazují na dvě různé verze stejné součásti v rámci jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="d3652-122">K tomuto účelu použít na přepínači alias **– referenční dokumentace** pro každý soubor k rozlišení mezi dvěma soubory.</span><span class="sxs-lookup"><span data-stu-id="d3652-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="d3652-123">Tento alias se použije jako kvalifikátor pro název komponenty a vyřeší do komponenty v jednom souboru.</span><span class="sxs-lookup"><span data-stu-id="d3652-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="d3652-124">Csc soubor odpovědí (.rsp), který se odkazuje na běžně používá sestavení rozhraní .NET Framework, se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d3652-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="d3652-125">Použít [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Pokud nechcete, aby kompilátor používal csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="d3652-125">Use [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3652-126">V sadě Visual Studio, použijte **přidat odkaz** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d3652-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="d3652-127">Další informace najdete v tématu [jak: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="d3652-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="d3652-128">K zajištění ekvivalentní chování mezi přidání odkazů pomocí `-reference` a přidání odkazů pomocí **přidat odkaz** dialogové okno, nastavte **Embed Interop Types** vlastnost **False** pro sestavení, které přidáte.</span><span class="sxs-lookup"><span data-stu-id="d3652-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="d3652-129">**Hodnota TRUE** je výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d3652-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3652-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3652-130">Example</span></span>  
 <span data-ttu-id="d3652-131">Tento příklad ukazuje způsob použití [externí alias](../../../csharp/language-reference/keywords/extern-alias.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="d3652-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="d3652-132">Kompilaci zdrojového souboru a import metadat od `grid.dll` a `grid20.dll`, které již byly zkompilovány dříve.</span><span class="sxs-lookup"><span data-stu-id="d3652-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="d3652-133">Dvě knihovny DLL obsahovat samostatné verze stejné součásti a použijete dvě **– referenční dokumentace** s možnostmi alias pro kompilaci zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="d3652-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="d3652-134">Možnosti vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="d3652-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="d3652-135">Tím se nastaví externích aliasů `GridV1` a `GridV2`, který používáte ve svém programu prostřednictvím `extern` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="d3652-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="d3652-136">Až to uděláte, můžete odkazovat na ovládací prvek mřížky z `grid.dll` vložením prefixu název ovládacího prvku s `GridV1`, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="d3652-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="d3652-137">Kromě toho můžete odkazovat na ovládací prvek mřížky z `grid20.dll` vložením prefixu název ovládacího prvku s `GridV2` tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="d3652-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="d3652-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3652-138">See also</span></span>

- [<span data-ttu-id="d3652-139">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d3652-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="d3652-140">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="d3652-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
