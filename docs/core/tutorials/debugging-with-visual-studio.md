---
title: Ladění aplikace Hello World .NET Core pomocí sady Visual Studio 2017
description: Naučte se ladit aplikaci Hello World napsanou v C# nebo Visual Basic se sadou Visual Studio 2017.
ms.date: 12/15/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f318c163db6cfdd6de5aa99edebfeeb4bb470a02
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926169"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio-2017"></a>Ladění aplikace Hello World v jazyce C# nebo Visual Basic .NET Core pomocí sady Visual Studio 2017

Zatím jste postupovali podle kroků v části [vytvoření C# Hello World aplikace pomocí .NET Core v aplikaci Visual Studio 2017](with-visual-studio.md) nebo [sestavení Visual Basic Hello World aplikaci pomocí .NET core v aplikaci Visual Studio 2017](vb-with-visual-studio.md) pro vytvoření a spuštění jednoduché konzolové aplikace. Jakmile napíšete a zkompilujete aplikaci, můžete ji začít testovat. Sada Visual Studio obsahuje komplexní sadu ladicích nástrojů, které můžete použít při testování a odstraňování potíží s aplikací. 

## <a name="debugging-in-debug-mode"></a>Ladění v režimu ladění

*Ladění* a *vydání* jsou dvě z výchozích konfigurací sestavení sady Visual Studio. Aktuální konfigurace sestavení se zobrazí na panelu nástrojů. Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro kompilaci aplikace v režimu **ladění** .

   ![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Vždy byste měli začít testováním programu v režimu ladění. Režim ladění vypne většinu optimalizací kompilátoru a poskytuje bohatší informace během procesu sestavení.

## <a name="setting-a-breakpoint"></a>Nastavením zarážky

Spusťte program v režimu ladění a vyzkoušejte několik funkcí ladění:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. *Zarážka* dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou. 

   Nastavte zarážku na řádku, který čte `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` kliknutím na levý okraj okna kódu na daném řádku, nebo výběrem položky nabídky **ladit** > **přepínací zarážku** s vybraným řádkem. Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červeného kruhu v jeho levém okraji.

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Spusťte program v režimu ladění tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknete klávesu F5 nebo zvolíte **ladění** > **Spustit ladění**.

1. Pokud se program vyzve k zadání názvu a stisknete klávesu ENTER, zadejte v okně konzoly řetězec.

1. Spuštění programu se zastaví, když dosáhne zarážky a před `Console.WriteLine` tím, než se metoda spustí. Okno **Automatické** hodnoty zobrazuje hodnoty proměnných, které se používají kolem aktuálního řádku. Okno **místních** hodnot (které můžete zobrazit kliknutím na kartu **místní** hodnoty) zobrazí hodnoty proměnných, které jsou definovány v aktuálně vykonávané metodě.

   ![Snímek obrazovky se zarážkou v aplikaci Visual Studio.](./media/debugging-with-visual-studio/breakpoint-console-window.png)

1. Můžete změnit hodnotu proměnných, abyste viděli, jak ovlivní váš program. Pokud **okno okamžité** není viditelné, zobrazte ho výběrem**položky nabídky** **ladit** > **Windows** > hned. **Okamžité okno** vám umožní pracovat s aplikací, kterou ladíte.

1. Hodnoty proměnných můžete interaktivně měnit. Do `name = "Gracie"` příkazového **podokna** zadejte a stiskněte klávesu ENTER.

1. Do `date = new DateTime(2016,11,01,11,59,00)` příkazového **podokna** zadejte a stiskněte klávesu ENTER.

   V **příkazovém okně** se zobrazí hodnota proměnné řetězce a vlastnosti <xref:System.DateTime> hodnoty. Kromě toho je hodnota proměnných aktualizována v oknech **Automatické** hodnoty a **místní** hodnoty.

   ![Okno Automatické hodnoty a příkazové okno](./media/debugging-with-visual-studio/autos-immediate-window.png)

1. Pokračujte v provádění programu tak, že na panelu nástrojů kliknete na tlačítko **pokračovat** nebo vyberete položku nabídky **ladit** > **pokračovat** . Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém okně**.

   ![Okno konzoly zobrazující hodnotu zdířka v poli jaký je vaše jméno? výzva následovaná Gracie Hello](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a ukončete režim ladění.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. *Zarážka* dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou. 

   Nastavte zarážku na řádku, který čte `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` kliknutím na levý okraj okna kódu na daném řádku, nebo výběrem položky nabídky **ladit** > **přepínací zarážku** s vybraným řádkem. Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červeného kruhu v jeho levém okraji.

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/vb-set-breakpoint-in-editor.png)

1. Spusťte program v režimu ladění tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknete klávesu F5 nebo zvolíte **ladění** > **Spustit ladění**.

1. Pokud se program vyzve k zadání názvu a stisknete klávesu ENTER, zadejte v okně konzoly řetězec.

1. Spuštění programu se zastaví, když dosáhne zarážky a před `Console.WriteLine` tím, než se metoda spustí. Okno **Automatické** hodnoty zobrazuje hodnoty proměnných, které se používají kolem aktuálního řádku. Okno **místních** hodnot (které můžete zobrazit kliknutím na kartu **místní** hodnoty) zobrazí hodnoty proměnných, které jsou definovány v aktuálně vykonávané metodě.

   ![Okno aplikace Visual Studio na zarážce](./media/debugging-with-visual-studio/vb-stop-at-breakpoint.png)

1. Můžete změnit hodnotu proměnných, abyste viděli, jak ovlivní váš program. Pokud **okno okamžité** není viditelné, zobrazte ho výběrem**položky nabídky** **ladit** > **Windows** > hned. **Okamžité okno** vám umožní pracovat s aplikací, kterou ladíte.

1. Hodnoty proměnných můžete interaktivně měnit. Do `name = "Gracie"` příkazového **podokna** zadejte a stiskněte klávesu ENTER.

1. Do `currentDate = new DateTime(2016,11,01,11,59,00)` příkazového **podokna** zadejte a stiskněte klávesu ENTER.

1. Pokračujte v provádění programu tak, že na panelu nástrojů kliknete na tlačítko **pokračovat** nebo vyberete položku nabídky **ladit** > **pokračovat** . Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém okně**.

   ![Okno konzoly zobrazující změněné hodnoty zadané v příkazovém okně](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a ukončete režim ladění.

---

## <a name="setting-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nezadá něco? Můžete ji otestovat s užitečnou funkcí ladění, *podmíněná zarážka*, která přerušuje provádění programu, pokud je splněna jedna nebo více podmínek.

Chcete-li nastavit podmíněný bod přerušení a otestovat, co se stane, když uživatel nezadá řetězec, udělejte toto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku. V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** . Zaškrtněte políčko pro **podmínky**.

   ![Editor znázorňující panel nastavení zarážky –C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pro **podmíněný výraz** nahraďte "např. x = = 5" následujícím způsobem:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujete podmínku kódu, že `String.IsNullOrEmpty(name)` volání metody je `true` buď na to, že *název* není přiřazený nebo že má hodnotu prázdný řetězec (""). Můžete také zadat *počet*průchodů, který přerušuje spuštění programu před provedením určitého příkazu, nebo *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, proces název nebo název vlákna.

1. Kliknutím na tlačítko **Zavřít** zavřete dialogové okno.

1. Spusťte program v režimu ladění.

1. Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu ENTER.

1. Vzhledem k tomu, že podmínka `name` , kterou `null` jsme <xref:System.String.Empty?displayProperty=nameWithType>určili, je nebo, byla splněna, spuštění programu se zastaví, když `Console.WriteLine` dosáhne zarážky a předtím, než se metoda spustí.

1. Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou lokální pro právě spuštěnou metodu, což je `Main` metoda v programu. Všimněte si, že hodnota `name` proměnné je `""`nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém okně**. Výsledek je `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Okamžité okno vracející hodnotu true po provedení příkazu –C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončete režim ladění.

1. Vymažte zarážku kliknutím na tečka v levém okraji okna kódu nebo výběrem položky nabídky **ladění > Přepnout zarážku** s vybraným řádkem.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku. V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** . Zaškrtněte políčko pro **podmínky**.

   ![Editor znázorňující panel nastavení zarážky – Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pro **podmíněný výraz** nahraďte "např. x = 5" následujícím způsobem:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujete podmínku kódu, že `String.IsNullOrEmpty(name)` volání metody je `True` buď na to, že *název* není přiřazený nebo že má hodnotu prázdný řetězec (""). Můžete také zadat *počet*průchodů, který přerušuje spuštění programu před provedením určitého příkazu, nebo *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, proces název nebo název vlákna.

1. Kliknutím na tlačítko **Zavřít** zavřete dialogové okno.

1. Spusťte program v režimu ladění.

1. Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu ENTER.

1. Vzhledem k tomu, že podmínka `name` , kterou `null` jsme <xref:System.String.Empty?displayProperty=nameWithType>určili, je nebo, byla splněna, spuštění programu se zastaví, když `Console.WriteLine` dosáhne zarážky a předtím, než se metoda spustí.

1. Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou lokální pro právě spuštěnou metodu, což je `Main` metoda v programu. Všimněte si, že hodnota `name` proměnné je `""`nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém okně**. Výsledek je `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

  ![Okamžité okno vracející hodnotu true po provedení příkazu – Visual Basic](./media/debugging-with-visual-studio/vb-immediate-window-output.png)

1. Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončete režim ladění.

1. Vymažte zarážku kliknutím na tečka v levém okraji okna kódu nebo výběrem položky nabídky **ladění > Přepnout zarážku** s vybraným řádkem.

---
## <a name="stepping-through-a-program"></a>Krokování přes program

Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění. Obvykle byste nastavili zarážku a pomocí této funkce mohli sledovat tok programu přes malou část kódu programu. Vzhledem k tomu, že je váš program malý, můžete procházet celý program pomocí následujícího postupu:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Na panelu nabídek zvolte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   ![Krok v aplikaci Visual Studio – metoda –C#](./media/debugging-with-visual-studio/step-into-method.png)

   V tomto okamžiku okno **Automatické** hodnoty zobrazí, že program definoval pouze jednu proměnnou `args`. Vzhledem k tomu, že jste do programu neprošli žádné argumenty příkazového řádku, je jeho hodnota prázdným polem řetězce. Kromě toho Visual Studio otevřelo prázdné okno konzoly.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio teď zvýrazní další řádek provádění. Jak ukazuje obrázek, převzal méně než jeden milisekund, aby spustil kód mezi posledním příkazem a tímto. `args`zůstane jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.

   ![Krok sady Visual Studio ve zdroji metody –C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné. Okno **Automatické** hodnoty ukazuje, `name` `null`a okno konzoly zobrazuje řetězec "Co je vaše jméno?".

1. Zadáním řetězce v okně konzoly a stisknutím klávesy ENTER odpovězte na výzvu. Konzola nereaguje a řetězec, který zadáte, se v okně konzoly nezobrazí, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda přesto zaznamená vstup.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné (in C#) `currentDate` nebo (in Visual Basic). Okno **Automatické** hodnoty zobrazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. V okně konzoly se zobrazí také řetězec zadaný při zobrazení výzvy ke vstupu v konzole nástroje.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Okno **Automatické** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti. Okno konzoly se nezměnilo.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu. Hodnoty `date` (nebo `currentDate`) a `name` proměnné se zobrazí v okně **Automatické** hodnoty a v okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladit** > **Krok ven** nebo stiskněte Shift a klávesu F11. Tím se zastaví krok za krokem. V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončete režim ladění.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Na panelu nabídek zvolte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   ![Metoda Visual Studio Step Into – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   V tomto okamžiku, protože jste do programu neprošli žádné argumenty příkazového řádku, zobrazí okno **Automatické** hodnoty, že hodnota `args` proměnné je prázdné pole řetězce. Kromě toho Visual Studio otevřelo prázdné okno konzoly.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio teď zvýrazní další řádek provádění. Jak ukazuje obrázek, převzal méně než jeden milisekund, aby spustil kód mezi posledním příkazem a tímto. `args`zůstane jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.

   ![Krok do zdroje metody v aplikaci Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné. Okno **Automatické** hodnoty ukazuje, `name` `Nothing`a okno konzoly zobrazuje řetězec "Co je vaše jméno?".

1. Zadáním řetězce v okně konzoly a stisknutím klávesy ENTER odpovězte na výzvu. Konzola nereaguje a řetězec, který zadáte, se v okně konzoly nezobrazí, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda přesto zaznamená vstup.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné (in C#) `currentDate` nebo (in Visual Basic). Okno **Automatické** hodnoty zobrazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. V okně konzoly se zobrazí také řetězec zadaný při zobrazení výzvy ke vstupu v konzole nástroje.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Okno **Automatické** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti. Okno konzoly se nezměnilo.

1. Vyberte možnost **ladit** > **Krok do** nebo stiskněte klávesu F11. Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu. Hodnoty `date` (nebo `currentDate`) a `name` proměnné se zobrazí v okně **Automatické** hodnoty a v okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladit** > **Krok ven** nebo stiskněte Shift a klávesu F11. Tím se zastaví krok za krokem. V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.

1. Stisknutím libovolné klávesy zavřete okno konzoly a ukončete režim ladění.

---

## <a name="building-a-release-version"></a>Sestavení verze pro vydání

Po otestování sestavení ladění aplikace byste měli také kompilovat a testovat verzi vydání. Verze Release zahrnuje optimalizace kompilátoru, které mohou být někdy negativně ovlivněny chování aplikace. Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v asynchronních nebo vícevláknových aplikacích.

Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Když stisknete klávesu F5 nebo zvolíte **Sestavit řešení** z nabídky **sestavení** , Visual Studio zkompiluje verzi vydanou konzolovou aplikací. Můžete ho otestovat stejným způsobem jako ladicí verze aplikace.

Po dokončení ladění aplikace je dalším krokem publikování nasaditelné verze vaší aplikace. Informace o tom, jak to provést, najdete v tématu [publikování Hello World aplikace pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).
