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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345563"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Postupy: Odeslání souboru v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> lze použít k nahrání souboru a jeho uložení do vzdáleného umístění. Pokud je parametr `ShowUI` nastaven na `True`, zobrazí se dialogové okno s informacemi o průběhu nahrávání a umožňuje uživatelům zrušit operaci.  
  
### <a name="to-upload-a-file"></a>Nahrání souboru  
  
- Použijte metodu `UploadFile` k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI (Uniform Resource Identifier). Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Nahrání souboru a zobrazení průběhu operace  
  
- Použijte metodu `UploadFile` k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI. Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez zadání uživatelského jména nebo hesla, zobrazí průběh nahrávání a má časový limit 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Pokud chcete nahrát soubor, zadejte uživatelské jméno a heslo.  
  
- Použijte metodu `UploadFile` k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI a zadání uživatelského jména a hesla. Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx`a poskytne uživatelské jméno `anonymous` a prázdné heslo.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou vyvolat výjimku:  
  
- Cesta k místnímu souboru není platná (<xref:System.ArgumentException>).  
  
- Ověřování se nezdařilo (<xref:System.Security.SecurityException>).  
  
- Vypršel časový limit připojení (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Postupy: Stažení souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
