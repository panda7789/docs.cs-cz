---
title: "Postupy: Stažení souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc67d28b870f86c6464e86f7682f71e6e36ea9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Postupy: Stažení souboru v jazyce Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metoda slouží k stažení vzdáleného souboru a uložte ho do určitého umístění. Pokud `ShowUI` parametr je nastaven na `True`, zobrazí se dialogové okno zobrazující průběh stahování a umožníte uživatelům na tlačítko Storno. Ve výchozím nastavení nepřepisují existující soubory se stejným názvem; Pokud chcete přepsat existující soubory, nastavte `overwrite` parametru `True`.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název jednotky je neplatný (<xref:System.ArgumentException>).  
  
-   Nebyl zadán nezbytné ověřování (<xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException>).  
  
-   Server neodpověděl v rámci zadaného `connectionTimeout` (<xref:System.TimeoutException>).  
  
-   Požadavek se odmítne webovým serverem (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic. Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
### <a name="to-download-a-file"></a>Ke stažení souboru  
  
-   Použití `DownloadFile` metoda stažení souboru, zadáním umístění cílového souboru jako řetězec nebo identifikátor URI a určením umístění, kam chcete soubor uložit. Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Ke stažení souboru, zadání interval časového limitu  
  
-   Použití `DownloadFile` metoda stažení souboru, zadáním umístění cílového souboru jako řetězec nebo identifikátor URI, zadáte umístění, kam chcete uložit soubor a určením časového limitu v milisekundách (výchozí hodnota je 1000). Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`, zadání interval časového limitu na 500 milisekund:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Ke stažení souboru, poskytnutí uživatelského jména a hesla  
  
-   Použití `DownLoadFile` metoda stažení souboru, zadáním umístění cílového souboru jako řetězec nebo identifikátor URI a zadáte umístění, kam chcete uložit soubor, uživatelské jméno a heslo. Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`, s uživatelským jménem `anonymous` a prázdné heslo.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  Protokol FTP používá `DownLoadFile` metoda odesílá informace, včetně hesel ve formátu prostého textu a neměl by se používat k přenosu citlivých informací.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [Postupy: odeslání souboru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
