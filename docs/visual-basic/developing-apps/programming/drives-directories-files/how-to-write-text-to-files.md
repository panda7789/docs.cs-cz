---
title: 'Postupy: Zápis textu do souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334464"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Postupy: Zápis textu do souborů v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> lze použít k zápisu textu do souborů. Pokud zadaný soubor neexistuje, je vytvořen.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-text-to-a-file"></a>Zápis textu do souboru  
  
- Pomocí `WriteAllText` metody zapište text do souboru a zadejte soubor a text, který se má zapsat. Tento příklad zapíše řádek `"This is new text."` `test.txt`do souboru s názvem , připojí text k existujícímu textu v souboru.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Zápis řady řetězců do souboru  
  
- Smyčka prostřednictvím kolekce řetězce. Pomocí `WriteAllText` metody zapište text do souboru, určete cílový soubor `append` a `True`řetězec, který má být přidán, a nastavení na soubor .  
  
     Tento příklad zapisuje `Documents and Settings` názvy `FileList.txt`souborů v adresáři do , vložení matný návrat mezi každý pro lepší čitelnost.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- `File`odkazuje na cestu, která<xref:System.IO.FileNotFoundException> neexistuje <xref:System.IO.DirectoryNotFoundException>( nebo ).  
  
- Soubor je používán jiným procesem nebo dojde k chybě<xref:System.IO.IOException>vstupně-out ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
- Disk je plný a volání `WriteAllText` nezdaří (<xref:System.IO.IOException>).  
  
 Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Postup: Čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
