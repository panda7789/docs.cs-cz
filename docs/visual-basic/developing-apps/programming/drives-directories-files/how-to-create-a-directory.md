---
title: 'Postupy: Vytvoření adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348803"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Postupy: Vytvoření adresáře v jazyce Visual Basic

Pomocí `CreateDirectory` metody objektu `My.Computer.FileSystem` vytvořte adresáře.  
  
 Pokud adresář již existuje, není vyvolána žádná výjimka.  
  
### <a name="to-create-a-directory"></a>Vytvoření adresáře  
  
- Metodu `CreateDirectory` použijte zadáním úplné cesty k umístění, kde by měl být adresář vytvořen. Tento příklad vytvoří `NewDirectory` `C:\Documents and Settings\All Users\Documents`adresář v .  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Název adresáře je poškozen. Obsahuje například neplatné znaky nebo je<xref:System.ArgumentException>pouze prázdné znaky ( ).  
  
- Nadřazený adresář adresáře, který<xref:System.IO.IOException>má být vytvořen, je jen pro čtení ( .  
  
- Název adresáře `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- Název adresáře je<xref:System.IO.PathTooLongException>příliš dlouhý ( ).  
  
- Název adresáře je dvojtečka ":" (<xref:System.NotSupportedException>).  
  
- Uživatel nemá oprávnění k vytvoření adresáře (<xref:System.UnauthorizedAccessException>).  
  
- Uživatel nemá oprávnění v situaci částečné<xref:System.Security.SecurityException>důvěryhodnosti ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
