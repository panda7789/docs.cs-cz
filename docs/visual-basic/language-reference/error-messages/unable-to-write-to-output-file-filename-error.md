---
title: "Nelze zapisovat do výstupního souboru '<filename>': <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 087735722fcd4dd789e25aacf6eeefffb490dac5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198200"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>Do výstupního souboru\<filename > se nedá zapisovat: Chyba \<
Při vytváření souboru došlo k potížím.  
  
 Výstupní soubor nelze otevřít pro zápis. Soubor (nebo složku obsahující soubor) může být otevřen pro výhradní použití jiným procesem nebo může mít nastaven atribut jen pro čtení.  
  
 K běžným situacím, kdy se soubor otevírá výhradně, patří:  
  
- Aplikace už je spuštěná a používá její soubory. Chcete-li tento problém vyřešit, zajistěte, aby aplikace neběžela.  
  
- Soubor otevřela jiná aplikace. Chcete-li tento problém vyřešit, ujistěte se, že k souborům nepřistupuje žádná jiná aplikace. Vždy není zřejmé, ke které aplikaci přistupuje vaše soubory; v takovém případě může být restartování počítače nejjednodušší způsob, jak aplikaci ukončit.  
  
 Pokud je i jeden z výstupních souborů projektu označen jen pro čtení, bude vyvolána tato výjimka.  
  
 **ID chyby:** BC31019  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkompilujte program znovu, abyste viděli, jestli se chyba opakuje.  
  
2. Pokud chyba přetrvává, uložte svou práci a restartujte aplikaci Visual Studio.  
  
3. Pokud chyba přetrvává, restartujte počítač.  
  
4. Pokud se chyba opakuje, přeinstalujte Visual Basic.  
  
5. Pokud potíže potrvají i po přeinstalaci, upozorněte služby Microsoft Product Support Services.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Postup při kontrole atributů souborů v Průzkumníkovi souborů  
  
1. Otevřete složku, do které vás zajímáte.  
  
2. Klikněte na ikonu **zobrazení** a vyberte **Podrobnosti**.  
  
3. Klikněte pravým tlačítkem myši na záhlaví sloupce a v rozevíracím seznamu vyberte možnost **atributy** .  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Změna atributů souboru nebo složky  
  
1. V **Průzkumníku souborů**klikněte pravým tlačítkem na soubor nebo složku a vyberte **vlastnosti**.  
  
2. V části **atributy** na kartě **Obecné** zrušte zaškrtnutí políčka **jen pro čtení** .  
  
3. Stiskněte **OK**.  
  
## <a name="see-also"></a>Viz také:

- [Kontaktujte nás](/visualstudio/ide/feedback-options)
