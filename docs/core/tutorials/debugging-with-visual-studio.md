---
title: Ladění aplikace konzoly .NET Core pomocí sady Visual Studio
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí sady Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 743603cb037406948190c7090ca3527bfc40db18
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702064"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>Kurz: ladění konzolové aplikace .NET Core pomocí sady Visual Studio

V tomto kurzu se seznámíte s ladicími nástroji dostupnými v aplikaci Visual Studio.

## <a name="prerequisites"></a>Požadavky

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v sadě Visual Studio 2019](with-visual-studio.md).

## <a name="use-debug-build-configuration"></a>Použít konfiguraci sestavení pro ladění

*Ladění* a *vydání* jsou integrované konfigurace sestavení sady Visual Studio. Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.

V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější. Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.

 Ve výchozím nastavení Visual Studio Code používá konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.

1. Spusťte Visual Studio.

1. Otevřete projekt, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core v aplikaci Visual Studio 2019](with-visual-studio.md).

   Aktuální konfigurace sestavení se zobrazí na panelu nástrojů. Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro zkompilování ladicí verze aplikace:

   ![Panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a>Nastavení zarážky

*Zarážka* dočasně přerušuje provádění aplikace před provedením řádku se zarážkou.

1. Nastavte *zarážku* na řádku, který zobrazuje název, datum a čas kliknutím na levý okraj okna Code (kód) na řádku. Levý okraj je nalevo od čísel řádků.  Další způsob, jak nastavit zarážku, je umístěním kurzoru do řádku kódu a následným výběrem možnosti **ladit**  >  **Přepnout zarážku** z řádku nabídek.

   Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červené tečky na levém okraji.

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Stisknutím klávesy <kbd>F5</kbd> spusťte program v režimu ladění. Dalším způsobem, jak spustit ladění, je kliknutím na **ladění**  >  **Spustit ladění** z nabídky.

1. V okně konzoly zadejte řetězec, když se program vyzve k zadání názvu a potom stiskněte klávesu <kbd>ENTER</kbd>.

1. Spuštění programu se zastaví, když dosáhne zarážky a před tím, než se `Console.WriteLine` Metoda spustí. V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.

   ![Snímek obrazovky se zarážkou v aplikaci Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a>Použít příkazové okno

**Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte. Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.

1. Pokud okno **okamžité** není viditelné, zobrazte ho tak, že kliknete na možnost **ladění**  >  **oken**  >  **Immediate**.

1. `name = "Gracie"`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd> .

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd> .

   V **příkazovém** okně se zobrazí hodnota proměnné řetězce a vlastnosti <xref:System.DateTime> hodnoty. Kromě toho jsou hodnoty proměnných aktualizovány v okně **místních** hodnot.

   ![Místní a bezprostřední okna v aplikaci Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Stisknutím klávesy <kbd>F5</kbd> pokračujte v provádění programu. Dalším způsobem, jak pokračovat, je vybrat v nabídce možnost **ladění**  >  **pokračovat** .

   Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém** okně.

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.

## <a name="set-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nezadá něco? Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku. V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** . Zaškrtněte políčko pro **podmínky** , pokud již není vybráno.

   ![Editor znázorňující panel nastavení zarážky – C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pro **podmíněný výraz**zadejte následující kód do pole, které obsahuje ukázkový kód, který testuje, pokud `x` je 5. Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .

   Místo podmíněného výrazu můžete zadat *počet*průchodů, který přerušuje spuštění programu před provedením příkazu určeného počtu. Další možností je určit *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, název procesu nebo název vlákna.

1. Kliknutím na **Zavřít** zavřete dialogové okno.

1. Spusťte program s laděním stisknutím klávesy <kbd>F5</kbd>.

1. Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu <kbd>ENTER</kbd> .

1. Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ), byla splněna, spuštění programu se zastaví, když dosáhne zarážky a předtím, než se `Console.WriteLine` Metoda spustí.

1. Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu. V tomto případě `Main` je právě spuštěná metoda. Všimněte si, že hodnota `name` proměnné je `""` nebo <xref:System.String.Empty?displayProperty=nameWithType> .

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém** okně a stisknutím klávesy <kbd>ENTER</kbd>. Výsledek je `true` .

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   Otazník nasměruje okamžité okno k [vyhodnocení výrazu](/visualstudio/ide/reference/immediate-window#enter-commands).

   ![Okamžité okno vracející hodnotu true po provedení příkazu – C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Stisknutím klávesy <kbd>F5</kbd> pokračujte v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

1. Vymažte zarážku kliknutím na tečku na levém okraji okna Code (kód). Dalším způsobem, jak zrušit zarážku, je vybrat možnost **ladění > přepínat zarážku** , zatímco je vybraný řádek kódu.

## <a name="step-through-a-program"></a>Krokovat program

Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění. Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu. Vzhledem k tomu, že je tento program malý, můžete projít celým programem.

1. Vyberte možnost **ladit**  >  **Krok do**. Dalším způsobem, jak najednou ladit jeden příkaz, je stisknutí klávesy <kbd>F11</kbd>.

   Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   C#

   ![Krok v aplikaci Visual Studio do metody-C #](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Metoda Visual Studio Step Into – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   V tomto okamžiku okno **místních** hodnot ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty. Kromě toho Visual Studio otevřelo prázdné okno konzoly.

1. Stiskněte klávesu <kbd>F11</kbd>. Visual Studio teď zvýrazní další řádek provádění. Okno **místní** hodnoty se nezměnilo a okno konzoly zůstane prázdné.

   C#

   ![Krok sady Visual Studio ve zdroji metody – C #](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Krok do zdroje metody v aplikaci Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Stiskněte klávesu <kbd>F11</kbd>. Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné. Okno **místní** hodnoty ukazuje, `name` `null` a okno konzoly zobrazuje řetězec "Co je vaše jméno?".

1. Zadáním řetězce v okně konzoly a stisknutím klávesy <kbd>ENTER</kbd>odpovězte na výzvu. Konzola nereaguje a řetězec, který jste zadali, se nezobrazuje v okně konzoly, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda bude nicméně zachytávání vstupu.

1. Stiskněte klávesu <kbd>F11</kbd>. Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné ( `currentDate` v Visual Basic). Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. V okně konzoly se zobrazí také řetězec, který jste zadali na příkazovém řádku.

1. Stiskněte klávesu <kbd>F11</kbd>. Okno **místní** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti. Okno konzoly se nezměnilo.

1. Stiskněte klávesu <kbd>F11</kbd>. Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu. V okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladit**  >  **Krok ven**. Dalším způsobem, jak zastavit krok za krokem, je stisknutí klávesy <kbd>SHIFT</kbd> + <kbd>F11</kbd>.

   V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

## <a name="use-release-build-configuration"></a>Použít konfiguraci sestavení pro vydání

Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání. Verze Release zahrnuje optimalizace kompilátoru, které mohou být někdy negativně ovlivněny chování aplikace. Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.

Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Když stisknete klávesu <kbd>F5</kbd> nebo zvolíte **Sestavit řešení** z nabídky **sestavit** , Visual Studio zkompiluje verzi aplikace. Můžete ho otestovat stejně, jako jste použili ladicí verzi.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste použili ladicí nástroje sady Visual Studio. V dalším kurzu publikujete nasazovatelné verze aplikace.

> [!div class="nextstepaction"]
> [Publikování konzolové aplikace .NET Core pomocí sady Visual Studio](publishing-with-visual-studio.md)
