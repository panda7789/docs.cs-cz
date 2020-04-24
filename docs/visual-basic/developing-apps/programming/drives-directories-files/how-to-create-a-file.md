---
title: 'Postupy: Vytvoření souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348798"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Postupy: Vytvoření souboru v jazyce Visual Basic

Tento příklad vytvoří prázdný textový soubor v zadané cestě pomocí <xref:System.IO.File.Create%2A> metody ve <xref:System.IO.File> třídě.  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Použijte `file` proměnnou k zápisu do souboru.  
  
## <a name="robust-programming"></a>Robustní programování  

 Pokud soubor již existuje, je nahrazen.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název cesty je poškozen. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).  
  
- Cesta je určena jen pro čtení (<xref:System.IO.IOException>).  
  
- Název cesty je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException>).  
  
- Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException>).  
  
- Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 <xref:System.Security.SecurityException> Může být vyvolána v prostředích s částečnou důvěryhodností.  
  
 Volání <xref:System.IO.File.Create%2A> metody vyžaduje <xref:System.Security.Permissions.FileIOPermission>.  
  
 Pokud <xref:System.UnauthorizedAccessException> uživatel nemá oprávnění k vytvoření souboru, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Používání knihoven z částečně důvěryhodného kódu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md)
