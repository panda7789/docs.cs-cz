---
title: 'Postupy: Odeslání souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345563"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Postupy: Odeslání souboru v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> lze použít k nahrání souboru a jeho uložení do vzdáleného umístění. Pokud `ShowUI` je parametr `True`nastaven na , zobrazí se dialogové okno, které zobrazuje průběh nahrávání a umožňuje uživatelům operaci zrušit.  
  
### <a name="to-upload-a-file"></a>Nahrání souboru  
  
- Pomocí `UploadFile` této metody můžete nahrát soubor a zadat umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI (Identifikátor jednotného prostředku). Tento příklad odešle `Order.txt` `http://www.cohowinery.com/uploads.aspx`soubor do aplikace .  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Nahrání souboru a zobrazení průběhu operace  
  
- Pomocí `UploadFile` této metody můžete nahrát soubor a zadat umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI. Tento příklad odešle `Order.txt` `http://www.cohowinery.com/uploads.aspx` soubor bez zadání uživatelského jména nebo hesla, zobrazí průběh nahrávání a má interval časového intervalu 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Odeslání souboru zadáním uživatelského jména a hesla  
  
- Pomocí `UploadFile` této metody můžete nahrát soubor, zadat umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI a zadat uživatelské jméno a heslo. Tento příklad nahraje `Order.txt` `http://www.cohowinery.com/uploads.aspx`soubor do , `anonymous` zadání uživatelského jména a prázdné heslo.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou vyvolat výjimku:  
  
- Cesta k místnímu souboru není platná (<xref:System.ArgumentException>).  
  
- Ověřování se<xref:System.Security.SecurityException>nezdařilo ( ).  
  
- Vypršel časový limit<xref:System.TimeoutException>připojení ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Postupy: Stažení souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
