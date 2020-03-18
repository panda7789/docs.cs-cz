---
title: -platforma (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70849877"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="0cd47-102">-platforma (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0cd47-102">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="0cd47-103">Určuje, která verze clr (Common Language Runtime) může spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cd47-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="0cd47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cd47-104">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="0cd47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cd47-105">Parameters</span></span>

`string` \
<span data-ttu-id="0cd47-106">anycpu (výchozí), anycpu32bitpreferred, ARM, x64, x86 nebo Itanium.</span><span class="sxs-lookup"><span data-stu-id="0cd47-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cd47-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cd47-107">Remarks</span></span>

- <span data-ttu-id="0cd47-108">**anycpu** (výchozí) zkompiluje sestavení spustit na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="0cd47-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0cd47-109">Aplikace běží jako 64bitový proces, kdykoli je to možné, a přejde zpět na 32bitový, pokud je k dispozici pouze tento režim.</span><span class="sxs-lookup"><span data-stu-id="0cd47-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="0cd47-110">**anycpu32bitpreferred** zkompiluje sestavení spustit na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="0cd47-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0cd47-111">Aplikace běží v 32bitovém režimu v systémech, které podporují 64bitové i 32bitové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0cd47-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="0cd47-112">Tuto možnost můžete zadat pouze pro projekty, které cílí na rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0cd47-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>

- <span data-ttu-id="0cd47-113">**ARM** zkompiluje sestavení ke spuštění v počítači, který má procesor Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="0cd47-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="0cd47-114">**ARM64** zkompiluje sestavení ke spuštění 64bitové CLR v počítači, který má procesor Advanced RISC Machine (ARM), který podporuje instrukční sadu A64.</span><span class="sxs-lookup"><span data-stu-id="0cd47-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="0cd47-115">**x64** zkompiluje sestavení, které má být spuštěno 64bitovým clr v počítači, který podporuje instrukční sadu AMD64 nebo EM64T.</span><span class="sxs-lookup"><span data-stu-id="0cd47-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="0cd47-116">**x86** zkompiluje sestavení, které bude spuštěno 32bitovým kódem CLR kompatibilním s x86.</span><span class="sxs-lookup"><span data-stu-id="0cd47-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="0cd47-117">**Itanium** zkompiluje sestavení, které bude spuštěno 64bitovým CLR v počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="0cd47-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="0cd47-118">V 64bitovém operačním systému Windows:</span><span class="sxs-lookup"><span data-stu-id="0cd47-118">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="0cd47-119">Sestavení zkompilovaná s **-platform:x86** se provádějí na 32bitovém CLR běžícím pod WOW64.</span><span class="sxs-lookup"><span data-stu-id="0cd47-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="0cd47-120">DLL zkompilované s **-platform:anycpu** spustí na stejném CLR jako proces, do kterého je načten.</span><span class="sxs-lookup"><span data-stu-id="0cd47-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="0cd47-121">Spustitelné soubory, které jsou kompilovány s **-platform:anycpu** spustit na 64bitclr.</span><span class="sxs-lookup"><span data-stu-id="0cd47-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="0cd47-122">Spustitelné soubory zkompilované s **-platform:anycpu32bitpreferred** provést na 32bitCLR.</span><span class="sxs-lookup"><span data-stu-id="0cd47-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="0cd47-123">**Anycpu32bitpreferred** nastavení je platné pouze pro spustitelný soubor (. EXE) a vyžaduje rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0cd47-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>

<span data-ttu-id="0cd47-124">Další informace o vývoji aplikace pro spuštění v 64bitovém operačním systému Windows naleznete v [64bitových aplikacích](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="0cd47-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0cd47-125">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0cd47-125">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="0cd47-126">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="0cd47-126">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="0cd47-127">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="0cd47-127">Click the **Build** property page.</span></span>

3. <span data-ttu-id="0cd47-128">Upravte vlastnost **Target platformy** a u projektů, které cílí na rozhraní .NET Framework 4.5, zaškrtněte nebo zrušte zaškrtnutí políčka **Preferovat 32bitový.**</span><span class="sxs-lookup"><span data-stu-id="0cd47-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="0cd47-129">`-platform`není k dispozici ve vývojovém prostředí v jazyce Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="0cd47-129">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="0cd47-130">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="0cd47-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="0cd47-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cd47-131">Example</span></span>

<span data-ttu-id="0cd47-132">Následující příklad ukazuje, jak pomocí **-platforma** možnost určit, že aplikace by měla být spuštěna 64bitový CLR na 64bitový operační systém Windows.</span><span class="sxs-lookup"><span data-stu-id="0cd47-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="0cd47-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cd47-133">See also</span></span>

- [<span data-ttu-id="0cd47-134">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0cd47-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="0cd47-135">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0cd47-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
