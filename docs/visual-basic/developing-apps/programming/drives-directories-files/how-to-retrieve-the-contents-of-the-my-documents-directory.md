---
title: "Postupy: Načtení obsahu adresáře Moje dokumenty v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3456984a697439a8c2ab7fb88f9f0f32d10cb0e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Postupy: Načtení obsahu adresáře Moje dokumenty v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Objekt můžete použít ke čtení z mnoha **všichni uživatelé** adresáře, jako například **dokumenty** nebo **plochy**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Číst ze složky Dokumenty  
  
-   Použití `ReadAllText` metoda číst text z každého souboru v konkrétní adresář. Následující kód určuje adresáře a souboru a pak používá `ReadAllText` k jejich načtení do řetězec s názvem `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
