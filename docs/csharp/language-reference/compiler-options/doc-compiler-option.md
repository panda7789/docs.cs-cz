---
title: -doc (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: c46118a9b02df653844a0ca04f9e8f9952a957c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662904"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="49638-102">-doc (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="49638-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="49638-103">**-Doc** možnost umožňuje umístit komentáře dokumentace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="49638-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49638-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49638-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="49638-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="49638-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="49638-106">Výstupní soubor pro XML, který je naplněn komentáře v souborech zdrojového kódu kompilace.</span><span class="sxs-lookup"><span data-stu-id="49638-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49638-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49638-107">Remarks</span></span>  
 <span data-ttu-id="49638-108">V souborech zdrojového kódu je možné zpracovat a přidat do souboru XML dokumentační komentáře, které předcházet následující:</span><span class="sxs-lookup"><span data-stu-id="49638-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="49638-109">Uživatelem definované typy jako [třídy](../../../csharp/language-reference/keywords/class.md), [delegovat](../../../csharp/language-reference/keywords/delegate.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="49638-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
- <span data-ttu-id="49638-110">Členy jako pole, [události](../../../csharp/language-reference/keywords/event.md), [vlastnost](../../../csharp/programming-guide/classes-and-structs/using-properties.md), nebo – metoda</span><span class="sxs-lookup"><span data-stu-id="49638-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="49638-111">Výstup souboru se zdrojovým kódem, který obsahuje hlavní je nejdříve do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="49638-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="49638-112">Použít soubor generovaný XML pro použití se službou [IntelliSense](/visualstudio/ide/using-intellisense) funkcí, ponechte název souboru .xml být stejný jako název sestavení, které chcete podporovat a zkontrolujte, že soubor .xml nachází ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="49638-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="49638-113">Proto když sestavení se odkazuje v projektu sady Visual Studio, soubor .xml nenajde také.</span><span class="sxs-lookup"><span data-stu-id="49638-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="49638-114">Zobrazit [zadávání komentářů ke kódu](/visualstudio/ide/supplying-xml-code-comments) a další informace.</span><span class="sxs-lookup"><span data-stu-id="49638-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="49638-115">Pokud kompilujete s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` bude obsahovat \<sestavení > \< /Assembly > značky zadání názvu souboru, který obsahuje manifest sestavení pro výstupní soubor kompilace.</span><span class="sxs-lookup"><span data-stu-id="49638-115">Unless you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49638-116">-Doc – možnost platí pro všechny vstupní soubory. nebo, pokud v nastavení projektu, všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="49638-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="49638-117">Chcete-li vypnout upozornění související s komentáře dokumentace pro konkrétní soubor nebo části kódu, použijte [varování #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="49638-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="49638-118">Zobrazit [doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) způsoby, jak generovat dokumentaci z komentáře v kódu.</span><span class="sxs-lookup"><span data-stu-id="49638-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="49638-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49638-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="49638-120">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="49638-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="49638-121">Klikněte na tlačítko **sestavení** kartu.</span><span class="sxs-lookup"><span data-stu-id="49638-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="49638-122">Upravit **soubor dokumentace XML** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="49638-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="49638-123">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="49638-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49638-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49638-124">See also</span></span>

- [<span data-ttu-id="49638-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="49638-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="49638-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="49638-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
