---
title: 'Postupy: Nahrání souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: cee6811d6b6d295c28eb683c5d2f7bcbb5fe94ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401807"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Postupy: Odeslání souboru v jazyce Visual Basic

<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>Metodu lze použít k nahrání souboru a jeho uložení do vzdáleného umístění. Pokud `ShowUI` je parametr nastaven na hodnotu `True` , zobrazí se dialogové okno, které zobrazuje průběh nahrávání a umožňuje uživatelům zrušit operaci.  
  
### <a name="to-upload-a-file"></a>Nahrání souboru  
  
- Použijte `UploadFile` metodu pro nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátor URI (Uniform Resource Identifier). Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx` .  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Nahrání souboru a zobrazení průběhu operace  
  
- Použijte `UploadFile` metodu k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI. Tento příklad nahraje soubor do, `Order.txt` `http://www.cohowinery.com/uploads.aspx` aniž by zadal uživatelské jméno nebo heslo, zobrazuje průběh nahrávání a má časový limit 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Pokud chcete nahrát soubor, zadejte uživatelské jméno a heslo.  
  
- Použijte `UploadFile` metodu k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI a zadání uživatelského jména a hesla. Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx` , zadáním uživatelského jména `anonymous` a prázdného hesla.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou vyvolat výjimku:  
  
- Cesta k místnímu souboru není platná ( <xref:System.ArgumentException> ).  
  
- Ověřování se nezdařilo ( <xref:System.Security.SecurityException> ).  
  
- Vypršel časový limit připojení ( <xref:System.TimeoutException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Postupy: Stažení souboru](how-to-download-a-file.md)
- [Postupy: Analýza cest k souborům](../drives-directories-files/how-to-parse-file-paths.md)
