---
title: 'Postupy: Vytvoření adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: a7ba9ea1e7762b0a4a6660339c331fa6cdeb7858
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976899"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Postupy: Vytvoření adresáře v jazyce Visual Basic
Použití `CreateDirectory` metodu `My.Computer.FileSystem` objekt k vytvoření adresáře.  
  
 Pokud adresář již existuje, není vyvolána žádná výjimka.  
  
### <a name="to-create-a-directory"></a>K vytvoření adresáře  
  
-   Použití `CreateDirectory` metoda zadáním úplné cesty umístění, kde by měl být vytvořen adresář. Tento příklad vytvoří adresář `NewDirectory` v `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název adresáře je poškozený. Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException>).  
  
-   Nadřazený adresář složky adresář, který má být vytvořen je jen pro čtení (<xref:System.IO.IOException>).  
  
-   Název adresáře je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Název adresáře je příliš dlouhý (<xref:System.IO.PathTooLongException>).  
  
-   Název adresáře je dvojtečka ":" (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá oprávnění k vytvoření adresáře (<xref:System.UnauthorizedAccessException>).  
  
-   Uživatel nemá oprávnění v situacích částečné důvěryhodnosti (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
