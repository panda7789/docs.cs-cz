---
title: 'Postupy: Načtení obsahu adresáře Moje dokumenty v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 1d0536c65949dab7d431f3a4cb7b3293bddb7008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Postupy: Načtení obsahu adresáře Moje dokumenty v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Objekt můžete použít ke čtení z mnoha **všichni uživatelé** adresáře, jako například **dokumenty** nebo **plochy**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Číst ze složky Dokumenty  
  
-   Použití `ReadAllText` metoda číst text z každého souboru v konkrétní adresář. Následující kód určuje adresáře a souboru a pak používá `ReadAllText` k jejich načtení do řetězec s názvem `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
