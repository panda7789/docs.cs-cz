---
title: -reference (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: 3e6a999d528be111ba2b92886f4e6e3ebf185d5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173663"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="26cc2-102">-reference (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="26cc2-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="26cc2-103">Možnost **-reference** způsobí, že kompilátor importuje informace [o veřejném](../keywords/public.md) typu v zadaném souboru do aktuálního projektu, což vám umožní odkazovat na metadata ze zadaných souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-103">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26cc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26cc2-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="26cc2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26cc2-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="26cc2-106">Název souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="26cc2-107">Chcete-li importovat více než jeden soubor, zahrňte pro každý soubor samostatnou možnost **odkazu** .</span><span class="sxs-lookup"><span data-stu-id="26cc2-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="26cc2-108">Platný identifikátor Jazyka C#, který bude představovat kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26cc2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26cc2-109">Remarks</span></span>  
 <span data-ttu-id="26cc2-110">Chcete-li importovat z více než jednoho souboru, zahrňte pro každý soubor možnost **-reference.**</span><span class="sxs-lookup"><span data-stu-id="26cc2-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="26cc2-111">Importované soubory musí obsahovat manifest; výstupní soubor musí být zkompilován s jednou z možností [-target](./target-compiler-option.md) než [-target:module](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="26cc2-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="26cc2-112">**-r** je zkrácená forma **odkazu**.</span><span class="sxs-lookup"><span data-stu-id="26cc2-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="26cc2-113">Pomocí [modulu -addmodule](./addmodule-compiler-option.md) importujte metadata z výstupního souboru, který neobsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-113">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="26cc2-114">Pokud odkazujete na sestavení (sestavení A), které odkazuje na jinou sestavu (sestavení B), budete muset odkazovat na sestavení B, pokud:</span><span class="sxs-lookup"><span data-stu-id="26cc2-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="26cc2-115">Typ, který použijete ze sestavení A dědí z typu nebo implementuje rozhraní z sestavení B.</span><span class="sxs-lookup"><span data-stu-id="26cc2-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="26cc2-116">Vyvoláte pole, vlastnost, událost nebo metodu, která má návratový typ nebo typ parametru ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="26cc2-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="26cc2-117">Použijte [-lib](./lib-compiler-option.md) k určení adresáře, ve kterém je umístěn jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-117">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="26cc2-118">Téma **-lib** také popisuje adresáře, ve kterých kompilátor hledá sestavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="26cc2-119">Aby kompilátor rozpoznal typ v sestavení a nikoli v modulu, musí být vynuceno přeložit typ, který můžete provést definováním instance typu.</span><span class="sxs-lookup"><span data-stu-id="26cc2-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="26cc2-120">Existují i jiné způsoby, jak přeložit názvy typů v sestavení pro kompilátor: například pokud dědíte z typu v sestavení, název typu pak bude rozpoznán kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="26cc2-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="26cc2-121">Někdy je nutné odkazovat na dvě různé verze stejné součásti z jedné sestavy.</span><span class="sxs-lookup"><span data-stu-id="26cc2-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="26cc2-122">Chcete-li to provést, použijte dílčí alias na **přepínači -reference** pro každý soubor k rozlišení mezi dvěma soubory.</span><span class="sxs-lookup"><span data-stu-id="26cc2-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="26cc2-123">Tento alias bude použit jako kvalifikátor pro název komponenty a bude přeložit na komponentu v jednom ze souborů.</span><span class="sxs-lookup"><span data-stu-id="26cc2-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="26cc2-124">Soubor csc response (.rsp), který odkazuje na běžně používaná sestavení rozhraní .NET Framework, se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="26cc2-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="26cc2-125">Pokud nechcete, aby kompilátor používal csc.rsp, použijte [-noconfig.](./noconfig-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="26cc2-125">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26cc2-126">V sadě Visual Studio použijte dialogové okno **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="26cc2-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="26cc2-127">Další informace naleznete v [tématu How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="26cc2-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="26cc2-128">Chcete-li zajistit ekvivalentní chování `-reference` mezi přidáváním odkazů pomocí a přidáváním odkazů pomocí dialogového okna **Přidat odkaz,** nastavte vlastnost **Embed Interop Types** na **False** pro sestavení, které přidáváte.</span><span class="sxs-lookup"><span data-stu-id="26cc2-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="26cc2-129">**True** je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26cc2-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26cc2-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="26cc2-130">Example</span></span>  
 <span data-ttu-id="26cc2-131">Tento příklad ukazuje, jak používat funkci [aliasu extern.](../keywords/extern-alias.md)</span><span class="sxs-lookup"><span data-stu-id="26cc2-131">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="26cc2-132">Zkompilovat zdrojový soubor `grid.dll` a `grid20.dll`import metadat z a , které byly zkompilovány dříve.</span><span class="sxs-lookup"><span data-stu-id="26cc2-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="26cc2-133">Dvě knihovny DLL obsahují samostatné verze stejné součásti a ke kompilaci zdrojového souboru použijete dva **odkazy** s možnostmi aliasu.</span><span class="sxs-lookup"><span data-stu-id="26cc2-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="26cc2-134">Možnosti vypadají takto:</span><span class="sxs-lookup"><span data-stu-id="26cc2-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="26cc2-135">Tím nastavíte externí `GridV1` `GridV2`aliasy a , které používáte `extern` v programu pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="26cc2-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="26cc2-136">Jakmile je to hotovo, můžete odkazovat `grid.dll` na mřížku ovládacího prvku z předponou název ovládacího prvku s `GridV1`, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="26cc2-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="26cc2-137">Kromě toho můžete odkazovat na `grid20.dll` ovládací prvek mřížky `GridV2` z předponou název ovládacího prvku takto:</span><span class="sxs-lookup"><span data-stu-id="26cc2-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="26cc2-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="26cc2-138">See also</span></span>

- [<span data-ttu-id="26cc2-139">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="26cc2-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="26cc2-140">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="26cc2-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
