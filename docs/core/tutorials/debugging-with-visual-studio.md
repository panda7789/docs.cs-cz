---
title: Ladění aplikace Hello World .NET Core pomocí sady Visual Studio
description: Naučte se ladit aplikaci Hello World napsanou v C# nebo Visual Basic se sadou Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156670"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Ladění aplikace C# .net Core Hello World nebo Visual Basic pomocí sady Visual Studio

Zatím jste postupovali podle kroků v části [Vytvoření první konzolové aplikace .NET Core v aplikaci Visual Studio 2019](with-visual-studio.md) pro vytvoření a spuštění jednoduché konzolové aplikace. Jakmile napíšete a zkompilujete aplikaci, můžete ji začít testovat. Sada Visual Studio obsahuje komplexní sadu ladicích nástrojů, které můžete použít k řešení potíží s aplikací.

## <a name="debug-build-configuration"></a>Ladit konfiguraci sestavení

*Ladění* a *vydání* jsou dvě z výchozích konfigurací sestavení sady Visual Studio. Aktuální konfigurace sestavení se zobrazí na panelu nástrojů. Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro zkompilování ladicí verze aplikace:

![Panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Začněte spuštěním ladicí verze vaší aplikace. Konfigurace sestavení ladění vypíná většinu optimalizací kompilátoru a poskytuje bohatší informace během procesu sestavení.

## <a name="set-a-breakpoint"></a>Nastavení zarážky

Spusťte program a vyzkoušejte několik funkcí ladění:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. Nastavte *zarážku* na řádku, který čte `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` kliknutím na levý okraj okna Code (kód) na řádku. Zarážku lze také nastavit vložením blikajícího kurzoru do řádku kódu a následným stisknutím klávesy **F9** nebo výběrem možnosti **ladit** > v řádku nabídek **Přepnout zarážku** .

   Zarážka dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou.

   Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červeného kruhu v jeho levém okraji.

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Spusťte program v režimu ladění tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknete klávesu **F5**nebo zvolíte **ladění** > **Spustit ladění**.

1. V okně konzoly zadejte řetězec, když se program vyzve k zadání názvu a potom stiskněte klávesu **ENTER**.

1. Spuštění programu se zastaví, když dosáhne zarážky a před spuštěním metody `Console.WriteLine`. V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.

   ![Snímek obrazovky se zarážkou v aplikaci Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. **Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte. Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.

   1. Pokud okno **okamžité** není viditelné, zobrazte ho výběrem možnosti **ladění** > **Windows** > **Immediate**.

   1. Do příkazového podokna **zadejte** `name = "Gracie"` a stiskněte klávesu **ENTER** .

   1. Do příkazového podokna **zadejte** `date = DateTime.Parse("11/16/2019 5:25 PM")` a stiskněte klávesu **ENTER** .

   V **příkazovém** okně se zobrazí hodnota proměnné řetězce a vlastnosti <xref:System.DateTime> hodnoty. Kromě toho jsou hodnoty proměnných aktualizovány v okně **místních** hodnot.

   ![Místní a bezprostřední okna v aplikaci Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Pokračujte v provádění programu tak, že na panelu nástrojů vyberete tlačítko **pokračovat** nebo vyberete **ladění** > **pokračovat**. Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém** okně.

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Nastavte *zarážku* na řádku, který čte `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` kliknutím na levý okraj okna Code (kód) na řádku. Můžete také nastavit zarážku umístěním blikajícího kurzoru na požadovaný řádek a pak vybrat možnost **ladění** > v řádku nabídek **Přepnout zarážku** .

   Zarážka dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou.

   Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červeného kruhu v jeho levém okraji.

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Spusťte program v režimu ladění tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknete klávesu **F5**nebo zvolíte **ladění** > **Spustit ladění**.

1. Pokud se program vyzve k zadání názvu a stisknete klávesu **ENTER**, zadejte v okně konzoly řetězec.

1. Spuštění programu se zastaví, když dosáhne zarážky a před spuštěním metody `Console.WriteLine`. V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.

1. **Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte. Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.

   1. Pokud okno **okamžité** není viditelné, zobrazte ho výběrem možnosti **ladění** > **Windows** > **Immediate**.

   1. Do příkazového podokna **zadejte** `name = "Gracie"` a stiskněte klávesu **ENTER** .

   1. Do příkazového podokna **zadejte** `date = DateTime.Parse("11/16/2019 5:25 PM")` a stiskněte klávesu **ENTER** .

   Hodnoty proměnných jsou aktualizovány v okně **místních** hodnot.

1. Pokračujte v provádění programu tak, že na panelu nástrojů vyberete tlačítko **pokračovat** nebo vyberete položku nabídky **ladění** > **pokračovat** . Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém** okně.

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.

---

## <a name="set-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nezadá něco? Můžete ji otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*, která přerušuje provádění programu, pokud je splněna jedna nebo více podmínek.

Chcete-li nastavit podmíněný bod přerušení a otestovat, co se stane, když uživatel nezadá řetězec, udělejte toto:

# <a name="c"></a>[C#](#tab/csharp)

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku. V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** . Zaškrtněte políčko pro **podmínky** , pokud ještě není vybraná.

   ![Editor znázorňující panel nastavení zarážky –C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pro **podmíněný výraz**nahraďte "např. x = = 5" následujícím způsobem:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujete podmínku kódu, že volání metody `String.IsNullOrEmpty(name)` je `true` buď, protože `name` nebyla přiřazena hodnota nebo vzhledem k tomu, že její hodnota je prázdný řetězec (""). Místo podmíněného výrazu můžete také určit *Počet přístupů*, který přerušuje spuštění programu před příkazem, který je určen stanoveným počtem opakování, nebo *podmínku filtru*, který přerušuje spuštění programu na základě těchto atributů jako identifikátor vlákna, název procesu nebo název vlákna.

1. Kliknutím na **Zavřít** zavřete dialogové okno.

1. Spusťte program s laděním stisknutím klávesy **F5**.

1. Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu **ENTER** .

1. Vzhledem k tomu, že je podmínka, kterou jste zadali, `name` buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, byla splněna, spuštění programu se zastaví, když dosáhne zarážky a před spuštěním metody `Console.WriteLine`.

1. Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu. V tomto případě je `Main` aktuálně vykonávanou metodou. Všimněte si, že hodnota proměnné `name` je `""`nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém** okně a stisknutím klávesy **ENTER**. Výsledek je `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Okamžité okno vracející hodnotu true po provedení příkazu –C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

1. Vymažte zarážku kliknutím na tečku na levém okraji okna kódu nebo výběrem možnosti **ladit > přepínací zarážku** , když je vybraný řádek kódu.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku. V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** . Zaškrtněte políčko pro **podmínky**.

   ![Editor znázorňující panel nastavení zarážky – Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pro **podmíněný výraz** nahraďte "např. x = 5" následujícím způsobem:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujete podmínku kódu, že volání metody `String.IsNullOrEmpty(name)` je `true` buď, protože `name` nebyla přiřazena hodnota nebo vzhledem k tomu, že její hodnota je prázdný řetězec (""). Místo podmíněného výrazu můžete také určit *Počet přístupů*, který přerušuje spuštění programu před příkazem, který je určen stanoveným počtem opakování, nebo *podmínku filtru*, který přerušuje spuštění programu na základě těchto atributů jako identifikátor vlákna, název procesu nebo název vlákna.

1. Kliknutím na **Zavřít** zavřete dialogové okno.

1. Spusťte program s laděním stisknutím klávesy **F5**.

1. Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu **ENTER** .

1. Vzhledem k tomu, že je podmínka, kterou jste zadali, `name` buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, byla splněna, spuštění programu se zastaví, když dosáhne zarážky a před spuštěním metody `Console.WriteLine`.

1. Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu. V tomto případě je `Main` aktuálně vykonávanou metodou. Všimněte si, že hodnota proměnné `name` je `""`nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém** okně a stisknutím klávesy **ENTER**. Výsledek je `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Okamžité okno vracející hodnotu true po provedení příkazu – Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

1. Vymažte zarážku kliknutím na tečka v levém okraji okna kódu nebo výběrem položky nabídky **ladění > Přepnout zarážku** s vybraným řádkem.

---
## <a name="step-through-a-program"></a>Krokovat program

Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění. Obvykle byste nastavili zarážku a pomocí této funkce mohli sledovat tok programu přes malou část kódu programu. Vzhledem k tomu, že je váš program malý, můžete projít celým programem:

# <a name="c"></a>[C#](#tab/csharp)

1. Na panelu nabídek zvolte možnost **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu **F11**. Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   ![Krok v aplikaci Visual Studio – metoda –C#](./media/debugging-with-visual-studio/step-into-method.png)

   V tomto okamžiku okno **místní** hodnoty ukazuje, že program definoval pouze jednu proměnnou, `args`. Vzhledem k tomu, že jste do programu neprošli žádné argumenty příkazového řádku, je jeho hodnota prázdným polem řetězce. Kromě toho Visual Studio otevřelo prázdné okno konzoly.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio teď zvýrazní další řádek provádění. Jak ukazuje obrázek, byl méně než jeden milisekund, aby provedl kód mezi posledním příkazem a tímto. `args` zůstane jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.

   ![Krok sady Visual Studio ve zdroji metody –C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio zvýrazní příkaz, který obsahuje přiřazení proměnné `name`. V okně **místní** hodnoty se zobrazí `name` `null`a v okně konzoly se zobrazí řetězec "Co je vaše jméno?".

1. Zadáním řetězce v okně konzoly a stisknutím klávesy **ENTER**odpovězte na výzvu. Konzola nereaguje a řetězec, který jste zadali, se v okně konzoly nezobrazí, ale metoda <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> přesto zaznamená vstup.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio zvýrazní příkaz, který obsahuje přiřazení proměnné `date`. Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním metody <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. V okně konzoly se zobrazí také řetězec, který jste zadali na příkazovém řádku.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Okno **místní** hodnoty zobrazuje hodnotu proměnné `date` po přiřazení z vlastnosti <xref:System.DateTime.Now?displayProperty=nameWithType>. Okno konzoly se nezměnilo.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio volá metodu <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. V okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladění** > **Krok ven** nebo stiskněte **SHIFT**+**F11**. Tím se zastaví krok za krokem. V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Na panelu nabídek zvolte možnost **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu **F11**. Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   ![Metoda Visual Studio Step Into – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   V tomto okamžiku okno **místní** hodnoty ukazuje, že program definoval pouze jednu proměnnou, `args`. Vzhledem k tomu, že jste do programu neprošli žádné argumenty příkazového řádku, je jeho hodnota prázdným polem řetězce. Kromě toho Visual Studio otevřelo prázdné okno konzoly.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio teď zvýrazní další řádek provádění. Jak ukazuje obrázek, převzal méně než jeden milisekund, aby spustil kód mezi posledním příkazem a tímto. `args` zůstane jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.

   ![Krok do zdroje metody v aplikaci Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio zvýrazní příkaz, který obsahuje přiřazení proměnné `name`. V okně **místní** hodnoty se zobrazí `name` `Nothing`a v okně konzoly se zobrazí řetězec "Co je vaše jméno?".

1. Zadáním řetězce v okně konzoly a stisknutím klávesy **ENTER**odpovězte na výzvu. Konzola nereaguje a řetězec, který zadáte, se v okně konzoly nezobrazí, ale metoda <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> přesto zaznamená vstup.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio zvýrazní příkaz, který obsahuje přiřazení proměnné `currentDate`. Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním metody <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. V okně konzoly se zobrazí také řetězec zadaný při zobrazení výzvy ke vstupu v konzole nástroje.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Okno konzoly se nezměnilo.

1. Vyberte možnost **ladění** > **Krokovat** s vnořením nebo stiskněte klávesu **F11**. Visual Studio volá metodu <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. V okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladění** > **Krok ven** nebo stiskněte **SHIFT**+**F11**. Tím se zastaví krok za krokem. V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

---

## <a name="build-a-release-version"></a>Sestavení verze pro vydání

Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání. Verze Release zahrnuje optimalizace kompilátoru, které mohou být někdy negativně ovlivněny chování aplikace. Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.

Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Když stisknete klávesu **F5** nebo zvolíte **Sestavit řešení** z nabídky **sestavit** , Visual Studio zkompiluje verzi aplikace. Můžete ho otestovat stejně, jako jste použili ladicí verzi.

## <a name="next-steps"></a>Další kroky

Po deladění aplikace je dalším krokem publikování nasaditelné verze aplikace. Informace o tom, jak to provést, najdete v tématu [publikování aplikace Hello World .NET Core pomocí sady Visual Studio](publishing-with-visual-studio.md).
