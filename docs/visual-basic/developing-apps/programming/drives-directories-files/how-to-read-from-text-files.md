---
title: "Postupy: Čtení z textových souborů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f75d89fb4ab10a8c116d4a0ab79c17ceb3efd0ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Postupy: Čtení z textových souborů v jazyce Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metodu `My.Computer.FileSystem` objekt umožňuje čtení z textového souboru. Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.  
  
 Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.  
  
> [!NOTE]
>  Pokud chcete přečíst jeden řádek textu souboru, použijte <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metodu `My.Computer.FileSystem` objektu. `OpenTextFileReader` Metoda vrátí <xref:System.IO.StreamReader> objektu. Můžete použít <xref:System.IO.StreamReader.ReadLine%2A> metodu `StreamReader` objektu určeného ke čtení souboru jeden řádek v čase. Můžete otestovat na konci souboru pomocí <xref:System.IO.StreamReader.EndOfStream%2A> metodu `StreamReader` objektu.  
  
### <a name="to-read-from-a-text-file"></a>Čtení z textového souboru  
  
-   Použití `ReadAllText` metodu `My.Computer.FileSystem` objektu určeného ke čtení obsahu textového souboru do řetězce cesty. Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Čtení z textového souboru s kódováním  
  
-   Použití `ReadAllText` metodu `My.Computer.FileSystem` objekt k načtení obsahu textového souboru do řetězce cesty a souboru typ kódování. Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Není dostatek paměti pro zápis řetězec do vyrovnávací paměti (<xref:System.OutOfMemoryException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zdrojový soubor.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>  
 [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Postupy: čtení z oddělených čárkou textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Postupy: čtení z textových souborů s pevnou délkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [Postupy: čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [Řešení potíží: Čtení a zápis do textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [Návod: Manipulace se soubory a adresáře v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
