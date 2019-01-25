---
title: '-target: appcontainerexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 4f8c59d94b76dd0f3415846f7e682d62cc1771ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707606"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="a7cb8-102">-target: appcontainerexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a7cb8-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="a7cb8-103">Pokud používáte **-target: appcontainerexe** – možnost kompilátoru, kompilátor vytvoří spustitelný soubor (.exe) soubor Windows, který musí být spuštěn v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="a7cb8-104">Tato možnost je ekvivalentní k [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale je navržená pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7cb8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7cb8-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="a7cb8-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7cb8-106">Remarks</span></span>  
 <span data-ttu-id="a7cb8-107">Vyžadovat spuštění v kontejneru aplikace, tato možnost nastaví bit v [přenosný spustitelný soubor](/windows/desktop/Debug/pe-format) souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="a7cb8-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="a7cb8-108">Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess snaží spustit spustitelný soubor mimo kontejner aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="a7cb8-109">Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="a7cb8-110">Pokud zadáte tuto možnost příkazového řádku, všechny soubory až do další **-out** nebo **– cíl** slouží k vytvoření spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="a7cb8-111">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="a7cb8-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="a7cb8-112">V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="a7cb8-113">Na **aplikace** kartě **typ výstupu** klikněte na položku **aplikace Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="a7cb8-114">Tato možnost je dostupná jenom pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikací.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="a7cb8-115">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7cb8-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7cb8-116">Example</span></span>  
 <span data-ttu-id="a7cb8-117">Následující příkaz kompiluje `filename.cs` do Windows spustitelného souboru, který lze spustit pouze v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7cb8-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7cb8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7cb8-118">See also</span></span>

- [<span data-ttu-id="a7cb8-119">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a7cb8-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="a7cb8-120">-target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a7cb8-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)
- [<span data-ttu-id="a7cb8-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7cb8-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
