---
title: 'Postupy: Analýza cest k souborům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 7479f368558a8a8a07c1e6ed588bdfef21a0b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585941"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="b1a44-102">Postupy: Analýza cest k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1a44-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="b1a44-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> Objekt nabízí řadu užitečných metod při analýze cesty k souborům.</span><span class="sxs-lookup"><span data-stu-id="b1a44-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="b1a44-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda přebírá dvě cesty a vrátí správně formátovaný kombinovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="b1a44-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="b1a44-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda vrátí absolutní cesta nadřazenou zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="b1a44-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="b1a44-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda vrátí <xref:System.IO.FileInfo> objekt, který může být dotazován k určení vlastností souboru, například jeho název a cesta.</span><span class="sxs-lookup"><span data-stu-id="b1a44-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="b1a44-107">Neprovádějte rozhodnutí o obsahu souboru na základě přípony názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="b1a44-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="b1a44-108">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b1a44-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="b1a44-109">Chcete-li zjistit název a cesta souboru</span><span class="sxs-lookup"><span data-stu-id="b1a44-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="b1a44-110">Použití <xref:System.IO.FileInfo.DirectoryName%2A> a <xref:System.IO.FileInfo.Name%2A> vlastnosti <xref:System.IO.FileInfo> objektem pro určení název a cesta souboru.</span><span class="sxs-lookup"><span data-stu-id="b1a44-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="b1a44-111">Tento příklad určuje název a cestu a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="b1a44-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="b1a44-112">Kombinování název a directory k vytvoření úplnou cestu souboru</span><span class="sxs-lookup"><span data-stu-id="b1a44-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="b1a44-113">Použití `CombinePath` metody adresáře a název.</span><span class="sxs-lookup"><span data-stu-id="b1a44-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="b1a44-114">Tento příklad zpracuje řetězce `folderPath` a `fileName` vytvořili v předchozím příkladu je kombinuje a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="b1a44-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b1a44-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1a44-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [<span data-ttu-id="b1a44-116">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="b1a44-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
