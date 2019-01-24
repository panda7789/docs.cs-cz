---
title: 'Postupy: Načíst obsah adresáři MyDocuments v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 6313ebd190a6cee8a697399e2e77b63d8c43db2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602582"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="fbd04-102">Postupy: Načíst obsah adresáři MyDocuments v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbd04-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="fbd04-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Objekt lze použít ke čtení z mnoha **všichni uživatelé** adresáře, jako například **dokumenty** nebo **Desktop**.</span><span class="sxs-lookup"><span data-stu-id="fbd04-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="fbd04-104">Čtení ze složky Dokumenty</span><span class="sxs-lookup"><span data-stu-id="fbd04-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="fbd04-105">Použití `ReadAllText` metodu za účelem čtení textu z každého souboru v konkrétním adresáři.</span><span class="sxs-lookup"><span data-stu-id="fbd04-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="fbd04-106">Následující kód určuje adresář a soubor a potom použije `ReadAllText` pro načtení do řetězce s názvem `patients`.</span><span class="sxs-lookup"><span data-stu-id="fbd04-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fbd04-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbd04-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
