---
title: -target:appcontainerexe (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204525"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="10c73-102">-target:appcontainerexe (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="10c73-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="10c73-103">Pokud použijete možnost kompilátoru **-target:appcontainerexe,** kompilátor vytvoří soubor spustitelného souboru systému Windows (.exe), který musí být spuštěn v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="10c73-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="10c73-104">Tato možnost je ekvivalentní [-target:winexe,](./target-winexe-compiler-option.md) ale je určena pro aplikace pro Windows 8.x Store.</span><span class="sxs-lookup"><span data-stu-id="10c73-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10c73-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10c73-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="10c73-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10c73-106">Remarks</span></span>  
 <span data-ttu-id="10c73-107">Chcete-li vyžadovat, aby aplikace běžela v kontejneru aplikace, tato možnost nastaví bit v souboru [Přenosného spustitelného souboru](/windows/desktop/Debug/pe-format) (PE).</span><span class="sxs-lookup"><span data-stu-id="10c73-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="10c73-108">Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess pokusí spustit spustitelný soubor mimo kontejner aplikace.</span><span class="sxs-lookup"><span data-stu-id="10c73-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="10c73-109">Pokud nepoužijete možnost [-out,](./out-compiler-option.md) název výstupního souboru přebírá název vstupního souboru, který obsahuje metodu [Main.](../../programming-guide/main-and-command-args/index.md)</span><span class="sxs-lookup"><span data-stu-id="10c73-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="10c73-110">Zadáte-li tuto možnost na příkazovém řádku, budou k vytvoření spustitelného souboru použity všechny soubory až do další volby **-out** nebo **-target.**</span><span class="sxs-lookup"><span data-stu-id="10c73-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="10c73-111">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="10c73-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="10c73-112">V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="10c73-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="10c73-113">Na kartě **Aplikace** v seznamu **Typ výstupu** zvolte **Aplikaci pro Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="10c73-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="10c73-114">Tato možnost je dostupná jenom pro šablony aplikací pro Windows 8.x Store.</span><span class="sxs-lookup"><span data-stu-id="10c73-114">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="10c73-115">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="10c73-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10c73-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="10c73-116">Example</span></span>  
 <span data-ttu-id="10c73-117">Následující příkaz se `filename.cs` zkompiluje do spustitelného souboru systému Windows, který lze spustit pouze v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="10c73-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="10c73-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="10c73-118">See also</span></span>

- [<span data-ttu-id="10c73-119">-target (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="10c73-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="10c73-120">-target:winexe (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="10c73-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="10c73-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10c73-121">C# Compiler Options</span></span>](./index.md)
