---
title: 'Postupy: Načíst obsah adresáři MyDocuments v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: fe98d3e92726dc6c4ed576ef989d968852c846d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770292"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Postupy: Načíst obsah adresáři MyDocuments v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Objekt lze použít ke čtení z mnoha **všichni uživatelé** adresáře, jako například **dokumenty** nebo **Desktop**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Čtení ze složky Dokumenty  
  
-   Použití `ReadAllText` metodu za účelem čtení textu z každého souboru v konkrétním adresáři. Následující kód určuje adresář a soubor a potom použije `ReadAllText` pro načtení do řetězce s názvem `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
