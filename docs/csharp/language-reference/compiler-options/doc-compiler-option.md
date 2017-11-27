---
title: "-doc (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae3d6e1ffdaaa3245a51005070b16041c16dadae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="doc-c-compiler-options"></a><span data-ttu-id="fd3ae-102">/doc (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="fd3ae-102">/doc (C# Compiler Options)</span></span>
<span data-ttu-id="fd3ae-103">**/Doc** možnost vám umožňuje umístit dokumentační komentáře v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-103">The **/doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd3ae-104">Syntax</span></span>  
  
```console  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd3ae-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fd3ae-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="fd3ae-106">Výstupní soubor pro formát XML, který je naplněn komentáře ve zdrojových souborech kód kompilace.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd3ae-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd3ae-107">Remarks</span></span>  
 <span data-ttu-id="fd3ae-108">V soubory zdrojového kódu můžete zpracovat a přidat do souboru XML dokumentační komentáře, které předcházejí následující:</span><span class="sxs-lookup"><span data-stu-id="fd3ae-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
-   <span data-ttu-id="fd3ae-109">Uživatelem definované typy jako [třída](../../../csharp/language-reference/keywords/class.md), [delegovat](../../../csharp/language-reference/keywords/delegate.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="fd3ae-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
-   <span data-ttu-id="fd3ae-110">Členy jako pole, [událostí](../../../csharp/language-reference/keywords/event.md), [vlastnost](../../../csharp/programming-guide/classes-and-structs/using-properties.md), nebo – metoda</span><span class="sxs-lookup"><span data-stu-id="fd3ae-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="fd3ae-111">Výstup souboru zdrojového kódu, který obsahuje hlavní nejprve je do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="fd3ae-112">Chcete použít soubor .xml vygenerovaný pro použití s [IntelliSense](/visualstudio/ide/using-intellisense) funkci, ponechte název souboru .xml být stejný jako název sestavení, které chcete podporovat a zkontrolujte soubor .xml nachází ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="fd3ae-113">Proto při odkazování na sestavení v sadě Visual Studio projektu, soubor .xml nalezen také.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="fd3ae-114">V tématu [podporované komentáře kódu](/visualstudio/ide/supplying-xml-code-comments) a další informace.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="fd3ae-115">Pokud je kompilovat s [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` bude obsahovat \<sestavení >\</assembly > značky zadáním názvu souboru, který obsahuje manifest sestavení pro výstupní soubor kompilace.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-115">Unless you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd3ae-116">/ DOC možnost se vztahuje na všechny vstupní soubory; nebo, pokud v nastavení projektu, všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-116">The /doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="fd3ae-117">Chcete-li zakázat upozornění související s dokumentační komentáře pro konkrétní soubor nebo části kódu, použijte [#pragma – upozornění](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="fd3ae-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="fd3ae-118">V tématu [doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) pro způsoby, jak generovat dokumentaci z komentářů v kódu.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fd3ae-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd3ae-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="fd3ae-120">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-120">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="fd3ae-121">Klikněte **sestavení** kartě.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-121">Click the **Build** tab.</span></span>  
  
3.  <span data-ttu-id="fd3ae-122">Změnit **souborů dokumentace XML** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="fd3ae-123">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd3ae-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3ae-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd3ae-124">See Also</span></span>  
 [<span data-ttu-id="fd3ae-125">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="fd3ae-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="fd3ae-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="fd3ae-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
