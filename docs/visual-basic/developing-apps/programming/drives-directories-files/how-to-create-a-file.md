---
title: 'Postupy: Vytvoření souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348798"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Postupy: Vytvoření souboru v jazyce Visual Basic

Tento příklad vytvoří prázdný textový soubor v zadané cestě pomocí metody <xref:System.IO.File.Create%2A> ve třídě <xref:System.IO.File>.  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 K zápisu do souboru použijte proměnnou `file`.  
  
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

 <xref:System.Security.SecurityException> může být vyvolána v prostředích s částečnou důvěryhodností.  
  
 Volání metody <xref:System.IO.File.Create%2A> vyžaduje <xref:System.Security.Permissions.FileIOPermission>.  
  
 Pokud uživatel nemá oprávnění k vytvoření souboru, je vyvolána <xref:System.UnauthorizedAccessException>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Používání knihoven z částečně důvěryhodného kódu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md)
