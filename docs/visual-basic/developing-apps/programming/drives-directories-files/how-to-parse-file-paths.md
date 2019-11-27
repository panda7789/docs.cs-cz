---
title: 'Postupy: Analýza cest k souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335353"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="7eb6b-102">Postupy: Analýza cest k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7eb6b-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="7eb6b-103">Objekt <xref:Microsoft.VisualBasic.FileIO.FileSystem> nabízí několik užitečných metod při analýze cest k souborům.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="7eb6b-104">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> přebírá dvě cesty a vrací správně naformátovanou kombinovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="7eb6b-105">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> vrátí absolutní cestu nadřazeného objektu v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="7eb6b-106">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> vrátí objekt <xref:System.IO.FileInfo>, ke kterému se dá dotázat, aby se určily vlastnosti souboru, jako je jeho název a cesta.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="7eb6b-107">Neprovádějte rozhodnutí o obsahu souboru na základě přípony názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="7eb6b-108">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="7eb6b-109">Určení názvu a cesty k souboru</span><span class="sxs-lookup"><span data-stu-id="7eb6b-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="7eb6b-110">Pomocí vlastností <xref:System.IO.FileInfo.DirectoryName%2A> a <xref:System.IO.FileInfo.Name%2A> objektu <xref:System.IO.FileInfo> určete název souboru a cestu.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="7eb6b-111">Tento příklad určuje název a cestu a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="7eb6b-112">Kombinování názvu souboru a adresáře pro vytvoření úplné cesty</span><span class="sxs-lookup"><span data-stu-id="7eb6b-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="7eb6b-113">Použijte metodu `CombinePath` a zadejte adresář a název.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="7eb6b-114">Tento příklad přebírá řetězce `folderPath` a `fileName` vytvořené v předchozím příkladu, kombinuje je a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="7eb6b-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="7eb6b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eb6b-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="7eb6b-116">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="7eb6b-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
