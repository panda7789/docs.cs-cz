---
title: 'Postupy: Připojování k textovým souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348874"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Postupy: Připojování k textovým souborům v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> lze použít pro připojení k textovému souboru zadáním, že parametr `append` je nastaven na hodnotu `True`.  
  
### <a name="to-append-to-a-text-file"></a>Připojení k textovému souboru  
  
- Použijte metodu `WriteAllText`, určete cílový soubor a řetězec, který se má připojit, a nastavte parametr `append` na `True`.  
  
     Tento příklad zapíše řetězec `"This is a test string."` do souboru s názvem `Testfile.txt`.  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).  
  
- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
