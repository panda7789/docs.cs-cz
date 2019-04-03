---
title: 'Postupy: Analýza cest k souborům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: c089910e3fd5d02b674cfed3062fb15275d91486
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834605"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="9ffb8-102">Postupy: Analýza cest k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ffb8-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="9ffb8-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> Objekt nabízí celou řadu užitečných metod při analýze cesty k souborům.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="9ffb8-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda přijímá dvě cesty a vrátí správně formátovaná kombinovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="9ffb8-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda vrátí absolutní cesta nadřazeného člena zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="9ffb8-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda vrátí hodnotu <xref:System.IO.FileInfo> objekt, který může být dotazována k určení vlastností souboru, například jeho název a cesta.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="9ffb8-107">Rozhodování o obsahu souboru neřiďte příponou názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="9ffb8-108">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="9ffb8-109">Chcete-li zjistit název a cesta k souboru</span><span class="sxs-lookup"><span data-stu-id="9ffb8-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="9ffb8-110">Použití <xref:System.IO.FileInfo.DirectoryName%2A> a <xref:System.IO.FileInfo.Name%2A> vlastnosti <xref:System.IO.FileInfo> objektu určit název a cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="9ffb8-111">Tento příklad určuje název a cestu a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="9ffb8-112">Kombinovat adresář k vytvoření úplnou cestu a název souboru</span><span class="sxs-lookup"><span data-stu-id="9ffb8-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="9ffb8-113">Použití `CombinePath` metodu adresáře a názvu.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="9ffb8-114">V tomto příkladu přebírá řetězce `folderPath` a `fileName` vytvořili v předchozím příkladu, sloučí a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="9ffb8-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="9ffb8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ffb8-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="9ffb8-116">Postupy: Získání kolekce souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="9ffb8-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
