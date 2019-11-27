---
title: 'Postupy: Načtení obsahu adresáře Moje dokumenty'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: cf4470020507c581999b9d72602ddb6e3e76ed74
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334539"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Postupy: Načtení obsahu adresáře Moje dokumenty v jazyce Visual Basic

Objekt <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> lze použít ke čtení z mnoha adresářů **všech uživatelů** , jako jsou **dokumenty** nebo **plocha**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Čtení ze složky Dokumenty  
  
- Pomocí metody `ReadAllText` si můžete přečíst text z každého souboru v konkrétním adresáři. Následující kód určuje adresář a soubor a poté používá `ReadAllText` ke čtení do řetězce s názvem `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
