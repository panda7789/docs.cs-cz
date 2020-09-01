---
description: -Platform (možnosti kompilátoru C#)
title: -Platform (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: e2e4fc37418243ff6998d19165250b895c0a4fa1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124861"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="544b7-103">-Platform (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="544b7-103">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="544b7-104">Určuje, která verze modulu CLR (Common Language Runtime) může spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="544b7-104">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="544b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="544b7-105">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="544b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="544b7-106">Parameters</span></span>

`string` \
<span data-ttu-id="544b7-107">anycpu (výchozí), anycpu32bitpreferred, ARM, x64, x86 nebo Itanium.</span><span class="sxs-lookup"><span data-stu-id="544b7-107">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="544b7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="544b7-108">Remarks</span></span>

- <span data-ttu-id="544b7-109">**anycpu** (výchozí) zkompiluje sestavení tak, aby běželo na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="544b7-109">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="544b7-110">Vaše aplikace běží jako 64 proces, kdykoli je to možné, a vrátí se do 32-bit, pokud je k dispozici pouze tento režim.</span><span class="sxs-lookup"><span data-stu-id="544b7-110">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="544b7-111">**anycpu32bitpreferred** zkompiluje vaše sestavení tak, aby běželo na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="544b7-111">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="544b7-112">Vaše aplikace běží v 32ovém režimu v systémech, které podporují 64 i 32-bit aplikací.</span><span class="sxs-lookup"><span data-stu-id="544b7-112">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="544b7-113">Tuto možnost lze zadat pouze pro projekty, které cílí na .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="544b7-113">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>

- <span data-ttu-id="544b7-114">**ARM** zkompiluje vaše sestavení tak, aby běželo na počítači, který má procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="544b7-114">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="544b7-115">**ARM64** zkompiluje sestavení tak, aby běželo 64 CLR na počítači, který má procesor Advanced RISC Machine (ARM), který podporuje instrukční sadu A64.</span><span class="sxs-lookup"><span data-stu-id="544b7-115">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="544b7-116">**x64** kompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 CLR v počítači, který podporuje INSTRUKČNÍ sady amd64 nebo EM64T.</span><span class="sxs-lookup"><span data-stu-id="544b7-116">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="544b7-117">**x86** zkompiluje vaše sestavení tak, aby se spouštělo pomocí 32 CLR kompatibilního s platformou x86.</span><span class="sxs-lookup"><span data-stu-id="544b7-117">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="544b7-118">**Procesory Itanium** zkompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 CLR v počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="544b7-118">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="544b7-119">V 64 operačním systému Windows:</span><span class="sxs-lookup"><span data-stu-id="544b7-119">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="544b7-120">Sestavení kompilována s **platformou: x86** se spustí v 32 CLR spuštěném v WOW64.</span><span class="sxs-lookup"><span data-stu-id="544b7-120">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="544b7-121">Knihovna DLL kompilovaná s **platformou-Platform: anycpu** se spouští na stejném CLR jako proces, do kterého je načtený.</span><span class="sxs-lookup"><span data-stu-id="544b7-121">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="544b7-122">Spustitelné soubory, které jsou kompilovány s **platformou-Platform: anycpu** , se spustí v 64 modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="544b7-122">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="544b7-123">Spustitelné soubory kompilované s **platformou: anycpu32bitpreferred** se spustí na 32 CLR.</span><span class="sxs-lookup"><span data-stu-id="544b7-123">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="544b7-124">Nastavení **anycpu32bitpreferred** je platné pouze pro spustitelný soubor (. Soubory EXE) a vyžaduje .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="544b7-124">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>

<span data-ttu-id="544b7-125">Další informace o vývoji aplikace pro spuštění v operačním systému Windows 64 naleznete v tématu [64-bitové aplikace](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="544b7-125">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="544b7-126">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="544b7-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="544b7-127">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="544b7-127">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="544b7-128">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="544b7-128">Click the **Build** property page.</span></span>

3. <span data-ttu-id="544b7-129">Upravte vlastnost **target platformy** a pro projekty, které cílí na .NET Framework 4,5 zaškrtněte políčko **preferovat 32-bit** nebo zrušte jeho zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="544b7-129">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="544b7-130">`-platform` není k dispozici ve vývojovém prostředí v jazyce Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="544b7-130">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="544b7-131">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A> .</span><span class="sxs-lookup"><span data-stu-id="544b7-131">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="544b7-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="544b7-132">Example</span></span>

<span data-ttu-id="544b7-133">Následující příklad ukazuje, jak použít možnost **-Platform** k určení toho, že by aplikace měla běžet 64 modul CLR na 64 operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="544b7-133">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="544b7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="544b7-134">See also</span></span>

- [<span data-ttu-id="544b7-135">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="544b7-135">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="544b7-136">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="544b7-136">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
