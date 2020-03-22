---
title: 'Postupy: Stažení souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4923feb46ff638de9514a4d70fc00367491a6f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345625"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Postupy: Stažení souboru v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> lze použít ke stažení vzdáleného souboru a jeho uložení do určitého umístění. Pokud `ShowUI` je parametr `True`nastaven na , zobrazí se dialogové okno, které ukazuje průběh stahování a umožňuje uživatelům operaci zrušit. Ve výchozím nastavení nejsou existující soubory se stejným názvem přepsány. Pokud chcete přepsat existující soubory, `overwrite` nastavte `True`parametr na .

Následující podmínky mohou způsobit výjimku:

- Název jednotky není<xref:System.ArgumentException>platný ( ).

- Nebylo zadáno nezbytné<xref:System.UnauthorizedAccessException> ověření <xref:System.Security.SecurityException>( nebo ).

- Server nereaguje v rámci `connectionTimeout` <xref:System.TimeoutException>zadaného ( ).

- Požadavek je webem zamítnut<xref:System.Net.WebException>( ).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic. Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

### <a name="to-download-a-file"></a>Stažení souboru

- Pomocí `DownloadFile` této metody stáhněte soubor, zadejte umístění cílového souboru jako řetězec nebo identifikátor URI a umístění, ve kterém má být soubor ukládán. Tento příklad stáhne `WineList.txt` `http://www.cohowinery.com/downloads` soubor z a `C:\Documents and Settings\All Users\Documents`uloží jej do :

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Stažení souboru určením časového intervalu

- Pomocí `DownloadFile` metody stáhněte soubor, určení umístění cílového souboru jako řetězec nebo IDENTIFIKÁTOR URI, určení umístění, ve kterém chcete soubor uložit, a určení časového limitu v milisekundách (výchozí hodnota je 1000). Tento příklad stáhne `WineList.txt` `http://www.cohowinery.com/downloads` soubor z a `C:\Documents and Settings\All Users\Documents`uloží jej do aplikace , a zadává interval časového intervalu 500 milisekund:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Stažení souboru zadáním uživatelského jména a hesla

- Pomocí `DownLoadFile` této metody stáhněte soubor, zadejte umístění cílového souboru jako řetězec nebo identifikátor URI a umístění, do kterého chcete soubor uložit, uživatelské jméno a heslo. Tento příklad stáhne `WineList.txt` `http://www.cohowinery.com/downloads` soubor z a `C:\Documents and Settings\All Users\Documents`uloží jej `anonymous` do aplikace s uživatelským jménem a prázdným heslem.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > Protokol FTP používaný `DownLoadFile` metodou odesílá informace, včetně hesel, ve formátu prostého textu a neměl by být používán pro přenos citlivých informací.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Postupy: Nahrání souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
