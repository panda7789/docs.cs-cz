---
title: 'Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce97bcb2dd0de774c1a82ae75ef5b83c02467edb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a>Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;
Došlo k potížím, vytvoření souboru.  
  
 Výstupní soubor nelze otevřít pro zápis. Soubor (nebo ve složce obsahující soubor) můžou být otevřené pro výhradní použití jiný proces, nebo může mít jeho nastaven atribut jen pro čtení.  
  
 Běžné situace, kdy je výhradně otevřen souboru jsou:  
  
-   Aplikace je již spuštěna a pomocí jeho soubory. Chcete-li tento problém vyřešit, ujistěte se, že aplikace není spuštěn.  
  
-   Jiná aplikace má otevřít soubor. Chcete-li tento problém vyřešit, ujistěte se, že žádná jiná aplikace, je přístup k souborům. Není vždy zřejmé aplikaci, pro kterou je přístupu k souborům; restartování počítače v takovém případě může být nejjednodušší způsob, jak aplikaci ukončit.  
  
 Pokud ani jeden z výstupních souborů projektu je označena jako jen pro čtení, bude vyvolána výjimka.  
  
 **ID chyby:** BC31019  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Kompilace programu zjistíte, pokud se chyba objeví znovu.  
  
2.  Pokud potíže potrvají, uložte si práci a restartujte Visual Studio.  
  
3.  Pokud potíže potrvají, restartujte počítač.  
  
4.  Pokud se chyba objeví znovu, přeinstalujte jazyka Visual Basic.  
  
5.  Pokud chyba přetrvává i po přeinstalování, upozorněte služby Microsoft Product Support Services.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Chcete-li zkontrolovat atributů souboru v Průzkumníkovi souborů  
  
1.  Otevřete složku, které vás zajímají.  
  
2.  Klikněte **zobrazení** ikonu a vyberte **podrobnosti**.  
  
3.  Klikněte pravým tlačítkem myši na záhlaví sloupce a vyberte **atributy** z rozevíracího seznamu.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Chcete-li změnit atributy souboru nebo složky  
  
1.  V **Průzkumníka souborů**, klikněte pravým tlačítkem na soubor nebo složku a vyberte možnost **vlastnosti**.  
  
2.  V **atributy** části **Obecné** zrušte **jen pro čtení** pole.  
  
3.  Press **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
