---
title: 'Postupy: Připojování k textovým souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348874"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Postupy: Připojování k textovým souborům v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> lze použít k připojení k textovému souboru zadáním, že `append` parametr je nastaven na `True`.  
  
### <a name="to-append-to-a-text-file"></a>Připojení k textovému souboru  
  
- Použijte `WriteAllText` metodu, určení cílového souboru a řetězce, `append` který `True`má být připojen, a nastavení parametru na .  
  
     Tento příklad zapíše řetězec `"This is a test string."` `Testfile.txt`do souboru s názvem .  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- `File`odkazuje na cestu, která<xref:System.IO.FileNotFoundException> neexistuje <xref:System.IO.DirectoryNotFoundException>( nebo ).  
  
- Soubor je používán jiným procesem nebo dojde k chybě<xref:System.IO.IOException>vstupně-out ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
