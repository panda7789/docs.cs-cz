---
title: 'Postupy: Vytvoření souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 6167ea0850308eec4b558a47dd881476325a8ea1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md)
