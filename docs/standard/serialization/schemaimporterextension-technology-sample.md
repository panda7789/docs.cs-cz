---
title: Ukázka technologie SchemaImporterExtension
ms.date: 03/30/2017
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
ms.openlocfilehash: 042ea9eecb7820d4ffb88bdb8862aec1e7f6e483
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042488"
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="4eb02-102">Ukázka technologie SchemaImporterExtension</span><span class="sxs-lookup"><span data-stu-id="4eb02-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="4eb02-103">Stáhněte si ukázky</span><span class="sxs-lookup"><span data-stu-id="4eb02-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="4eb02-104">Tento příklad znázorňuje vlastní <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> , který umožňuje přesné řízení generování kódu, když je importován schématu XML.</span><span class="sxs-lookup"><span data-stu-id="4eb02-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="4eb02-105">Aplikace ukazuje, jak vytvářet, registrace a vyvolání tohoto rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4eb02-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="4eb02-106">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="4eb02-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="4eb02-107">Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="4eb02-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="4eb02-108">Typ **msbuild.exe OrderSchemaImporterExtension.sln** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="4eb02-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="4eb02-109">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4eb02-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="4eb02-110">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="4eb02-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="4eb02-111">Poklepejte na ikonu OrderSchemaImporterExtension.sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4eb02-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="4eb02-112">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="4eb02-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="4eb02-113">Aplikace bude vytvořen v adresáři \bin nebo \bin\Debug výchozí.</span><span class="sxs-lookup"><span data-stu-id="4eb02-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="4eb02-114">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4eb02-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="4eb02-115">Přejděte do adresáře, který obsahuje novou spustitelný soubor, pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4eb02-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="4eb02-116">Typ **[exe name]** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="4eb02-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eb02-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4eb02-117">Remarks</span></span>  
 <span data-ttu-id="4eb02-118">Další informace o vytváření binární ukázky a registraci kroky naleznete v tématu komentáře v souborech zdrojového kódu a build.proj.</span><span class="sxs-lookup"><span data-stu-id="4eb02-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb02-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4eb02-119">See also</span></span>

- <xref:System.CodeDom.CodeCompileUnit>  
- <xref:System.CodeDom.CodeNamespace>  
- <xref:System.CodeDom.CodeNamespaceImport>  
- <xref:Microsoft.CSharp.CSharpCodeProvider>  
- <xref:System.Xml.Serialization.IXmlSerializable>  
- <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>  
- <xref:System.CodeDom>  
- <xref:System.CodeDom.Compiler>  
- <xref:System.Web.Services.Description>  
- <xref:System.Web.Services.Discovery>  
- <xref:System.Xml.Serialization>  
- <xref:System.Uri>  
- <xref:Microsoft.VisualBasic.VBCodeProvider>  
- <xref:System.Web.Services.Description.WebReference>  
- <xref:System.Xml.Serialization.XmlSchemaImporter>
