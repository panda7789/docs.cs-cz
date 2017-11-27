---
title: "Postupy: Vytvoření souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Postupy: Vytvoření souboru v jazyce Visual Basic
Tento příklad vytvoří prázdný textový soubor v zadané cestě pomocí <xref:System.IO.File.Create%2A> metoda v <xref:System.IO.File> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Použití `file` proměnná k zápisu do souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud soubor již existuje, je nahradit.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název cesty je chybný. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).  
  
-   Cesta je jen pro čtení (<xref:System.IO.IOException>).  
  
-   Název cesty je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException>).  
  
-   Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 A <xref:System.Security.SecurityException> může být vyvolána v prostředí s částečným vztahem důvěryhodnosti.  
  
 Volání <xref:System.IO.File.Create%2A> metoda vyžaduje <xref:System.Security.Permissions.FileIOPermission>.  
  
 <xref:System.UnauthorizedAccessException> Je vyvolána, pokud uživatel nemá oprávnění k vytvoření souboru.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [Používání knihoven z částečně důvěryhodného kódu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [Základy zabezpečení přístupu kódu](https://msdn.microsoft.com/library/33tceax8)
