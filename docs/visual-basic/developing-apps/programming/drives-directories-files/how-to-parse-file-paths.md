---
title: 'Postupy: Analýza cest k souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335353"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Postupy: Analýza cest k souborům v jazyce Visual Basic

Objekt <xref:Microsoft.VisualBasic.FileIO.FileSystem> nabízí řadu užitečných metod při analýzě cest souborů.  
  
- Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> trvá dvě cesty a vrátí správně formátované kombinované cesty.  
  
- Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> vrátí absolutní cestu nadřazené cesty zapředpokladu.  
  
- Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> vrátí <xref:System.IO.FileInfo> objekt, který může být dotazován k určení vlastností souboru, jako je například jeho název a cesta.  
  
 Neprovávejte rozhodování o obsahu souboru na základě přípony názvu souboru. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Určení názvu a cesty souboru  
  
- Pomocí <xref:System.IO.FileInfo.DirectoryName%2A> vlastností objektu <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> určete název a cestu souboru. Tento příklad určuje název a cestu a zobrazí je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Sloučení názvu a adresáře souboru za účelem vytvoření úplné cesty  
  
- Použijte `CombinePath` metodu, zadání adresáře a název. Tento příklad bere `folderPath` řetězce `fileName` a vytvořené v předchozím příkladu, kombinuje je a zobrazí výsledek.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
