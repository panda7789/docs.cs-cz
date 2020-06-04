---
title: 'Postupy: Analýza cest k souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: eb7714a8594c0bce344eb2e48ebc5053dc3bfbb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359939"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Postupy: Analýza cest k souborům v jazyce Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem>Objekt nabízí řadu užitečných metod při analýze cest k souborům.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>Metoda přijímá dvě cesty a vrací správně naformátovanou kombinovanou cestu.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A>Metoda vrátí absolutní cestu nadřazeného objektu v zadané cestě.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>Metoda vrátí <xref:System.IO.FileInfo> objekt, na který lze zadat dotaz, aby bylo možné určit vlastnosti souboru, jako je například jeho název a cesta.  
  
 Neprovádějte rozhodnutí o obsahu souboru na základě přípony názvu souboru. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.  
  
### <a name="to-determine-a-files-name-and-path"></a>Určení názvu a cesty k souboru  
  
- Pomocí <xref:System.IO.FileInfo.DirectoryName%2A> vlastností a <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> objektu určete název a cestu souboru. Tento příklad určuje název a cestu a zobrazí je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Kombinování názvu souboru a adresáře pro vytvoření úplné cesty  
  
- Použijte `CombinePath` metodu, která poskytuje název adresáře a názvu. Tento příklad přebírá řetězce `folderPath` a `fileName` vytvoří v předchozím příkladu, kombinuje je a zobrazí výsledek.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Postupy: Získání kolekce souborů z adresáře](how-to-get-the-collection-of-files-in-a-directory.md)
