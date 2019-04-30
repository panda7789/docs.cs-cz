---
title: "Nelze zapisovat do výstupního souboru '<filename>': <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: f29eb628c079f65a520cf5e1ccd8afed549f7cad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787410"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>Nelze zapisovat do výstupního souboru '\<název souboru >': \<chyby >
Došlo k potížím, vytváření souboru.  
  
 Výstupní soubor nelze otevřít pro zápis. Soubor (nebo na složku obsahující soubor) můžou být otevřené pro výhradní použití jiným procesem nebo je možné, že jeho nastaven atribut jen pro čtení.  
  
 Běžné situace, kde je soubor otevřený výhradně jsou:  
  
- Aplikace je již spuštěn a pomocí jeho soubory. Chcete-li tento problém vyřešit, ujistěte se, že aplikace není spuštěna.  
  
- Jiná aplikace má soubor otevřen. Chcete-li tento problém vyřešit, ujistěte se, že žádná jiná aplikace je přístup k souborům. Není vždy zřejmé aplikaci, pro kterou je přístupu k souborům; restartování počítače v takovém případě může být nejjednodušší způsob, jak aplikaci ukončit.  
  
 Pokud ani jeden z výstupních souborů projektu je označena jako jen pro čtení, tato výjimka bude vyvolána.  
  
 **ID chyby:** BC31019  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Kompilovat program znovu, abyste viděli, pokud se chyba objeví znovu.  
  
2. Pokud chyba přetrvává, uložte si práci a restartujte aplikaci Visual Studio.  
  
3. Pokud chyba přetrvává, restartujte počítač.  
  
4. Pokud se chyba objeví znovu, přeinstalujte Visual Basic.  
  
5. Pokud chyba přetrvává po přeinstalaci, upozorní Microsoft Product Support Services.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Ke kontrole atributů souboru v Průzkumníku souborů  
  
1. Otevřete složku, které vás zajímají.  
  
2. Klikněte na tlačítko **zobrazení** ikonu a zvolte **podrobnosti**.  
  
3. Klikněte pravým tlačítkem na záhlaví sloupce a vybrat **atributy** z rozevíracího seznamu.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Chcete-li změnit atributy souboru nebo složky  
  
1. V **Průzkumníka souborů**, klikněte pravým tlačítkem na soubor nebo složku a zvolte **vlastnosti**.  
  
2. V **atributy** část **Obecné** kartu, zrušte **jen pro čtení** pole.  
  
3. Stisknutím klávesy **OK**.  
  
## <a name="see-also"></a>Viz také:

- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
