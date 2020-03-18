---
title: Ladění aplikace Hello World .NET Core pomocí sady Visual Studio
description: Přečtěte si, jak ladit aplikaci Hello World napsanou v jazyce C# nebo Visual Basic pomocí sady Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156670"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Ladění aplikace C# nebo Visual Basic .NET Core Hello World pomocí sady Visual Studio

Zatím jste postupovali podle kroků v [části Vytvoření první aplikace konzoly .NET Core v sadě Visual Studio 2019](with-visual-studio.md) k vytvoření a spuštění jednoduché konzolové aplikace. Jakmile jste napsali a zkompilovali aplikaci, můžete ji začít testovat. Visual Studio obsahuje komplexní sadu ladicích nástrojů, které můžete použít k řešení potíží s aplikací.

## <a name="debug-build-configuration"></a>Ladění konfigurace sestavení

*Ladění* a *vydání* jsou dvě výchozí konfigurace sestavení sady Visual Studio. Aktuální konfigurace sestavení je zobrazena na panelu nástrojů. Následující obrázek panelu nástrojů ukazuje, že Visual Studio je nakonfigurováno pro kompilaci ladicí verze aplikace:

![Panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Začněte spuštěním verze ladění aplikace. Konfigurace sestavení ladění vypne většinu optimalizace kompilátoru a poskytuje bohatší informace během procesu sestavení.

## <a name="set-a-breakpoint"></a>Nastavení zarážky

Spusťte program a vyzkoušejte několik funkcí ladění:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Nastavte *zarážku* na `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` řádku, který čte kliknutím na levém okraji okna kódu na tomto řádku. Zarážku můžete také nastavit umístěním stříšky do řádku kódu a stisknutím **klávesy F9** nebo výběrem **možnosti Ladění** > **přepínací zarážky z** řádku nabídek.

   Zarážka dočasně přeruší provádění aplikace *před* provedením řádku s zarážkou.

   Jak ukazuje následující obrázek, Visual Studio označuje řádek, na kterém je zarážka nastavena zvýrazněním a zobrazením červeného kruhu v levém okraji.

   ![Okno Programu sady Visual Studio s nastavenou zarážkou](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Spusťte program v režimu ladění výběrem tlačítka **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknutím **klávesy F5**nebo volbou **Ladění** > **ladění spustit ladění**.

1. Když program vyzve k zadání názvu, zadejte řetězec do okna konzoly a stiskněte **klávesu Enter**.

1. Spuštění programu se zastaví, když dosáhne `Console.WriteLine` zarážky a před spuštěním metody. Místní **Locals** okno zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.

   ![Snímek obrazovky s zarážkou v Sadě Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. Okno **Okamžité** umožňuje interakci s aplikací, kterou ladíte. Můžete interaktivně změnit hodnotu proměnných a zjistit, jak ovlivňuje váš program.

   1. Pokud okno **Okamžité** není viditelné, zobrazte ho tak, že zvolíte **Ladění** > **systému Windows** > **Immediate**.

   1. Zadejte `name = "Gracie"` do okna **Okamžité** a stiskněte klávesu **Enter.**

   1. Zadejte `date = DateTime.Parse("11/16/2019 5:25 PM")` do okna **Okamžité** a stiskněte klávesu **Enter.**

   Okno **Okamžité** zobrazuje hodnotu proměnné řetězce a <xref:System.DateTime> vlastnosti hodnoty. Kromě toho jsou aktualizovány hodnoty proměnných v okně **Locals.**

   ![Místní a okamžitá okna windows ve Visual Studiu 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Pokračujte v provádění programu výběrem tlačítka **Pokračovat** na panelu nástrojů nebo výběrem **možnosti Pokračovat** > **v**ladění . Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v okně **Okamžité.**

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Nastavte *zarážku* na `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` řádku, který čte kliknutím na levém okraji okna kódu na tomto řádku. Zarážku můžete také nastavit umístěním stříšky na požadovaný řádek a pak zvolte **ladění** > **přepnout zarážku** z řádku nabídek.

   Zarážka dočasně přeruší provádění aplikace *před* provedením řádku s zarážkou.

   Jak ukazuje následující obrázek, Visual Studio označuje řádek, na kterém je zarážka nastavena zvýrazněním a zobrazením červeného kruhu v levém okraji.

   ![Okno Programu sady Visual Studio s nastavenou zarážkou](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Spusťte program v režimu ladění výběrem tlačítka **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknutím **klávesy F5**nebo volbou **Ladění** > **ladění spustit ladění**.

1. Když program vyzve k zadání názvu, zadejte řetězec do okna konzoly a stiskněte **klávesu Enter**.

1. Spuštění programu se zastaví, když dosáhne `Console.WriteLine` zarážky a před spuštěním metody. Místní **Locals** okno zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.

1. Okno **Okamžité** umožňuje interakci s aplikací, kterou ladíte. Můžete interaktivně změnit hodnotu proměnných a zjistit, jak ovlivňuje váš program.

   1. Pokud okno **Okamžité** není viditelné, zobrazte ho tak, že zvolíte **Ladění** > **systému Windows** > **Immediate**.

   1. Zadejte `name = "Gracie"` do okna **Okamžité** a stiskněte klávesu **Enter.**

   1. Zadejte `date = DateTime.Parse("11/16/2019 5:25 PM")` do okna **Okamžité** a stiskněte klávesu **Enter.**

   Hodnoty proměnných jsou aktualizovány v okně **Locals.**

1. Pokračujte v provádění programu výběrem tlačítka **Pokračovat** na panelu nástrojů nebo výběrem položky**nabídky** Pokračovat v **ladění.** >  Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v okně **Okamžité.**

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.

---

## <a name="set-a-conditional-breakpoint"></a>Nastavení podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nic nezadá? Můžete otestovat pomocí užitečné funkce ladění s názvem *podmíněné zarážky*, která přeruší spuštění programu, pokud jsou splněny jednu nebo více podmínek.

Chcete-li nastavit podmíněnou zarážku a otestovat, co se stane, když uživatel nezadá řetězec, postupujte takto:

# <a name="c"></a>[C #](#tab/csharp)

1. Klikněte pravým tlačítkem myši na červenou tečku, která představuje zarážku. V místní nabídce vyberte **Podmínky,** chcete-li otevřít dialogové okno **Nastavení zarážky.** Zaškrtněte políčko **Podmínky,** pokud ještě není vybrané.

   ![Editor zobrazující panel nastavení zarážky - C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pro **podmíněný výraz**nahraďte "např. x == 5" následujícím:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujete podmínku kódu, že `String.IsNullOrEmpty(name)` volání metody `true` je `name` buď proto, že nebyla přiřazena hodnota, nebo protože jeho hodnota je prázdný řetězec (""). Namísto podmíněného výrazu můžete také určit *počet přístupů*, který přeruší spuštění programu před provedením příkazu zadaným počtem opakování nebo *podmínkou filtru*, která přeruší spuštění programu na základě těchto atributů, jako je identifikátor vlákna, název procesu nebo název vlákna.

1. Chcete-li zavřít dialogové okno, vyberte **Zavřít.**

1. Spusťte program s laděním stisknutím **klávesy F5**.

1. V okně konzoly stiskněte klávesu **Enter,** když se zobrazí výzva k zadání jména.

1. Vzhledem `name` k tomu, `null` že <xref:System.String.Empty?displayProperty=nameWithType>zadaná podmínka je buď nebo , byla splněna, provádění programu se zastaví, jakmile dosáhne zarážky a před spuštěním `Console.WriteLine` metody.

1. Vyberte okno **Locals,** které zobrazuje hodnoty proměnných, které jsou místní pro aktuálně spuštěnou metodu. V tomto `Main` případě je aktuálně spuštěná metoda. Všimněte si, `name` že `""`hodnota <xref:System.String.Empty?displayProperty=nameWithType>proměnné je , nebo .

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu do okna **Okamžité** a stisknutím **klávesy Enter**. Výsledkem `true`je .

   ```csharp
   ? name == String.Empty
   ```

   ![Okamžité okno vrací hodnotu true po provedení příkazu - C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Chcete-li pokračovat v provádění programu, vyberte na panelu nástrojů tlačítko **Pokračovat.**

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

1. Zrušte zarážku kliknutím na tečku v levém okraji okna kódu nebo výběrem **možnosti Ladění > Přepnout zarážku,** když je vybrán řádek kódu.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Klikněte pravým tlačítkem myši na červenou tečku, která představuje zarážku. V místní nabídce vyberte **Podmínky,** chcete-li otevřít dialogové okno **Nastavení zarážky.** Zaškrtněte políčko **Podmínky**.

   ![Editor zobrazující panel nastavení zarážky – Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Podmíněný **výraz** nahraďte "např. x = 5" následujícím:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujete podmínku kódu, že `String.IsNullOrEmpty(name)` volání metody `true` je `name` buď proto, že nebyla přiřazena hodnota, nebo protože jeho hodnota je prázdný řetězec (""). Namísto podmíněného výrazu můžete také určit *počet přístupů*, který přeruší spuštění programu před provedením příkazu zadaným počtem opakování nebo *podmínkou filtru*, která přeruší spuštění programu na základě těchto atributů, jako je identifikátor vlákna, název procesu nebo název vlákna.

1. Chcete-li zavřít dialogové okno, vyberte **Zavřít.**

1. Spusťte program s laděním stisknutím **klávesy F5**.

1. V okně konzoly stiskněte klávesu **Enter,** když se zobrazí výzva k zadání jména.

1. Vzhledem `name` k tomu, `null` že <xref:System.String.Empty?displayProperty=nameWithType>zadaná podmínka je buď nebo , byla splněna, provádění programu se zastaví, jakmile dosáhne zarážky a před spuštěním `Console.WriteLine` metody.

1. Vyberte okno **Locals,** které zobrazuje hodnoty proměnných, které jsou místní pro aktuálně spuštěnou metodu. V tomto `Main` případě je aktuálně spuštěná metoda. Všimněte si, `name` že `""`hodnota <xref:System.String.Empty?displayProperty=nameWithType>proměnné je , nebo .

1. Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu do okna **Okamžité** a stisknutím **klávesy Enter**. Výsledkem `true`je .

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Okamžité okno vrací hodnotu true po provedení příkazu - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Chcete-li pokračovat v provádění programu, vyberte na panelu nástrojů tlačítko **Pokračovat.**

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

1. Zrušte zarážku kliknutím na tečku v levém okraji okna kódu nebo výběrem položky nabídky **Ladění > Přepnout zarážku** s vybraným řádkem.

---
## <a name="step-through-a-program"></a>Krokovat programem

Visual Studio také umožňuje krok krok za krokem prostřednictvím programu a sledovat jeho provádění. Obvykle byste nastavili zarážku a pomocí této funkce sledovali tok programu přes malou část kódu programu. Vzhledem k tomu, že váš program je malý, můžete krokovat celý program:

# <a name="c"></a>[C #](#tab/csharp)

1. Na řádku nabídek zvolte **Ladění** > **kroku do** nebo stiskněte **klávesu F11**. Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   ![Visual Studio krok do metody - C #](./media/debugging-with-visual-studio/step-into-method.png)

   V tomto okamžiku **locals** okno ukazuje, že váš `args`program definoval pouze jednu proměnnou, . Vzhledem k tomu, že jste programu nepředali žádné argumenty příkazového řádku, jeho hodnotou je prázdné pole řetězců. Kromě toho visual studio otevřelprázdné okno konzoly.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio nyní zvýrazní další řádek provádění. Jak ukazuje obrázek, trvalo méně než jednu milisekundu spustit kód mezi poslední příkaz a tento. `args`zůstává jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.

   ![Krok visual studia ve zdroji metody - C #](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `name` proměnné. Místní **Locals** okno ukazuje, že `name` je `null`a v okně konzoly se zobrazí řetězec "Jaké je vaše jméno?".

1. Na výzvu odpovíte zadáním řetězce v okně konzoly a stisknutím **klávesy Enter**. Konzole neodpovídá a zadaný řetězec se v okně konzoly nezobrazí, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda přesto zachytí váš vstup.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `date` proměnné. Místní **Locals** okno zobrazuje hodnotu vrácenou <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> voláním metody. V okně konzoly se také zobrazí řetězec, který jste zadali na výzvu.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Místní **Locals** okno zobrazuje hodnotu `date` proměnné po přiřazení <xref:System.DateTime.Now?displayProperty=nameWithType> z vlastnosti. Okno konzoly se nezmění.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> volá metodu. V okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **Možnost Ladění krok** > **ven** nebo stiskněte **Shift**+**F11**. To zastaví provádění krok za krokem. V okně konzoly se zobrazí zpráva a čeká, až stisknete klávesu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Na řádku nabídek zvolte **Ladění** > **kroku do** nebo stiskněte **klávesu F11**. Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.

   ![Visual Studio krok do metody - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   V tomto okamžiku **locals** okno ukazuje, že váš `args`program definoval pouze jednu proměnnou, . Vzhledem k tomu, že jste programu nepředali žádné argumenty příkazového řádku, jeho hodnotou je prázdné pole řetězců. Kromě toho visual studio otevřelprázdné okno konzoly.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio nyní zvýrazní další řádek provádění. Jak ukazuje obrázek, trvalo méně než jednu milisekundu spustit kód mezi poslední příkaz a tento. `args`zůstává jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.

   ![Visual Studio krok do zdroje metody - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `name` proměnné. Místní **Locals** okno ukazuje, že `name` je `Nothing`a v okně konzoly se zobrazí řetězec "Jaké je vaše jméno?".

1. Na výzvu odpovíte zadáním řetězce v okně konzoly a stisknutím **klávesy Enter**. Konzole neodpovídá a řetězec, který zadáte, se nezobrazí v okně <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> konzoly, ale metoda přesto zachytí váš vstup.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `currentDate` proměnné. Místní **Locals** okno zobrazuje hodnotu vrácenou <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> voláním metody. V okně konzoly se také zobrazí řetězec zadaný, když konzole vyzvala k zadání vstupu.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Okno konzoly se nezmění.

1. Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> volá metodu. V okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **Možnost Ladění krok** > **ven** nebo stiskněte **Shift**+**F11**. To zastaví provádění krok za krokem. V okně konzoly se zobrazí zpráva a čeká, až stisknete klávesu.

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.

---

## <a name="build-a-release-version"></a>Vytvoření verze vydání

Po otestování verze ladění aplikace, měli byste také zkompilovat a otestovat verzi vydání. Verze verze obsahuje optimalizace kompilátoru, které mohou někdy negativně ovlivnit chování aplikace. Například optimalizace kompilátoru, které jsou navrženy ke zlepšení výkonu můžete vytvořit podmínky časování v aplikacích s více vlákny.

Chcete-li vytvořit a otestovat verzi aplikace konzoly, změňte konfiguraci sestavení na panelu nástrojů z **Ladění** na **Verzi**.

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Když stisknete **klávesu F5** nebo zvolte **sestavit řešení** z nabídky **Sestavení,** Visual Studio zkompiluje verzi aplikace. Můžete jej otestovat stejně jako ladicí verze.

## <a name="next-steps"></a>Další kroky

Po odladění aplikace je dalším krokem publikování nasaditelné verze aplikace. Informace o tom, jak to provést, naleznete [v tématu publikování aplikace .NET Core Hello World pomocí sady Visual Studio](publishing-with-visual-studio.md).
