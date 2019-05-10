---
title: 'Postupy: Vytvořte soubor v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: f24fdd6ce1fea7540c33e4a2fdfc06885825f76a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628985"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Postupy: Vytvořte soubor v jazyce Visual Basic
Tento příklad vytvoří prázdný textový soubor v zadané cesty pomocí <xref:System.IO.File.Create%2A> metodu <xref:System.IO.File> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Použití `file` proměnné k zápisu do souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud soubor již existuje, nahradí se.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název cesty je poškozený. Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException>).  
  
- Cesta je jen pro čtení (<xref:System.IO.IOException>).  
  
- Název cesty je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException>).  
  
- Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException>).  
  
- Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 A <xref:System.Security.SecurityException> může být vyvolána v prostředí částečné důvěryhodnosti.  
  
 Volání <xref:System.IO.File.Create%2A> metoda vyžaduje <xref:System.Security.Permissions.FileIOPermission>.  
  
 <xref:System.UnauthorizedAccessException> Je vyvolána, pokud uživatel nemá oprávnění k vytvoření souboru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Používání knihoven z částečně důvěryhodného kódu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md)
