---
title: 'Postupy: Načíst obsah adresáři MyDocuments v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: f03dbe1811dd5367dab2d32d94ba35ff05fad198
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623152"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Postupy: Načíst obsah adresáři MyDocuments v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Objekt lze použít ke čtení z mnoha **všichni uživatelé** adresáře, jako například **dokumenty** nebo **Desktop**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Čtení ze složky Dokumenty  
  
- Použití `ReadAllText` metodu za účelem čtení textu z každého souboru v konkrétním adresáři. Následující kód určuje adresář a soubor a potom použije `ReadAllText` pro načtení do řetězce s názvem `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
