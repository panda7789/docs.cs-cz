---
title: 'Postupy: Vytvoření adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348803"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Postupy: Vytvoření adresáře v jazyce Visual Basic

K vytvoření adresáře použijte metodu `CreateDirectory` objektu `My.Computer.FileSystem`.  
  
 Pokud adresář již existuje, není vyvolána žádná výjimka.  
  
### <a name="to-create-a-directory"></a>Vytvoření adresáře  
  
- Použijte metodu `CreateDirectory` zadáním úplné cesty k umístění, kde má být adresář vytvořen. Tento příklad vytvoří adresář `NewDirectory` v `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Název adresáře je poškozený. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).  
  
- Nadřazený adresář adresáře, který se má vytvořit, je jen pro čtení (<xref:System.IO.IOException>).  
  
- Název adresáře je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Název adresáře je příliš dlouhý (<xref:System.IO.PathTooLongException>).  
  
- Název adresáře je dvojtečka ":" (<xref:System.NotSupportedException>).  
  
- Uživatel nemá oprávnění k vytvoření adresáře (<xref:System.UnauthorizedAccessException>).  
  
- Uživatel nemá oprávnění v situaci s částečnou důvěryhodností (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
