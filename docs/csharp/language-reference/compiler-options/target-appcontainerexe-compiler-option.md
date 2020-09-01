---
description: '-target: appcontainerexe (možnosti kompilátoru C#)'
title: '-target: appcontainerexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 8c3b85c2f5a20788bd311e9bf3b300c32967da77
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128579"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="a82d1-103">-target: appcontainerexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a82d1-103">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="a82d1-104">Použijete-li možnost kompilátoru **-target: appcontainerexe** , kompilátor vytvoří spustitelný soubor systému Windows (. exe), který musí být spuštěn v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-104">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="a82d1-105">Tato možnost je ekvivalentní k [cíli: winexe](./target-winexe-compiler-option.md) , ale je navržena pro aplikace Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="a82d1-105">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a82d1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a82d1-106">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="a82d1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a82d1-107">Remarks</span></span>  
 <span data-ttu-id="a82d1-108">Pokud chcete, aby aplikace běžela v kontejneru aplikace, tato možnost nastaví bit v [přenositelném spustitelném](/windows/desktop/Debug/pe-format) souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="a82d1-108">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="a82d1-109">Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess pokusí spustit spustitelný soubor mimo kontejner aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-109">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="a82d1-110">Pokud nepoužijete možnost [-out](./out-compiler-option.md) , název výstupního souboru vezme název vstupního souboru, který obsahuje metodu [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="a82d1-110">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="a82d1-111">Když zadáte tuto možnost na příkazovém řádku, všechny soubory až do **Možnosti další nebo** **cíl** se použijí k vytvoření spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="a82d1-111">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="a82d1-112">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="a82d1-112">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="a82d1-113">V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a82d1-113">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="a82d1-114">Na kartě **aplikace** v seznamu **Typ výstupu** vyberte možnost **aplikace pro Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="a82d1-114">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="a82d1-115">Tato možnost je k dispozici pouze pro šablony aplikací Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="a82d1-115">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="a82d1-116">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="a82d1-116">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a82d1-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="a82d1-117">Example</span></span>  
 <span data-ttu-id="a82d1-118">Následující příkaz se zkompiluje `filename.cs` do spustitelného souboru systému Windows, který lze spustit pouze v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-118">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a82d1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a82d1-119">See also</span></span>

- [<span data-ttu-id="a82d1-120">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a82d1-120">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="a82d1-121">-target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a82d1-121">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="a82d1-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="a82d1-122">C# Compiler Options</span></span>](./index.md)
