---
description: -Reference (možnosti kompilátoru C#)
title: -Reference (možnosti kompilátoru C#)
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
ms.openlocfilehash: 7b84953f85545c0400c7136c258849f259e8b48a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124796"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="e64c7-103">-Reference (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="e64c7-103">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="e64c7-104">Možnost **-reference** způsobí, že kompilátor importuje informace o [veřejném](../keywords/public.md) typu do zadaného souboru do aktuálního projektu, takže umožňuje odkazovat na metadata ze zadaných souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-104">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64c7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e64c7-105">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e64c7-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e64c7-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="e64c7-107">Název souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-107">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="e64c7-108">Chcete-li importovat více než jeden soubor, zahrňte možnost samostatného **odkazu** pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="e64c7-108">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="e64c7-109">Platný identifikátor jazyka C#, který bude představovat kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-109">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e64c7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e64c7-110">Remarks</span></span>  
 <span data-ttu-id="e64c7-111">Chcete-li importovat z více než jednoho souboru, zahrňte možnost **-reference** pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="e64c7-111">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="e64c7-112">Soubory, které importujete, musí obsahovat manifest; výstupní soubor musí být zkompilován s jednou z možností [TARGETu](./target-compiler-option.md) s výjimkou [target: Module](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e64c7-112">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e64c7-113">**-r** je krátká forma **reference**.</span><span class="sxs-lookup"><span data-stu-id="e64c7-113">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="e64c7-114">Pomocí [-addmodule –](./addmodule-compiler-option.md) importujte metadata z výstupního souboru, který neobsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-114">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="e64c7-115">Pokud odkazujete na sestavení (sestavení A), které odkazuje na jiné sestavení (sestavení B), budete muset odkazovat na sestavení B, pokud:</span><span class="sxs-lookup"><span data-stu-id="e64c7-115">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="e64c7-116">Typ, který použijete ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="e64c7-116">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="e64c7-117">Vyvoláte pole, vlastnost, událost nebo metodu, které mají návratový typ nebo typ parametru ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="e64c7-117">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="e64c7-118">Pomocí [-lib](./lib-compiler-option.md) Určete adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-118">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="e64c7-119">Téma **-lib** také popisuje adresáře, ve kterých kompilátor vyhledává sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-119">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="e64c7-120">Aby mohl kompilátor rozpoznat typ v sestavení a ne v modulu, musí být vynucen přeložit typ, který lze provést definováním instance typu.</span><span class="sxs-lookup"><span data-stu-id="e64c7-120">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="e64c7-121">Existují i jiné způsoby, jak přeložit názvy typů v sestavení pro kompilátor: například Pokud převezmete z typu v sestavení, název typu bude rozpoznán kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="e64c7-121">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="e64c7-122">V některých případech je nutné odkazovat na dvě různé verze stejné komponenty z jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-122">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="e64c7-123">Uděláte to tak, že pro každý soubor použijete dílčí možnost alias na přepínač **-reference** pro jednotlivé soubory, abyste je rozlišili mezi těmito dvěma soubory.</span><span class="sxs-lookup"><span data-stu-id="e64c7-123">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="e64c7-124">Tento alias bude použit jako kvalifikátor pro název součásti a bude přeložen na součást v jednom ze souborů.</span><span class="sxs-lookup"><span data-stu-id="e64c7-124">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="e64c7-125">Ve výchozím nastavení se používá soubor odpovědí csc (. rsp), který odkazuje na běžně používaná .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="e64c7-125">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="e64c7-126">Pokud nechcete, aby kompilátor používal CSc. rsp, použijte [-li konfiguraci](./noconfig-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="e64c7-126">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e64c7-127">V aplikaci Visual Studio, použijte dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="e64c7-127">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="e64c7-128">Další informace najdete v tématu [Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="e64c7-128">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="e64c7-129">Chcete-li zajistit ekvivalentní chování mezi přidáním odkazů pomocí `-reference` a přidáním odkazů pomocí dialogového okna **Přidat odkaz** , nastavte vlastnost **Embed Interop Types** na **hodnotu false** pro sestavení, které přidáváte.</span><span class="sxs-lookup"><span data-stu-id="e64c7-129">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="e64c7-130">**True** je výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e64c7-130">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e64c7-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="e64c7-131">Example</span></span>  
 <span data-ttu-id="e64c7-132">Tento příklad ukazuje, jak použít funkci [extern alias](../keywords/extern-alias.md) .</span><span class="sxs-lookup"><span data-stu-id="e64c7-132">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="e64c7-133">Zdrojový soubor zkompilujete a naimportujete metadata z `grid.dll` a `grid20.dll` , které byly zkompilovány dříve.</span><span class="sxs-lookup"><span data-stu-id="e64c7-133">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="e64c7-134">Tyto dvě knihovny DLL obsahují samostatné verze stejné komponenty a k zkompilování zdrojového souboru použijete dva **odkazy** s možnostmi aliasu.</span><span class="sxs-lookup"><span data-stu-id="e64c7-134">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="e64c7-135">Možnosti vypadají takto:</span><span class="sxs-lookup"><span data-stu-id="e64c7-135">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="e64c7-136">Tím se nastaví externí aliasy `GridV1` a `GridV2` , které v programu použijete, prostřednictvím `extern` příkazu:</span><span class="sxs-lookup"><span data-stu-id="e64c7-136">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="e64c7-137">Až to uděláte, můžete odkazovat na ovládací prvek mřížky z `grid.dll` pomocí předpony názvu ovládacího prvku, například takto `GridV1` :</span><span class="sxs-lookup"><span data-stu-id="e64c7-137">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="e64c7-138">Kromě toho můžete odkazovat na ovládací prvek mřížky z `grid20.dll` pomocí předpony názvu ovládacího prvku `GridV2` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e64c7-138">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="e64c7-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e64c7-139">See also</span></span>

- [<span data-ttu-id="e64c7-140">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="e64c7-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e64c7-141">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e64c7-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
