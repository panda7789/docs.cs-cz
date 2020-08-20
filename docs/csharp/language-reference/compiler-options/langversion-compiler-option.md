---
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
ms.openlocfilehash: fd05802008a20267fea54f14bae4c8deb0e21c65
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656203"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="2fb46-102">-langversion – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="2fb46-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="2fb46-103">Způsobí, že kompilátor přijme pouze syntaxi, která je obsažena ve zvolené specifikaci jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2fb46-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fb46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fb46-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="2fb46-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2fb46-105">Arguments</span></span>

`option`

<span data-ttu-id="2fb46-106">Platné jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2fb46-106">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="2fb46-107">Výchozí jazyková verze závisí na cílové architektuře vaší aplikace a na nainstalované verzi sady SDK nebo sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2fb46-107">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="2fb46-108">Tato pravidla jsou definována v článku [Konfigurace jazykové verze](../configure-language-version.md#defaults) .</span><span class="sxs-lookup"><span data-stu-id="2fb46-108">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fb46-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fb46-109">Remarks</span></span>

<span data-ttu-id="2fb46-110">Metadata, na která odkazuje vaše aplikace v jazyce C#, nejsou předmětem možnosti kompilátoru **langversion –** .</span><span class="sxs-lookup"><span data-stu-id="2fb46-110">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="2fb46-111">Vzhledem k tomu, že každá verze kompilátoru jazyka C# obsahuje rozšíření jazykové specifikace, **-langversion –** neposkytuje ekvivalentní funkce starší verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2fb46-111">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="2fb46-112">I když se aktualizace verze C# obecně shodují s hlavními .NET Framework verzemi, Nová syntaxe a funkce nejsou nutně vázané na konkrétní verzi Frameworku.</span><span class="sxs-lookup"><span data-stu-id="2fb46-112">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="2fb46-113">I když nové funkce budou jednoznačně vyžadovat novou aktualizaci kompilátoru, která se také vydává společně s revizí v jazyce C#, každá konkrétní funkce má své vlastní minimální požadavky rozhraní .NET API nebo modulu CLR (Common Language Runtime), které by mohly umožňovat jeho spuštění v rámci architektury nižší verze, včetně balíčků NuGet nebo jiných knihoven.</span><span class="sxs-lookup"><span data-stu-id="2fb46-113">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="2fb46-114">Bez ohledu na to, který parametr **-langversion –** použijete, použijte aktuální verzi modulu CLR (Common Language Runtime) k vytvoření souboru. exe nebo. dll.</span><span class="sxs-lookup"><span data-stu-id="2fb46-114">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="2fb46-115">Jedinou výjimkou jsou Friend sestavení a [-moduleassemblyname – (možnost kompilátoru C#)](./moduleassemblyname-compiler-option.md), která funguje v rámci **-langversion –: ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="2fb46-115">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="2fb46-116">Další způsoby určení verze jazyka C# naleznete v článku o jazykové verzi jazyka [c#](../configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="2fb46-116">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="2fb46-117">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fb46-117">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2fb46-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fb46-118">C# language specification</span></span>

| <span data-ttu-id="2fb46-119">Verze</span><span class="sxs-lookup"><span data-stu-id="2fb46-119">Version</span></span>          | <span data-ttu-id="2fb46-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2fb46-120">Link</span></span>                       | <span data-ttu-id="2fb46-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2fb46-121">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="2fb46-122">C# 7,0 a novější</span><span class="sxs-lookup"><span data-stu-id="2fb46-122">C# 7.0 and later</span></span> |                            | <span data-ttu-id="2fb46-123">Momentálně není k dispozici</span><span class="sxs-lookup"><span data-stu-id="2fb46-123">Not currently available</span></span>                                                 |
| <span data-ttu-id="2fb46-124">C# 6,0</span><span class="sxs-lookup"><span data-stu-id="2fb46-124">C# 6.0</span></span>           | <span data-ttu-id="2fb46-125">[Odkaz][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="2fb46-125">[Link][csharp-6]</span></span>           | <span data-ttu-id="2fb46-126">Specifikace jazyka C# verze 6 – neoficiální koncept: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="2fb46-126">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="2fb46-127">C# 5,0</span><span class="sxs-lookup"><span data-stu-id="2fb46-127">C# 5.0</span></span>           | <span data-ttu-id="2fb46-128">[Stáhnout PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="2fb46-128">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="2fb46-129">Standard ECMA-334 5. edice</span><span class="sxs-lookup"><span data-stu-id="2fb46-129">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="2fb46-130">C# 3,0</span><span class="sxs-lookup"><span data-stu-id="2fb46-130">C# 3.0</span></span>           | <span data-ttu-id="2fb46-131">[Stáhnout dokument][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="2fb46-131">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="2fb46-132">Specifikace jazyka C# verze 3,0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2fb46-132">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="2fb46-133">C# 2,0</span><span class="sxs-lookup"><span data-stu-id="2fb46-133">C# 2.0</span></span>           | <span data-ttu-id="2fb46-134">[Stáhnout PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="2fb46-134">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="2fb46-135">Standard ECMA – 334 4. edice</span><span class="sxs-lookup"><span data-stu-id="2fb46-135">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="2fb46-136">C# 1,2</span><span class="sxs-lookup"><span data-stu-id="2fb46-136">C# 1.2</span></span>           | <span data-ttu-id="2fb46-137">[Stáhnout dokument][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="2fb46-137">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="2fb46-138">Specifikace jazyka C# verze 1,2: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2fb46-138">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="2fb46-139">C# 1,0</span><span class="sxs-lookup"><span data-stu-id="2fb46-139">C# 1.0</span></span>           | <span data-ttu-id="2fb46-140">[Stáhnout dokument][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="2fb46-140">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="2fb46-141">Specifikace jazyka C# verze 1,0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2fb46-141">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="2fb46-142">Minimální verze sady SDK potřebná pro podporu všech funkcí jazyka</span><span class="sxs-lookup"><span data-stu-id="2fb46-142">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="2fb46-143">V následující tabulce je uveden minimální počet verzí sady SDK s kompilátorem jazyka C#, který podporuje odpovídající jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="2fb46-143">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="2fb46-144">Verze C#</span><span class="sxs-lookup"><span data-stu-id="2fb46-144">C# version</span></span> | <span data-ttu-id="2fb46-145">Minimální verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="2fb46-145">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="2fb46-146">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="2fb46-146">C# 8.0</span></span>     | <span data-ttu-id="2fb46-147">Microsoft Visual Studio/Build Tools 2019, verze 16,3 nebo .NET Core 3,0 SDK</span><span class="sxs-lookup"><span data-stu-id="2fb46-147">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="2fb46-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="2fb46-148">C# 7.3</span></span>     | <span data-ttu-id="2fb46-149">Microsoft Visual Studio/Build Tools 2017, verze 15,7</span><span class="sxs-lookup"><span data-stu-id="2fb46-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="2fb46-150">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="2fb46-150">C# 7.2</span></span>     | <span data-ttu-id="2fb46-151">Microsoft Visual Studio/Build Tools 2017, verze 15,5</span><span class="sxs-lookup"><span data-stu-id="2fb46-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="2fb46-152">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="2fb46-152">C# 7.1</span></span>     | <span data-ttu-id="2fb46-153">Microsoft Visual Studio/Build Tools 2017, verze 15,3</span><span class="sxs-lookup"><span data-stu-id="2fb46-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="2fb46-154">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="2fb46-154">C# 7.0</span></span>     | <span data-ttu-id="2fb46-155">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="2fb46-155">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="2fb46-156">C# 6</span><span class="sxs-lookup"><span data-stu-id="2fb46-156">C# 6</span></span>       | <span data-ttu-id="2fb46-157">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="2fb46-157">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="2fb46-158">C# 5</span><span class="sxs-lookup"><span data-stu-id="2fb46-158">C# 5</span></span>       | <span data-ttu-id="2fb46-159">Microsoft Visual Studio/Build Tools 2012 nebo .NET Framework 4,5 kompilátor</span><span class="sxs-lookup"><span data-stu-id="2fb46-159">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="2fb46-160">C# 4</span><span class="sxs-lookup"><span data-stu-id="2fb46-160">C# 4</span></span>       | <span data-ttu-id="2fb46-161">Microsoft Visual Studio/Build Tools 2010 nebo .NET Framework 4,0 kompilátor</span><span class="sxs-lookup"><span data-stu-id="2fb46-161">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="2fb46-162">C# 3</span><span class="sxs-lookup"><span data-stu-id="2fb46-162">C# 3</span></span>       | <span data-ttu-id="2fb46-163">Microsoft Visual Studio/Build Tools 2008 nebo .NET Framework 3,5 kompilátor</span><span class="sxs-lookup"><span data-stu-id="2fb46-163">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="2fb46-164">C# 2</span><span class="sxs-lookup"><span data-stu-id="2fb46-164">C# 2</span></span>       | <span data-ttu-id="2fb46-165">Microsoft Visual Studio/Build Tools 2005 nebo .NET Framework 2,0 kompilátor</span><span class="sxs-lookup"><span data-stu-id="2fb46-165">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="2fb46-166">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="2fb46-166">C# 1.0/1.2</span></span> | <span data-ttu-id="2fb46-167">Microsoft Visual Studio/Build Tools .NET 2002 nebo kompilátor .NET Framework 1,0</span><span class="sxs-lookup"><span data-stu-id="2fb46-167">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="2fb46-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fb46-168">See also</span></span>

- [<span data-ttu-id="2fb46-169">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="2fb46-169">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="2fb46-170">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="2fb46-170">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
