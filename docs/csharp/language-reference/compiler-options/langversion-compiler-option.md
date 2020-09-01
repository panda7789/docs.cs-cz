---
description: -langversion – (možnosti kompilátoru C#)
title: -langversion – (možnosti kompilátoru C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: b0e966bcc87303c0a7c2199fbfac743b22481424
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125472"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="65184-103">-langversion – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="65184-103">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="65184-104">Způsobí, že kompilátor přijme pouze syntaxi, která je obsažena ve zvolené specifikaci jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="65184-104">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="65184-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65184-105">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="65184-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="65184-106">Arguments</span></span>

`option`

<span data-ttu-id="65184-107">Platné jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="65184-107">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="65184-108">Výchozí jazyková verze závisí na cílové architektuře vaší aplikace a na nainstalované verzi sady SDK nebo sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65184-108">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="65184-109">Tato pravidla jsou definována v článku [Konfigurace jazykové verze](../configure-language-version.md#defaults) .</span><span class="sxs-lookup"><span data-stu-id="65184-109">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="65184-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65184-110">Remarks</span></span>

<span data-ttu-id="65184-111">Metadata, na která odkazuje vaše aplikace v jazyce C#, nejsou předmětem možnosti kompilátoru **langversion –** .</span><span class="sxs-lookup"><span data-stu-id="65184-111">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="65184-112">Vzhledem k tomu, že každá verze kompilátoru jazyka C# obsahuje rozšíření jazykové specifikace, **-langversion –** neposkytuje ekvivalentní funkce starší verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="65184-112">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="65184-113">I když se aktualizace verze C# obecně shodují s hlavními .NET Framework verzemi, Nová syntaxe a funkce nejsou nutně vázané na konkrétní verzi Frameworku.</span><span class="sxs-lookup"><span data-stu-id="65184-113">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="65184-114">I když nové funkce budou jednoznačně vyžadovat novou aktualizaci kompilátoru, která se také vydává společně s revizí v jazyce C#, každá konkrétní funkce má své vlastní minimální požadavky rozhraní .NET API nebo modulu CLR (Common Language Runtime), které by mohly umožňovat jeho spuštění v rámci architektury nižší verze, včetně balíčků NuGet nebo jiných knihoven.</span><span class="sxs-lookup"><span data-stu-id="65184-114">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="65184-115">Bez ohledu na to, který parametr **-langversion –** použijete, použijte aktuální verzi modulu CLR (Common Language Runtime) k vytvoření souboru. exe nebo. dll.</span><span class="sxs-lookup"><span data-stu-id="65184-115">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="65184-116">Jedinou výjimkou jsou Friend sestavení a [-moduleassemblyname – (možnost kompilátoru C#)](./moduleassemblyname-compiler-option.md), která funguje v rámci **-langversion –: ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="65184-116">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="65184-117">Další způsoby určení verze jazyka C# naleznete v článku o jazykové verzi jazyka [c#](../configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="65184-117">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="65184-118">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> .</span><span class="sxs-lookup"><span data-stu-id="65184-118">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="65184-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="65184-119">C# language specification</span></span>

| <span data-ttu-id="65184-120">Verze</span><span class="sxs-lookup"><span data-stu-id="65184-120">Version</span></span>          | <span data-ttu-id="65184-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="65184-121">Link</span></span>                       | <span data-ttu-id="65184-122">Popis</span><span class="sxs-lookup"><span data-stu-id="65184-122">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="65184-123">C# 7,0 a novější</span><span class="sxs-lookup"><span data-stu-id="65184-123">C# 7.0 and later</span></span> |                            | <span data-ttu-id="65184-124">Momentálně není k dispozici</span><span class="sxs-lookup"><span data-stu-id="65184-124">Not currently available</span></span>                                                 |
| <span data-ttu-id="65184-125">C# 6,0</span><span class="sxs-lookup"><span data-stu-id="65184-125">C# 6.0</span></span>           | <span data-ttu-id="65184-126">[Odkaz][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="65184-126">[Link][csharp-6]</span></span>           | <span data-ttu-id="65184-127">Specifikace jazyka C# verze 6 – neoficiální koncept: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="65184-127">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="65184-128">C# 5,0</span><span class="sxs-lookup"><span data-stu-id="65184-128">C# 5.0</span></span>           | <span data-ttu-id="65184-129">[Stáhnout PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="65184-129">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="65184-130">Standard ECMA-334 5. edice</span><span class="sxs-lookup"><span data-stu-id="65184-130">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="65184-131">C# 3,0</span><span class="sxs-lookup"><span data-stu-id="65184-131">C# 3.0</span></span>           | <span data-ttu-id="65184-132">[Stáhnout dokument][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="65184-132">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="65184-133">Specifikace jazyka C# verze 3,0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="65184-133">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="65184-134">C# 2,0</span><span class="sxs-lookup"><span data-stu-id="65184-134">C# 2.0</span></span>           | <span data-ttu-id="65184-135">[Stáhnout PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="65184-135">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="65184-136">Standard ECMA – 334 4. edice</span><span class="sxs-lookup"><span data-stu-id="65184-136">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="65184-137">C# 1,2</span><span class="sxs-lookup"><span data-stu-id="65184-137">C# 1.2</span></span>           | <span data-ttu-id="65184-138">[Stáhnout dokument][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="65184-138">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="65184-139">Specifikace jazyka C# verze 1,2: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="65184-139">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="65184-140">C# 1,0</span><span class="sxs-lookup"><span data-stu-id="65184-140">C# 1.0</span></span>           | <span data-ttu-id="65184-141">[Stáhnout dokument][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="65184-141">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="65184-142">Specifikace jazyka C# verze 1,0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="65184-142">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="65184-143">Minimální verze sady SDK potřebná pro podporu všech funkcí jazyka</span><span class="sxs-lookup"><span data-stu-id="65184-143">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="65184-144">V následující tabulce je uveden minimální počet verzí sady SDK s kompilátorem jazyka C#, který podporuje odpovídající jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="65184-144">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="65184-145">Verze C#</span><span class="sxs-lookup"><span data-stu-id="65184-145">C# version</span></span> | <span data-ttu-id="65184-146">Minimální verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="65184-146">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="65184-147">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="65184-147">C# 8.0</span></span>     | <span data-ttu-id="65184-148">Microsoft Visual Studio/Build Tools 2019, verze 16,3 nebo .NET Core 3,0 SDK</span><span class="sxs-lookup"><span data-stu-id="65184-148">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="65184-149">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="65184-149">C# 7.3</span></span>     | <span data-ttu-id="65184-150">Microsoft Visual Studio/Build Tools 2017, verze 15,7</span><span class="sxs-lookup"><span data-stu-id="65184-150">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="65184-151">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="65184-151">C# 7.2</span></span>     | <span data-ttu-id="65184-152">Microsoft Visual Studio/Build Tools 2017, verze 15,5</span><span class="sxs-lookup"><span data-stu-id="65184-152">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="65184-153">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="65184-153">C# 7.1</span></span>     | <span data-ttu-id="65184-154">Microsoft Visual Studio/Build Tools 2017, verze 15,3</span><span class="sxs-lookup"><span data-stu-id="65184-154">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="65184-155">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="65184-155">C# 7.0</span></span>     | <span data-ttu-id="65184-156">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="65184-156">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="65184-157">C# 6</span><span class="sxs-lookup"><span data-stu-id="65184-157">C# 6</span></span>       | <span data-ttu-id="65184-158">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="65184-158">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="65184-159">C# 5</span><span class="sxs-lookup"><span data-stu-id="65184-159">C# 5</span></span>       | <span data-ttu-id="65184-160">Microsoft Visual Studio/Build Tools 2012 nebo .NET Framework 4,5 kompilátor</span><span class="sxs-lookup"><span data-stu-id="65184-160">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="65184-161">C# 4</span><span class="sxs-lookup"><span data-stu-id="65184-161">C# 4</span></span>       | <span data-ttu-id="65184-162">Microsoft Visual Studio/Build Tools 2010 nebo .NET Framework 4,0 kompilátor</span><span class="sxs-lookup"><span data-stu-id="65184-162">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="65184-163">C# 3</span><span class="sxs-lookup"><span data-stu-id="65184-163">C# 3</span></span>       | <span data-ttu-id="65184-164">Microsoft Visual Studio/Build Tools 2008 nebo .NET Framework 3,5 kompilátor</span><span class="sxs-lookup"><span data-stu-id="65184-164">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="65184-165">C# 2</span><span class="sxs-lookup"><span data-stu-id="65184-165">C# 2</span></span>       | <span data-ttu-id="65184-166">Microsoft Visual Studio/Build Tools 2005 nebo .NET Framework 2,0 kompilátor</span><span class="sxs-lookup"><span data-stu-id="65184-166">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="65184-167">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="65184-167">C# 1.0/1.2</span></span> | <span data-ttu-id="65184-168">Microsoft Visual Studio/Build Tools .NET 2002 nebo kompilátor .NET Framework 1,0</span><span class="sxs-lookup"><span data-stu-id="65184-168">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="65184-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="65184-169">See also</span></span>

- [<span data-ttu-id="65184-170">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="65184-170">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="65184-171">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="65184-171">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
