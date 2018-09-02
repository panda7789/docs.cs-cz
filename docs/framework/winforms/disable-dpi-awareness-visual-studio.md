---
title: Zakázání sledování DPI v sadě Visual Studio
description: Tento článek popisuje omezení pro návrháře formulářů Windows na monitorech HDPI a jak spustit aplikaci Visual Studio jako nepodporující DPI proces.
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65c997e12aa033b3b08d32c8ab76372e3c52a803
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467104"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Zakázání sledování DPI v sadě Visual Studio

Visual Studio je bodů na palec (DPI) vědět aplikaci, což znamená, že zobrazení škáluje automaticky. Pokud aplikace uvádí, že není s ohledem na DPI, škáluje operační systém aplikace jako rastrový obrázek. Toto chování se také nazývá virtualizace DPI. Aplikace stále domnívá, že se spouští ve 100 % škálování nebo 96 dpi.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Návrhář formulářů Windows na monitorech HDPI

**Návrháře formulářů Windows** v sadě Visual Studio nemá škálování podpory. To způsobí, že problémy zobrazení při otevření některé formulářů v **Návrháře formulářů Windows** na vysokým počtem bodů na palec (HDPI) monitorování. Příklady můžete ovládací prvky se zobrazí překrytí, jak je znázorněno na následujícím obrázku:

![Návrhář formulářů Windows na monitoru HDPI](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

V sadě Visual Studio 2017 verze 15,8 a novější, když otevřete formulář v nástrojích pro **Návrháře formulářů Windows** na monitoru HDPI sady Visual Studio zobrazí žlutý informační pruh v horní části návrháře:

![Informační panel v sadě Visual Studio k restartování v DPI nepodporující režim](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

Přečte zprávu **škálování na hlavní obrazovce je nastavena na 200 % (192 dpi). To může způsobit problémů s vykreslováním v okně návrháře.**

Pokud nefungují v návrháři a není potřeba upravit rozložení formuláře, můžete ignorovat informační panel a pokračovat v práci v editoru kódu nebo v jiných typech návrhářů. Pouze **Návrháře formulářů Windows** má vliv. Pokud potřebujete pracovat **Návrháře formulářů Windows**, následující část vám pomůže [problém pomohl vyřešit](#to-resolve-the-problem).

## <a name="to-resolve-the-problem"></a>Chcete-li vyřešit tento problém

Existují tři možnosti, jak vyřešit problém zobrazení.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Restartujte sadu Visual Studio jako nepodporující DPI proces

Visual Studio můžete restartovat jako nepodporující DPI procesu tak, že vyberete možnost v žlutý informační panel. Toto je upřednostňovaný způsob řešení problému.

Když Visual Studio spustí jako proces nepodporující DPI, vyřešení problémů rozložení návrháře, ale může zobrazit fuzzy písma. Visual Studio zobrazí různé žlutý informační zprávy při spuštění jako nepodporující DPI proces, který říká **sady Visual Studio je spuštěn jako proces nepodporující DPI. Návrháře WPF a XAML se nemusí zobrazit správně.** Informační panel také nabízí možnost **restartujte Visual Studio jako rozlišením DPI proces**.

> [!NOTE]
> - Pokud měl neukotveno okna nástrojů v sadě Visual Studio, pokud jste vybrali možnost restartuje jako proces nepodporující DPI, může změnit umístění těchto oken nástrojů.
> - Pokud používáte výchozí profil jazyka Visual Basic, nebo pokud máte **uložit nové projekty při vytvoření** volba vybraná v **nástroje** > **možnosti**  >  **Projekty a řešení**, Visual Studio nelze znovu otevřít váš projekt, když ho restartuje jako proces nepodporující DPI. Však můžete otevřít projekt tak, že vyberete ho pod **souboru** > **poslední projekty a řešení**.

Je důležité restartovat Visual Studio jako rozlišením DPI proces, až budete hotovi, práci **Návrháře formulářů Windows**. Když je spuštěn jako proces nepodporující DPI, můžete se podívat fuzzy písma a může se zobrazit problémy v jiné návrháře, jako **návrháře XAML**. Pokud ho zavřete a znovu otevřete Visual Studio, když je spuštěn v režimu nepodporující DPI, stane se rozlišením DPI znovu. Můžete také kliknout **restartujte Visual Studio jako rozlišením DPI proces** možnost v informační panel.

### <a name="add-a-registry-entry"></a>Přidat položku registru

Visual Studio můžete označit jako nepodporující DPI úpravou registru. Otevřít **Editor registru** a přidání položky do **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** podklíč:

**Položka**: % ProgramFiles (x86) %\Microsoft Visual Studio\2017\your-edition\Common7\IDE\devenv.exe

**Typ**: REG_SZ

**Hodnota**: DPIUNAWARE

> [!NOTE]
> Visual Studio zůstane v DPI nepodporující režim, dokud odebrání položky registru.

### <a name="set-your-display-scaling-setting-to-100"></a>Nastavte zobrazení škálování nastavení na 100 %

Pokud chcete nastavit zobrazení nastavení na 100 % změna měřítka ve Windows 10, zadejte **nastavení zobrazení** na hlavním panelu vyhledávacího pole a pak vyberte **změně nastavení zobrazení**. V **nastavení** okno, nastavte **změnit velikost textu, aplikací a dalších položek** k **100 %**.

Nastavení displeje škálování na 100 % může nežádoucí, protože uživatelské rozhraní může být příliš malá, aby byla použitelná.

## <a name="see-also"></a>Viz také:

- [Automatická změna měřítka ve Windows Forms](automatic-scaling-in-windows-forms.md)