---
title: '-target: appcontainerexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: b8765f64aeb08d816ca17fce64c13e981d85145b
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42907654"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="5b489-102">-target: appcontainerexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5b489-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="5b489-103">Pokud používáte **-target: appcontainerexe** – možnost kompilátoru, kompilátor vytvoří spustitelný soubor (.exe) soubor Windows, který musí být spuštěn v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b489-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="5b489-104">Tato možnost je ekvivalentní k [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale je navržená pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b489-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b489-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b489-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="5b489-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b489-106">Remarks</span></span>  
 <span data-ttu-id="5b489-107">Vyžadovat spuštění v kontejneru aplikace, tato možnost nastaví bit v [přenosný spustitelný soubor](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="5b489-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (PE) file.</span></span> <span data-ttu-id="5b489-108">Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess snaží spustit spustitelný soubor mimo kontejner aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b489-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="5b489-109">Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="5b489-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="5b489-110">Pokud zadáte tuto možnost příkazového řádku, všechny soubory až do další **-out** nebo **– cíl** slouží k vytvoření spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="5b489-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="5b489-111">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="5b489-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="5b489-112">V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5b489-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="5b489-113">Na **aplikace** kartě **typ výstupu** klikněte na položku **aplikace Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="5b489-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="5b489-114">Tato možnost je dostupná jenom pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikací.</span><span class="sxs-lookup"><span data-stu-id="5b489-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="5b489-115">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b489-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b489-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b489-116">Example</span></span>  
 <span data-ttu-id="5b489-117">Následující příkaz kompiluje `filename.cs` do Windows spustitelného souboru, který lze spustit pouze v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b489-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b489-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b489-118">See Also</span></span>  
 [<span data-ttu-id="5b489-119">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5b489-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="5b489-120">-target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5b489-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="5b489-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5b489-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
