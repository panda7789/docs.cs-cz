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
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Postupy: Analýza cest k souborům v jazyce Visual Basic

Objekt <xref:Microsoft.VisualBasic.FileIO.FileSystem> nabízí několik užitečných metod při analýze cest k souborům.  
  
- Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> přebírá dvě cesty a vrací správně naformátovanou kombinovanou cestu.  
  
- Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> vrátí absolutní cestu nadřazeného objektu v zadané cestě.  
  
- Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> vrátí objekt <xref:System.IO.FileInfo>, ke kterému se dá dotázat, aby se určily vlastnosti souboru, jako je jeho název a cesta.  
  
 Neprovádějte rozhodnutí o obsahu souboru na základě přípony názvu souboru. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.  
  
### <a name="to-determine-a-files-name-and-path"></a>Určení názvu a cesty k souboru  
  
- Pomocí vlastností <xref:System.IO.FileInfo.DirectoryName%2A> a <xref:System.IO.FileInfo.Name%2A> objektu <xref:System.IO.FileInfo> určete název souboru a cestu. Tento příklad určuje název a cestu a zobrazí je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Kombinování názvu souboru a adresáře pro vytvoření úplné cesty  
  
- Použijte metodu `CombinePath` a zadejte adresář a název. Tento příklad přebírá řetězce `folderPath` a `fileName` vytvořené v předchozím příkladu, kombinuje je a zobrazí výsledek.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
