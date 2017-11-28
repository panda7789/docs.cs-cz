---
title: "Postupy: Vytvoření adresáře v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e4cd94113d77b2f4ff8127c80174107966ef360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
