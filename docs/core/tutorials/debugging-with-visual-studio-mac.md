---
title: Ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí sady Visual Studio Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 011647a6e3e676909880befa3b770205eb9616d6
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957522"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a>Kurz: ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac

V tomto kurzu se seznámíte s ladicími nástroji dostupnými v Visual Studio pro Mac.

## <a name="prerequisites"></a>Předpoklady

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac](with-visual-studio-mac.md).

## <a name="use-debug-build-configuration"></a>Použít konfiguraci sestavení pro ladění

*Ladění* a *vydání* jsou integrované konfigurace sestavení sady Visual Studio. Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.

V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější. Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.

Ve výchozím nastavení Visual Studio pro Mac používá konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.

1. Spusťte Visual Studio pro Mac.

1. Otevřete projekt, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac](with-visual-studio-mac.md).

   Aktuální konfigurace sestavení se zobrazí na panelu nástrojů. Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro zkompilování ladicí verze aplikace:

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Panel nástrojů sady Visual Studio se zvýrazněným laděním":::

## <a name="set-a-breakpoint"></a>Nastavení zarážky

*Zarážka* dočasně přerušuje provádění aplikace před provedením řádku se zarážkou.

1. Nastavte zarážku na řádku, který zobrazuje název, datum a čas. Chcete-li to provést, umístěte kurzor na řádek kódu a stiskněte <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>příkaz</kbd> + <kbd>\\</kbd> ). Další způsob, jak nastavit zarážku, je vybrat možnost **Spustit**  >  **přepínací zarážku** z nabídky.

   Sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červené tečky na levém okraji.

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Okno programu Visual Studio se sadou zarážek":::

1. Stisknutím <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>) spusťte program v režimu ladění. Další způsob, jak spustit ladění, je kliknutím na příkaz **Spustit**  >  **ladění** z nabídky.

1. V okně terminálu zadejte řetězec, když se program vyzve k zadání názvu a potom stiskněte klávesu <kbd>ENTER</kbd>.

1. Spuštění programu se zastaví, když dosáhne zarážky, než se `Console.WriteLine` spustí metoda.

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Snímek obrazovky se zarážkou v aplikaci Visual Studio":::

## <a name="use-the-immediate-window"></a>Použít příkazové okno

**Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte. Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.

1. Pokud není okno **okamžité** , zobrazte ho tak, že kliknete na **Zobrazit**  >  **ladicí panely**  >  **okamžitě**.

1. `name = "Gracie"`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd>.

1. `date = date.AddDays(1)`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd>.

   V **příkazovém** okně se zobrazí nová hodnota řetězcové proměnné a vlastnosti <xref:System.DateTime> hodnoty.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Okamžité okno v aplikaci Visual Studio":::

   V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě. Hodnoty proměnných, které jste právě změnili, jsou aktualizovány v okně **místních** hodnot.

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Okno místních hodnot v aplikaci Visual Studio":::

1. Pokud chcete pokračovat v ladění, stiskněte <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).

   Hodnoty zobrazené v terminálu odpovídají změnám, které jste provedli v **příkazovém** okně.

   Pokud terminál nevidíte, vyberte v dolním navigačním panelu položku **Terminal-HelloWorld** .

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Hello World terminálu v dolním navigačním panelu":::

1. Ukončete program stisknutím libovolné klávesy.

1. Zavřete okno terminálu.

## <a name="set-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nezadá něco? Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.

1. <kbd>stiskněte klávesu CTRL</kbd>a klikněte na červenou tečku, která představuje zarážku. V místní nabídce vyberte **Upravit zarážku**.

1. V dialogovém okně **Upravit zarážku** zadejte do následujícího pole následující kód **a následující podmínka je pravdivá**a vyberte **použít**.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Editor znázorňující panel nastavení zarážky":::

   Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .

   Místo podmíněného výrazu můžete zadat *počet*průchodů, který přerušuje spuštění programu před provedením příkazu určeného počtu.

1. Spusťte ladění stisknutím <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).

1. V okně terminálu po zobrazení výzvy k zadání jména stiskněte klávesu <kbd>ENTER</kbd> .

   Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ), byla splněna, spuštění programu se zastaví při dosažení zarážky.

1. Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu. V tomto případě `Main` je právě spuštěná metoda. Všimněte si, že hodnota `name` proměnné je `""` , to znamená <xref:System.String.Empty?displayProperty=nameWithType> .

1. Můžete také zjistit, že hodnota je prázdný řetězec zadáním `name` názvu proměnné v **příkazovém podokně** a stisknutím klávesy <kbd>ENTER</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="Příkazové okno se zobrazeným názvem je prázdným řetězcem.":::

1. Pokud chcete pokračovat v ladění, stiskněte <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).

1. V okně terminálu ukončete program stisknutím libovolné klávesy.

1. Zavřete okno terminálu.

1. Vymažte zarážku kliknutím na červenou tečku na levém okraji okna Code (kód). Dalším způsobem, jak zrušit zarážku, je výběrem možnosti **spustit > Přepnout zarážku** , když je vybraný řádek kódu.

## <a name="step-through-a-program"></a>Krokovat program

Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění. Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu. Vzhledem k tomu, že je tento program malý, můžete projít celým programem.

1. Nastavte zarážku na složenou závorku, která označuje začátek `Main` metody (stiskněte <kbd>příkaz</kbd> + <kbd>\\</kbd> ).

1. Spusťte ladění stisknutím <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).

   Visual Studio se zastaví na řádku se zarážkou.

1. Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>) nebo vyberte **Spustit**  >  **Krok do** pro posunutí jednoho řádku.

   Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Metoda kroku v aplikaci Visual Studio":::

   V tomto okamžiku okno **místních** hodnot ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty. Kromě toho Visual Studio otevřelo prázdného terminálu.

1. Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).

   Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné. V okně **místní** hodnoty se zobrazí `name` to `null` a terminál zobrazí řetězec "Co je vaše jméno?".

1. Zadáním řetězce v okně konzoly a stisknutím klávesy <kbd>ENTER</kbd>odpovězte na výzvu.

1. Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).

   Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné. Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. Terminál zobrazí řetězec, který jste zadali na příkazovém řádku.

1. Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).

   Okno **místní** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti. Terminál je beze změny.

1. Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).

   Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu. Terminál zobrazí formátovaný řetězec.

1. Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>u</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>u</kbd>) nebo vyberte **Spustit**  >  **Krok ven**.

   Terminál zobrazí zprávu a počká, až stisknete klávesu.

1. Ukončete program stisknutím libovolné klávesy.

## <a name="use-release-build-configuration"></a>Použít konfiguraci sestavení pro vydání

Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání. Verze Release zahrnuje optimalizace kompilátoru, které mohou negativně ovlivnit chování aplikace. Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.

Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, proveďte následující kroky:

1. Změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním":::

1. Stiskněte <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>ENTER</kbd>) a spusťte bez ladění.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste použili ladicí nástroje sady Visual Studio. V dalším kurzu publikujete nasazovatelné verze aplikace.

> [!div class="nextstepaction"]
> [Publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac](publishing-with-visual-studio-mac.md)
