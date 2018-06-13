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
ms.openlocfilehash: d4cb4e219189deb6048692822c9245c5a03c5675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216509"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="dbc15-102">-platform (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="dbc15-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="dbc15-103">Určuje, jaká verze Common Language Runtime (CLR) můžete spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="dbc15-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbc15-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbc15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbc15-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="dbc15-106">anycpu (výchozí), anycpu32bitpreferred, ARM, x 64, x86 nebo Itanium.</span><span class="sxs-lookup"><span data-stu-id="dbc15-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbc15-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbc15-107">Remarks</span></span>  
  
-   <span data-ttu-id="dbc15-108">**anycpu** (výchozí) zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="dbc15-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dbc15-109">Vaše aplikace běží jako 64bitový proces kdykoli je to možné a spadne zpět na 32-bit v případě pouze tento režim je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="dbc15-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="dbc15-110">**anycpu32bitpreferred** zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="dbc15-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dbc15-111">Vaše aplikace běží v režimu 32-bit v systémech, které podporují 64bitové a 32bitové aplikace.</span><span class="sxs-lookup"><span data-stu-id="dbc15-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="dbc15-112">Tato možnost jenom pro projekty můžete zadat cílených rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="dbc15-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="dbc15-113">**ARM** zkompiluje vaše sestavení pro spuštění v počítači, který má procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="dbc15-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="dbc15-114">**x64** zkompiluje vaše sestavení pro 64bitové verze CLR spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.</span><span class="sxs-lookup"><span data-stu-id="dbc15-114">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="dbc15-115">**x86** zkompiluje vaše sestavení ke spuštění x86 kompatibilní, 32bitová verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="dbc15-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="dbc15-116">**Itanium** zkompiluje vaše sestavení pro 64bitové verze CLR spustit na počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="dbc15-116">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="dbc15-117">64bitová verze operačního systému Windows:</span><span class="sxs-lookup"><span data-stu-id="dbc15-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="dbc15-118">Sestavení kompilovat s **-platformy: x 86** spustit na 32bitová verze modulu CLR spuštěna pod WOW64.</span><span class="sxs-lookup"><span data-stu-id="dbc15-118">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="dbc15-119">Knihovny DLL kompilovat s **-platform: anycpu** spouští ve stejném modulu CLR jako proces, do kterého je načten.</span><span class="sxs-lookup"><span data-stu-id="dbc15-119">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="dbc15-120">Spustitelné soubory, které jsou kompilovat s **-platform: anycpu** spustit na 64-bit CLR.</span><span class="sxs-lookup"><span data-stu-id="dbc15-120">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="dbc15-121">Spustitelné soubory kompilovat s **-platformy: anycpu32bitpreferred** spustit na 32bitová verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="dbc15-121">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="dbc15-122">**Anycpu32bitpreferred** nastavení je platná pouze pro spustitelný soubor (. Soubory EXE) ale vyžaduje rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="dbc15-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="dbc15-123">Další informace o vývoji aplikace ke spuštění v operačním systému Windows 64-bit najdete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="dbc15-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="dbc15-124">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbc15-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="dbc15-125">Otevřete **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="dbc15-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="dbc15-126">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="dbc15-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="dbc15-127">Změnit **Cílová platforma** vlastnost a pro projekty, které cílí na rozhraní .NET Framework 4.5, zaškrtněte nebo zrušte **raději 32bitové** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="dbc15-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="dbc15-128">**Poznámka: - platformy** není k dispozici ve vývojovém prostředí Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="dbc15-128">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="dbc15-129">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="dbc15-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc15-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="dbc15-130">Example</span></span>  
 <span data-ttu-id="dbc15-131">Následující příklad ukazuje, jak používat **-platformy** můžete určit, že aplikace měly být spuštěny pomocí modulu CLR 64bitová verze 64bitová verze operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc15-131">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbc15-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbc15-132">See Also</span></span>  
 [<span data-ttu-id="dbc15-133">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dbc15-133">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="dbc15-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="dbc15-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
