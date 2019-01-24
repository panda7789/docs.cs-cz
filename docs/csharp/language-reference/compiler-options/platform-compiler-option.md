---
title: -platform (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 1573e28f2a6f9dec7825d364debcdf1085ef7ff2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635661"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="d01ed-102">-platform (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d01ed-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="d01ed-103">Určuje, jaké verze Common Language Runtime (CLR) můžete spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="d01ed-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d01ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d01ed-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d01ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d01ed-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="d01ed-106">anycpu (výchozí), anycpu32bitpreferred, ARM, x 64, x86 nebo Itanium.</span><span class="sxs-lookup"><span data-stu-id="d01ed-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d01ed-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d01ed-107">Remarks</span></span>  
  
-   <span data-ttu-id="d01ed-108">**anycpu** (výchozí) kompiluje sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="d01ed-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d01ed-109">Vaše aplikace běží jako 64bitový proces, kdykoli je to možné a spadne zpět na 32bitovém základě když pouze tento režim je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d01ed-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="d01ed-110">**anycpu32bitpreferred** zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="d01ed-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d01ed-111">Vaše aplikace běží v režimu 32-bit na systémy, které podporují 64bitové a 32bitové aplikace.</span><span class="sxs-lookup"><span data-stu-id="d01ed-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="d01ed-112">Můžete použít tuto možnost pouze pro projekty, které se zaměřují na rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d01ed-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="d01ed-113">**ARM** kompiluje sestavení ke spuštění v počítači, který má procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="d01ed-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="d01ed-114">**x64** kompiluje sestavení ke spuštění v 64bitovém modulu CLR na počítači, který podporuje AMD64 nebo EM64T instrukční sadu.</span><span class="sxs-lookup"><span data-stu-id="d01ed-114">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="d01ed-115">**x86** kompiluje sestavení ke spuštění v 32 bitů, které je kompatibilní x86 CLR.</span><span class="sxs-lookup"><span data-stu-id="d01ed-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="d01ed-116">**Itanium** kompiluje sestavení ke spuštění v 64bitovém modulu CLR na počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="d01ed-116">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="d01ed-117">V operačním systému Windows 64-bit:</span><span class="sxs-lookup"><span data-stu-id="d01ed-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="d01ed-118">Sestavení zkompilovaná **-platform: x 86** spouštět na 32-bit CLR spuštěna v modulu WOW64.</span><span class="sxs-lookup"><span data-stu-id="d01ed-118">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="d01ed-119">Knihovna DLL zkompilovaná **– platforma: anycpu** provede na stejném modulu CLR jako proces, do které je načten.</span><span class="sxs-lookup"><span data-stu-id="d01ed-119">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="d01ed-120">Spustitelné soubory, které jsou kompilovány pomocí **-platform: anycpu** spuštění v 64bitovém modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d01ed-120">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="d01ed-121">Spustitelné soubory zkompilovaná **-platform: anycpu32bitpreferred** spouštět na 32-bit modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d01ed-121">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="d01ed-122">**Anycpu32bitpreferred** nastavení platí jenom pro spustitelný soubor (. Soubory EXE) a vyžaduje rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d01ed-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="d01ed-123">Další informace o vývoji aplikací pro spuštění v operačním systému Windows 64-bit, naleznete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d01ed-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d01ed-124">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d01ed-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d01ed-125">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="d01ed-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="d01ed-126">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="d01ed-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d01ed-127">Upravit **Cílová platforma** vlastnost a pro projekty, které jsou cíleny na rozhraní .NET Framework 4.5, zaškrtněte nebo zrušte zaškrtnutí **preferovat 32bitovou verzi** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="d01ed-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="d01ed-128">**Poznámka: - platform** není k dispozici ve vývojovém prostředí sady Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="d01ed-128">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="d01ed-129">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="d01ed-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d01ed-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d01ed-130">Example</span></span>  
 <span data-ttu-id="d01ed-131">Následující příklad ukazuje způsob použití **-platform** možnost určit, že aplikace by měla spustit 64bitový modul CLR v operačním systému Windows 64-bit.</span><span class="sxs-lookup"><span data-stu-id="d01ed-131">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d01ed-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d01ed-132">See also</span></span>

- [<span data-ttu-id="d01ed-133">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d01ed-133">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="d01ed-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="d01ed-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
