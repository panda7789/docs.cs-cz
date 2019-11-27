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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345625"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Postupy: Stažení souboru v jazyce Visual Basic

Metodu <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> lze použít ke stažení vzdáleného souboru a jeho uložení do konkrétního umístění. Pokud je parametr `ShowUI` nastaven na hodnotu `True`, zobrazí se dialogové okno s informacemi o průběhu stahování a umožňující uživatelům zrušit operaci. Ve výchozím nastavení nejsou přepsány existující soubory se stejným názvem. Pokud chcete přepsat existující soubory, nastavte parametr `overwrite` na hodnotu `True`.

Následující podmínky mohou způsobit výjimku:

- Název jednotky není platný (<xref:System.ArgumentException>).

- Nebylo zadáno nezbytné ověřování (<xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException>).

- Server nereaguje v rámci zadaného `connectionTimeout` (<xref:System.TimeoutException>).

- Tento požadavek byl zamítnut webovým serverem (<xref:System.Net.WebException>).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor. Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

### <a name="to-download-a-file"></a>Stažení souboru

- Použijte metodu `DownloadFile` ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit. Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do `C:\Documents and Settings\All Users\Documents`:

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Stažení souboru s určením intervalu časového limitu

- Použijte metodu `DownloadFile` ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI, určení umístění, do kterého se má soubor uložit, a určení intervalu časového limitu v milisekundách (výchozí hodnota je 1000). Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží jej do `C:\Documents and Settings\All Users\Documents`a určí časový limit 500 milisekund:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Stažení souboru a zadání uživatelského jména a hesla

- Použijte metodu `DownLoadFile` ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit, uživatelské jméno a heslo. Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží jej do `C:\Documents and Settings\All Users\Documents`s uživatelským jménem `anonymous` a prázdným heslem.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > Protokol FTP používaný metodou `DownLoadFile` odesílá informace, včetně hesel, do prostého textu a neměl by se používat k přenosu citlivých informací.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Postupy: Nahrání souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
