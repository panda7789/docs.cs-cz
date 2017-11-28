---
title: "Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c4549f417e86e82897ca32d8d7cf22aaf462c90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda vrátí kolekci jen pro čtení řetězce představující názvy cest pro podadresáře v adresáři. Můžete použít `wildCards` parametr k určení specifického vzoru. Pokud chcete zahrnout obsah podadresářů hledání, nastavte `searchType` parametru `SearchOption.SearchAllSubDirectories`.  
  
 Prázdná kolekce je vrácena, pokud se nenajdou žádné adresáře odpovídající zadanému vzoru.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>K hledání podadresářů pomocí specifického vzoru  
  
-   Použití `GetDirectories` metodu název a cestu k adresáři, kterou chcete vyhledat. Následující příklad vrátí všechny adresáře struktury adresářů, obsahující slovo "Protokoly" v názvu a přidá je do `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Jeden nebo více zadaný zástupné znaky je `Nothing`, prázdný řetězec, nebo obsahuje pouze mezery (<xref:System.ArgumentNullException>).  
  
-   `directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory`ukazuje na existující soubor (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [Postupy: hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
