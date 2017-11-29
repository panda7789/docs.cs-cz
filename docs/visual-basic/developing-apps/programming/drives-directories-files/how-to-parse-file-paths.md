---
title: "Postupy: Analýza cest k souborům v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 913fe45cf6fc7afdc6e0f31e028bc18808cecf89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Postupy: Analýza cest k souborům v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem> Objekt nabízí řadu užitečných metod při analýze cesty k souborům.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda přebírá dvě cesty a vrátí správně formátovaný kombinovanou cestu.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda vrátí absolutní cesta nadřazenou zadané cestě.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda vrátí <xref:System.IO.FileInfo> objekt, který může být dotazován k určení vlastností souboru, například jeho název a cesta.  
  
 Neprovádějte rozhodnutí o obsahu souboru na základě přípony názvu souboru. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Chcete-li zjistit název a cesta souboru  
  
-   Použití <xref:System.IO.FileInfo.DirectoryName%2A> a <xref:System.IO.FileInfo.Name%2A> vlastnosti <xref:System.IO.FileInfo> objektem pro určení název a cesta souboru. Tento příklad určuje název a cestu a zobrazí je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Kombinování název a directory k vytvoření úplnou cestu souboru  
  
-   Použití `CombinePath` metody adresáře a název. Tento příklad zpracuje řetězce `folderPath` a `fileName` vytvořili v předchozím příkladu je kombinuje a zobrazí výsledek.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [Postupy: získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
