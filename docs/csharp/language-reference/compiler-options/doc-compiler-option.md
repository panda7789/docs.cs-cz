---
description: -doc (možnosti kompilátoru C#)
title: -doc (možnosti kompilátoru C#)
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
ms.openlocfilehash: 366bad1029904b3571be0a76d827ff0213d776bb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125745"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="ffa95-103">-doc (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ffa95-103">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="ffa95-104">Možnost **-doc** slouží k umístění dokumentačních komentářů do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ffa95-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa95-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffa95-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ffa95-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ffa95-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="ffa95-107">Výstupní soubor pro jazyk XML, který je vyplněn komentáři v souborech zdrojového kódu kompilace.</span><span class="sxs-lookup"><span data-stu-id="ffa95-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffa95-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffa95-108">Remarks</span></span>  
 <span data-ttu-id="ffa95-109">V souborech zdrojového kódu lze do souboru XML zpracovat a přidat dokumentační komentáře, které předcházejí následujícímu:</span><span class="sxs-lookup"><span data-stu-id="ffa95-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="ffa95-110">Takové uživatelsky definované typy jako [Třída](../keywords/class.md), [delegát](../builtin-types/reference-types.md#the-delegate-type)nebo [rozhraní](../keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="ffa95-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="ffa95-111">Tito členové jako pole, [událost](../keywords/event.md), [vlastnost](../../programming-guide/classes-and-structs/using-properties.md)nebo metoda</span><span class="sxs-lookup"><span data-stu-id="ffa95-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="ffa95-112">Zdrojový soubor zdrojového kódu, který obsahuje Main, je nejprve výstup do XML.</span><span class="sxs-lookup"><span data-stu-id="ffa95-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="ffa95-113">Chcete-li použít vygenerovaný soubor. XML pro použití s funkcí [technologie IntelliSense](/visualstudio/ide/using-intellisense) , nechte název souboru. XML stejný jako sestavení, které chcete podporovat, a poté se ujistěte, že soubor. XML je ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="ffa95-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="ffa95-114">Proto, pokud je odkazováno na sestavení v projektu sady Visual Studio, je také nalezen soubor. XML.</span><span class="sxs-lookup"><span data-stu-id="ffa95-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="ffa95-115">Další informace najdete v tématu [poskytnutí komentářů k kódu](/visualstudio/ide/reference/generate-xml-documentation-comments) a další informace.</span><span class="sxs-lookup"><span data-stu-id="ffa95-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="ffa95-116">Pokud kompilujete s [-target: Module](./target-module-compiler-option.md), `file` bude obsahovat značky, které \<assembly> \</assembly> určují název souboru obsahujícího manifest sestavení pro výstupní soubor kompilace.</span><span class="sxs-lookup"><span data-stu-id="ffa95-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffa95-117">Možnost-doc se vztahuje na všechny vstupní soubory; nebo, pokud je nastavena v nastavení projektu, všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="ffa95-118">Chcete-li zakázat upozornění související s dokumentačními komentáři pro určitý soubor nebo oddíl kódu, použijte [#pragma upozornění](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="ffa95-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="ffa95-119">Způsoby, jak generovat dokumentaci z komentářů v kódu, najdete v tématu [Doporučené značky pro dokumentační komentáře](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) .</span><span class="sxs-lookup"><span data-stu-id="ffa95-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ffa95-120">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ffa95-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ffa95-121">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ffa95-122">Klikněte na kartu **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="ffa95-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="ffa95-123">Upravte vlastnost **souboru dokumentace XML** .</span><span class="sxs-lookup"><span data-stu-id="ffa95-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="ffa95-124">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="ffa95-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa95-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffa95-125">See also</span></span>

- [<span data-ttu-id="ffa95-126">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ffa95-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ffa95-127">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ffa95-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
