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
ms.openlocfilehash: a5b379da00656f65476e4d9504457bf8b464beac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411652"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Postupy: Stažení souboru v jazyce Visual Basic

<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>Metoda může být použita ke stažení vzdáleného souboru a jeho uložení do konkrétního umístění. Pokud `ShowUI` je parametr nastaven na hodnotu `True` , zobrazí se dialogové okno s informacemi o průběhu stahování a umožňující uživatelům zrušit operaci. Ve výchozím nastavení nejsou přepsány existující soubory se stejným názvem. Pokud chcete přepsat existující soubory, nastavte `overwrite` parametr na `True` .

Následující podmínky mohou způsobit výjimku:

- Název jednotky není platný ( <xref:System.ArgumentException> ).

- Nezbytné ověření nebylo zadáno ( <xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException> ).

- Server nereaguje v rámci zadaného `connectionTimeout` ( <xref:System.TimeoutException> ).

- Požadavek byl zamítnut webovým serverem ( <xref:System.Net.WebException> ).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor. Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

### <a name="to-download-a-file"></a>Stažení souboru

- Použijte `DownloadFile` metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit. Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do `C:\Documents and Settings\All Users\Documents` :

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Stažení souboru s určením intervalu časového limitu

- Použijte `DownloadFile` metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI, určení umístění, do kterého se má soubor uložit, a určení intervalu časového limitu v milisekundách (výchozí hodnota je 1000). Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do a `C:\Documents and Settings\All Users\Documents` určí časový limit 500 milisekund:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Stažení souboru a zadání uživatelského jména a hesla

- Použijte `DownLoadFile` metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit, uživatelské jméno a heslo. Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží jej do `C:\Documents and Settings\All Users\Documents` , s uživatelským jménem `anonymous` a prázdným heslem.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > Protokol FTP používaný `DownLoadFile` metodou odesílá informace, včetně hesel, do prostého textu a neměl by se používat k přenosu citlivých informací.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Postupy: Nahrání souboru](how-to-upload-a-file.md)
- [Postupy: Analýza cest k souborům](../drives-directories-files/how-to-parse-file-paths.md)
