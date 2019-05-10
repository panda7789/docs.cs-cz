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
ms.openlocfilehash: b2c313078e3438c84068b6cc54d787b567a768b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662700"
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
