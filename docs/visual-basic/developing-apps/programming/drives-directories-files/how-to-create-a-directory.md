---
title: 'Postupy: Vytvoření adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 0da915054a2e38c778f15bc0b472fe9b02521189
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401664"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Postupy: Vytvoření adresáře v jazyce Visual Basic

Použijte `CreateDirectory` metodu `My.Computer.FileSystem` objektu k vytvoření adresáře.  
  
 Pokud adresář již existuje, není vyvolána žádná výjimka.  
  
### <a name="to-create-a-directory"></a>Vytvoření adresáře  
  
- Použijte metodu zadáním `CreateDirectory` úplné cesty k umístění, kde má být adresář vytvořen. Tento příklad vytvoří adresář `NewDirectory` v `C:\Documents and Settings\All Users\Documents` .  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Název adresáře je poškozený. Například obsahuje neplatné znaky nebo je pouze mezera ( <xref:System.ArgumentException> ).  
  
- Nadřazený adresář adresáře, který se má vytvořit, je jen pro čtení ( <xref:System.IO.IOException> ).  
  
- Název adresáře je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Název adresáře je příliš dlouhý ( <xref:System.IO.PathTooLongException> ).  
  
- Název adresáře je dvojtečka ":" ( <xref:System.NotSupportedException> ).  
  
- Uživatel nemá oprávnění k vytvoření adresáře ( <xref:System.UnauthorizedAccessException> ).  
  
- Uživatel nemá oprávnění v situaci s částečným vztahem důvěryhodnosti ( <xref:System.Security.SecurityException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Vytváření, odstraňování a přesouvání souborů a adresářů](creating-deleting-and-moving-files-and-directories.md)
