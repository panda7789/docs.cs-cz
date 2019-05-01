---
title: 'Postupy: Nahrát soubor v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 486351bc140a2bbf18bb8f85f761fc491f028bba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013891"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Postupy: Nahrát soubor v jazyce Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metodu je možné nahrát soubor a uloží je do vzdáleného umístění. Pokud `ShowUI` parametr je nastaven na `True`, se zobrazí dialogové okno, které zobrazí průběh nahrávání a umožňuje uživatelům na zrušení operace.  
  
### <a name="to-upload-a-file"></a>Pokud chcete nahrát soubor  
  
- Použití `UploadFile` metodu pro nahrání souboru, zadáte umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI (Uniform Resource Identifier). Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Nahrát soubor a zobrazí průběh operace  
  
- Použití `UploadFile` metodu pro nahrání souboru, jako řetězec nebo identifikátor URI určující umístění zdrojového souboru a umístění cílového adresáře. Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx` bez uživatelského jména a hesla, zobrazí se průběh nahrávání a má interval časového limitu 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Pokud chcete nahrát soubor, zadáním uživatelského jména a hesla  
  
- Použití `UploadFile` metodu pro nahrání souboru, jako řetězec nebo identifikátor URI určující umístění zdrojového souboru a umístění cílového adresáře a uživatelské jméno a heslo. Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx`, zadáním uživatelského jména `anonymous` a heslo necháte prázdné.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou vyvolat výjimku:  
  
- Cestu k místnímu souboru není platný (<xref:System.ArgumentException>).  
  
- Ověření se nezdařilo (<xref:System.Security.SecurityException>).  
  
- Vypršel časový limit připojení (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Postupy: Stažení souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
