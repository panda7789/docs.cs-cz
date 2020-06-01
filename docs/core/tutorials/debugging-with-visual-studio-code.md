---
title: Ladění konzolové aplikace .NET Core pomocí Visual Studio Code
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: 82b2798397d702aa2a50c04bf6e4d569b97e3666
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241510"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a>Kurz: ladění konzolové aplikace .NET Core pomocí Visual Studio Code

Tento kurz zavádí ladicí nástroje, které jsou k dispozici v Visual Studio Code pro práci s aplikacemi .NET Core.

## <a name="prerequisites"></a>Požadavky

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio Code](with-visual-studio-code.md).

## <a name="use-debug-build-configuration"></a>Použít konfiguraci sestavení pro ladění

*Ladění* a *vydání* jsou dvě konfigurace sestavení .NET Core. Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.

V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější. Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.

 Ve výchozím nastavení Visual Studio Code používá konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.

## <a name="set-a-breakpoint"></a>Nastavení zarážky

Zarážka dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou.

1. Otevřete Visual Studio Code.

1. Otevřete složku projektu *HelloWorld* , kterou jste vytvořili v [části Vytvoření konzolové aplikace .net Core v Visual Studio Code](with-visual-studio-code.md).

1. Otevřete soubor *program.cs* .

1. Nastavte *zarážku* na řádku, který zobrazuje název, datum a čas kliknutím na levý okraj okna Code (kód). Levý okraj je nalevo od čísel řádků. Dalším způsobem, jak nastavit zarážku, je umístit kurzor do řádku kódu a stisknout <kbd>F9</kbd>.

   Jak ukazuje následující obrázek, Visual Studio Code označuje řádek, na kterém je zarážka nastavena, zobrazením červené tečky na levém okraji.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Sada zarážek":::

## <a name="set-up-for-terminal-input"></a>Nastavení pro terminálový vstup

Zarážka je umístěna po `Console.ReadLine` volání metody. **Konzola ladění** nepřijímá vstup terminálu pro spuštěný program. Pro zpracování vstupu terminálu během ladění můžete použít integrovaný terminál (jeden z Visual Studio Code Windows) nebo externí terminál. V tomto kurzu použijete integrovaný terminál.

1. Otevřete *. VSCode/Launch. JSON*.

1. Změňte `console` nastavení na `integratedTerminal` .

   Z:

   ```
   "console": "internalConsole",
   ```

   Do:

   ```
   "console": "integratedTerminal",
   ```

1. Uložte provedené změny.

## <a name="start-debugging"></a>Spustit ladění

1. Otevřete zobrazení ladění výběrem ikony ladění v nabídce na levé straně.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Otevřete kartu ladění v Visual Studio Code":::

1. Spustit ladění tak, že vyberete zelenou šipku v horní části podokna, vedle možnosti **spuštění .NET Core (konzola)**.  Dalším způsobem, jak spustit ladění, je stisknout klávesu <kbd>F5</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Spustit ladění":::

1. Vyberte kartu **terminál** , pokud chcete zobrazit "Co je vaše jméno?". před čekáním na odpověď se zobrazí výzva k zadání programu.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Výběr karty terminálu":::

1. V okně **terminálu** zadejte řetězec jako odpověď na výzvu pro název a stiskněte klávesu <kbd>ENTER</kbd>.

   Spuštění programu se zastaví, když dosáhne zarážky a před tím, než se `Console.WriteLine` Metoda spustí. Oddíl **místních** hodnot v okně **proměnné** zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Pozice zarážky, zobrazení lokálních hodnot":::

## <a name="change-variable-values"></a>Změnit hodnoty proměnných

Okno **konzoly ladění** vám umožní pracovat s aplikací, kterou ladíte. Můžete změnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.

1. Vyberte kartu **Konzola ladění** .

1. Zadejte `name = "Gracie"` na příkazovém řádku v dolní části okna **konzoly ladění** a stiskněte klávesu <kbd>ENTER</kbd> .

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Změnit hodnoty proměnných":::

1. Zadejte `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` v dolní části okna **konzoly ladění** a stiskněte klávesu <kbd>ENTER</kbd> .

   V okně **proměnné** se zobrazí nové hodnoty `name` `date` proměnných a.

1. Pokračujte v provádění programu tak, že na panelu nástrojů vyberete tlačítko **pokračovat** . Dalším způsobem, jak pokračovat, je stisknout klávesu <kbd>F5</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Pokračovat v ladění":::

1. Znovu vyberte kartu **terminálu** .

   Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **konzole ladění**.

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminál znázorňující zadané hodnoty":::

1. Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.

## <a name="set-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nezadá něco? Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.

1. Klikněte pravým tlačítkem myši (<kbd>CTRL</kbd>+ kliknutí na MacOS) na červenou tečku, která představuje zarážku. V místní nabídce vyberte **Upravit zarážku** , aby se otevřelo dialogové okno, které vám umožní zadat podmíněný výraz.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Místní nabídka zarážky":::

1. `Expression`V rozevíracím seznamu vyberte, zadejte následující podmíněný výraz a stiskněte klávesu <kbd>ENTER</kbd>.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Zadejte podmíněný výraz.":::

   Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .

   Místo podmíněného výrazu lze určit *Počet volání*, který přerušuje spuštění programu před provedením určitého příkazu, nebo *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, název procesu nebo název vlákna.

1. Spusťte program s laděním stisknutím klávesy <kbd>F5</kbd>.

1. Na kartě **terminál** po zobrazení výzvy k zadání názvu stiskněte klávesu <kbd>ENTER</kbd> .

   Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ) je splněná, spuštění programu se zastaví, když dosáhne zarážky a předtím, než se `Console.WriteLine` Metoda spustí.

   Okno **proměnné** ukazuje, že hodnota `name` proměnné je `""` nebo <xref:System.String.Empty?displayProperty=nameWithType> .

1. Zadáním následujícího příkazu na příkazovém řádku **konzoly ladění** a stisknutím klávesy <kbd>ENTER</kbd>potvrďte, že hodnota je prázdný řetězec. Výsledek je `true` .

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Ladit konzolu vracející hodnotu true po provedení příkazu":::

1. Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.

1. Vyberte kartu **terminál** a stisknutím libovolné klávesy ukončete program a zastavte ladění.

1. Vymažte zarážku kliknutím na tečku na levém okraji okna Code (kód). Dalším způsobem, jak zrušit zarážku, je stisknutí klávesy <kbd>F9</kbd> při výběru řádku kódu.

1. Pokud se zobrazí upozornění, že bude ztracena Podmínka zarážky, vyberte možnost **odebrat zarážku**.

## <a name="step-through-a-program"></a>Krokovat program

Visual Studio Code také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění. Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu. Vzhledem k tomu, že je tento program malý, můžete projít celým programem.

1. Nastavte zarážku na levou složenou závorku `Main` metody.

1. Stisknutím klávesy <kbd>F5</kbd> spusťte ladění.

   Visual Studio Code zvýrazní řádek zarážky.

   V tomto okamžiku okno **proměnné** ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty.

1. Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Tlačítko Krokovat s vnořením":::

   Visual Studio Code zvýrazní další řádek.

1. Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.

   Visual Studio Code spustí `Console.WriteLine` pro příkazový řádek název a zvýrazní další řádek provádění. Další řádek je `Console.ReadLine` pro `name` . Okno **proměnné** se nezměnilo a karta **terminálu** zobrazuje "Co je vaše jméno?" výzv.

1. Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.

   Visual Studio zvýrazní `name` přiřazení proměnné. V okně **proměnné** se zobrazí, že `name` je stále `null` .

1. Na výzvu odpovězte zadáním řetězce na kartě terminálu a stisknutím klávesy <kbd>ENTER</kbd>.

   Karta **terminálu** nezobrazuje řetězec, který zadáte při zadávání, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda zachytí vstup.

1. Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.

   Visual Studio Code zvýrazní `date` přiřazení proměnné. Okno **proměnné** zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. Na kartě **terminál** se zobrazí řetězec, který jste zadali na příkazovém řádku.

1. Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.

   Okno **proměnné** zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti.

1. Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.

   Visual Studio Code volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu. V okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **Krok ven** nebo stiskněte klávesu <kbd>SHIFT</kbd> + <kbd>F11</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Tlačítko pro krokování":::

1. Vyberte kartu **terminál** .

   Terminál zobrazí "při ukončení stiskněte libovolnou klávesu..."

1. Ukončete program stisknutím libovolné klávesy.

## <a name="select-release-build-configuration"></a>Vybrat konfiguraci sestavení pro vydání

Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání. Verze Release zahrnuje optimalizace kompilátoru, které mohou ovlivnit chování aplikace. Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.

Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, otevřete **terminál** a spusťte následující příkaz:

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a>Další zdroje

* [Ladění v Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste použili Visual Studio Code ladicí nástroje. V dalším kurzu publikujete nasazovatelné verze aplikace.

> [!div class="nextstepaction"]
> [Publikování konzolové aplikace .NET Core pomocí Visual Studio Code](publishing-with-visual-studio-code.md)
