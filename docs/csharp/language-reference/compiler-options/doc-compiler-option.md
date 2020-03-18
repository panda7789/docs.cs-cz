---
title: -doc (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422976"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="1c043-102">-doc (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1c043-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="1c043-103">Možnost **-doc** umožňuje umístit komentáře dokumentace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="1c043-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c043-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1c043-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c043-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="1c043-106">Výstupní soubor pro XML, který je naplněn komentáři v souborech zdrojového kódu kompilace.</span><span class="sxs-lookup"><span data-stu-id="1c043-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c043-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c043-107">Remarks</span></span>  
 <span data-ttu-id="1c043-108">V souborech zdrojového kódu mohou být komentáře dokumentace, které předcházejí následujícím uvažování, zpracovány a přidány do souboru XML:</span><span class="sxs-lookup"><span data-stu-id="1c043-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="1c043-109">Takové uživatelem definované typy jako [třída](../keywords/class.md), [delegát](../builtin-types/reference-types.md#the-delegate-type)nebo [rozhraní](../keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="1c043-109">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="1c043-110">Takové členy jako pole, [událost](../keywords/event.md), [vlastnost](../../programming-guide/classes-and-structs/using-properties.md)nebo metoda</span><span class="sxs-lookup"><span data-stu-id="1c043-110">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="1c043-111">Soubor zdrojového kódu, který obsahuje Main je výstup první do XML.</span><span class="sxs-lookup"><span data-stu-id="1c043-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="1c043-112">Chcete-li použít generovaný soubor XML pro použití s funkcí [IntelliSense,](/visualstudio/ide/using-intellisense) nechte název souboru XML stejný jako sestavení, které chcete podporovat, a poté se ujistěte, že soubor XML je ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c043-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="1c043-113">Proto při odkazování na sestavení v projektu sady Visual Studio je nalezen také soubor XML.</span><span class="sxs-lookup"><span data-stu-id="1c043-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="1c043-114">Další informace naleznete [v tématu Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and For more information.</span><span class="sxs-lookup"><span data-stu-id="1c043-114">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="1c043-115">Pokud kompilujete s `file` [-target:module](./target-module-compiler-option.md), bude obsahovat \<sestavení>\</assembly> značky určující název souboru obsahujícímanifest sestavení pro výstupní soubor kompilace.</span><span class="sxs-lookup"><span data-stu-id="1c043-115">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c043-116">Možnost -doc platí pro všechny vstupní soubory; nebo, pokud je nastavena v nastavení projektu, všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="1c043-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="1c043-117">Chcete-li zakázat upozornění týkající se poznámek k dokumentaci pro určitý soubor nebo část kódu, použijte [#pragma upozornění](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="1c043-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="1c043-118">Způsoby generování dokumentace z komentářů v kódu najdete v [tématu Doporučené značky pro komentáře k dokumentaci.](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)</span><span class="sxs-lookup"><span data-stu-id="1c043-118">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1c043-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1c043-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1c043-120">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="1c043-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1c043-121">Klikněte na kartu **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="1c043-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="1c043-122">Upravte vlastnost **souboru dokumentace XML.**</span><span class="sxs-lookup"><span data-stu-id="1c043-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="1c043-123">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="1c043-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c043-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c043-124">See also</span></span>

- [<span data-ttu-id="1c043-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c043-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1c043-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1c043-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
