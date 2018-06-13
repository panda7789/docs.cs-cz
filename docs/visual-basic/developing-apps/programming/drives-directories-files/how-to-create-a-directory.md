---
title: 'Postupy: Vytvoření adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: ec9ee01e17f116e80708dbcb34e4d804bf3d7a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583952"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Postupy: Vytvoření adresáře v jazyce Visual Basic
Použití `CreateDirectory` metodu `My.Computer.FileSystem` objekt k vytvoření adresáře.  
  
 Pokud adresář již existuje, je vyvolána žádná výjimka.  
  
### <a name="to-create-a-directory"></a>K vytvoření adresáře  
  
-   Použití `CreateDirectory` metoda zadáním úplnou cestu k umístění, kde se vytvořit adresář. Tento příklad vytvoří adresář `NewDirectory` v `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název adresáře je poškozený. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).  
  
-   Nadřazeném adresáři vytvořen adresář je jen pro čtení (<xref:System.IO.IOException>).  
  
-   Název adresáře je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Název adresáře je příliš dlouhý (<xref:System.IO.PathTooLongException>).  
  
-   Název adresáře je dvojtečkou ":" (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá oprávnění vytvořit adresář (<xref:System.UnauthorizedAccessException>).  
  
-   Uživatel nemá oprávnění v situaci, částečným vztahem důvěryhodnosti (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
