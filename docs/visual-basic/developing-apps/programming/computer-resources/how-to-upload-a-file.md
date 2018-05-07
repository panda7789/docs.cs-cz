---
title: 'Postupy: Odeslání souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 769c04430f8323dfde680fca45cfcd67809bdab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Postupy: Odeslání souboru v jazyce Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metoda slouží k nahrání souboru a jeho uložení do vzdáleného umístění. Pokud `ShowUI` parametr je nastaven na `True`, se zobrazí dialogové okno, které zobrazuje průběh nahrávání a umožňuje uživatelům na tlačítko Storno.  
  
### <a name="to-upload-a-file"></a>Pro nahrání souboru  
  
-   Použití `UploadFile` metodu pro nahrání souboru, zadáte umístění zdrojových souborů a cílové umístění adresáře jako řetězec nebo identifikátor URI (Uniform Resource Identifier). Tento příklad nahrávání souboru `Order.txt` k `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Nahrát soubor a zobrazit průběh operace  
  
-   Použití `UploadFile` metodu pro nahrání souboru, zadáte umístění zdrojových souborů a cílové umístění adresáře jako řetězec nebo identifikátor URI. Tento příklad nahrávání souboru `Order.txt` k `http://www.cohowinery.com/uploads.aspx` bez uživatelské jméno a heslo, zobrazí průběh nahrávání a interval časového limitu na 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Nahrát soubor s poskytnutím uživatelské jméno a heslo  
  
-   Použití `UploadFile` metodu pro nahrání souboru, zadáním umístění zdrojových souborů a cílové umístění adresáře jako řetězec nebo identifikátor URI a uživatelské jméno a heslo. Tento příklad nahrávání souboru `Order.txt` k `http://www.cohowinery.com/uploads.aspx`, poskytuje uživatelské jméno `anonymous` a prázdné heslo.  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následujících podmínek může vyvolat výjimku:  
  
-   Cestu k místnímu souboru není platný (<xref:System.ArgumentException>).  
  
-   Ověření se nezdařilo (<xref:System.Security.SecurityException>).  
  
-   Vypršel časový limit připojení (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>  
 [Postupy: Stažení souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
