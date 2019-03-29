---
title: Zakázání sledování DPI v sadě Visual Studio
description: Tento článek popisuje omezení pro návrháře formulářů Windows na monitorech HDPI a jak spustit aplikaci Visual Studio jako nepodporující DPI proces.
ms.date: 03/19/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 73f2371c40facf8902958cce020a6f02047615ba
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633865"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Zakázání sledování DPI v sadě Visual Studio

Visual Studio je bodů na palec (DPI) vědět aplikaci, což znamená, že zobrazení škáluje automaticky. Pokud aplikace uvádí, že není s ohledem na DPI, škáluje operační systém aplikace jako rastrový obrázek. Toto chování se také nazývá virtualizace DPI. Aplikace stále domnívá, že se spouští ve 100 % škálování nebo 96 dpi.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Návrhář formulářů Windows na monitorech HDPI

**Návrháře formulářů Windows** v sadě Visual Studio nemá škálování podpory. To způsobí, že problémy zobrazení při otevření některé formulářů v **Návrháře formulářů Windows** na vysokým počtem bodů na palec (HDPI) monitorování. Příklady můžete ovládací prvky se zobrazí překrytí, jak je znázorněno na následujícím obrázku:

![Návrhář formulářů Windows na monitoru HDPI](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

Když otevřete formulář v nástrojích pro **Návrháře formulářů Windows** v sadě Visual Studio na monitoru HDPI, aplikace Visual Studio zobrazí žlutý informační pruh v horní části návrháře:

![Informační panel v sadě Visual Studio k restartování v DPI nepodporující režim](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

Přečte zprávu **škálování na hlavní obrazovce je nastavena na 200 % (192 dpi). To může způsobit problémů s vykreslováním v okně návrháře.**

> [!NOTE]
> Tento informační panel byla zavedena v sadě Visual Studio 2017 verze 15.8.

Pokud nefungují v návrháři a není potřeba upravit rozložení formuláře, můžete ignorovat informační panel a pokračovat v práci v editoru kódu nebo v jiných typech návrhářů. (Můžete také [zakázat oznámení](#disable-notifications) tak, aby informační panel nebude nadále zobrazovat.) Pouze **Návrháře formulářů Windows** má vliv. Pokud potřebujete pracovat **Návrháře formulářů Windows**, následující část vám pomůže [problém pomohl vyřešit](#to-resolve-the-problem).

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

**Položka**: V závislosti na tom, jestli používáte Visual Studio 2017 nebo 2019 použijte jednu z těchto hodnot:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Pokud používáte edici Professional nebo Enterprise sady Visual Studio, nahraďte **komunity** s **Professional** nebo **Enterprise** v položce. Také nahraďte podle potřeby písmeno jednotky.

**Typ**: REG_SZ

**Hodnota**: DPIUNAWARE

> [!NOTE]
> Visual Studio zůstane v DPI nepodporující režim, dokud odebrání položky registru.

### <a name="set-your-display-scaling-setting-to-100"></a>Nastavte zobrazení škálování nastavení na 100 %

Pokud chcete nastavit zobrazení nastavení na 100 % změna měřítka ve Windows 10, zadejte **nastavení zobrazení** na hlavním panelu vyhledávacího pole a pak vyberte **změně nastavení zobrazení**. V **nastavení** okno, nastavte **změnit velikost textu, aplikací a dalších položek** k **100 %**.

Nastavení displeje škálování na 100 % může nežádoucí, protože uživatelské rozhraní může být příliš malá, aby byla použitelná.

## <a name="disable-notifications"></a>Zakázat oznámení

Můžete se informováni o DPI škálování problémy v sadě Visual Studio. Můžete chtít zakázat oznámení, pokud nepracujete v návrháři, např.

Chcete-li zakázat oznámení, zvolte **nástroje** > **možnosti** otevřít **možnosti** dialogového okna. Potom kliknutím na možnost **Návrháře formulářů Windows** > **Obecné**a nastavte **DPI škálování oznámení** k **False**.

![DPI škálování možnost oznámení v sadě Visual Studio](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

Pokud chcete později znovu povolit škálování oznámení, nastavte vlastnost na **True**.

## <a name="troubleshoot"></a>Řešení potíží

Pokud přechod sledování DPI nefunguje podle očekávání v sadě Visual Studio, zkontrolujte, zda máte `dpiAwareness` hodnotu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File provádění Options\devenv.exe**  podklíče v editoru registru. Odstraňte hodnotu, pokud je k dispozici.

## <a name="see-also"></a>Viz také:

- [Automatická změna měřítka ve Windows Forms](automatic-scaling-in-windows-forms.md)
