---
title: Ladění aplikace C# nebo Visual Basic Hello World .NET Core pomocí sady Visual Studio 2017
description: Zjistěte, jak ladit aplikaci Hello World v jazyce C# nebo Visual Basic pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 12/15/2017
ms.custom: vs-dotnet
ms.openlocfilehash: 4623f4efa8637bd30f378006a92bfc4965429182
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082913"
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a>Ladění aplikace Hello World pomocí sady Visual Studio 2017

Zatím jste postupovali podle kroků v [sestavení Hello World aplikaci v C# pomocí platformy .NET Core v sadě Visual Studio 2017](.\with-visual-studio.md) nebo [sestavení jazyka Visual Basic Hello World aplikace s .NET Core v sadě Visual Studio 2017](vb-with-visual-studio.md) k vytvoření a spusťte jednoduchou konzolovou aplikaci. Po zapisují a zkompilovat aplikaci, můžete začít testování. Visual Studio zahrnuje komplexní sadu ladicí nástroje, které můžete použít při testování a řešení potíží s vaší aplikací.

## <a name="debugging-in-debug-mode"></a>Ladění v režimu ladění

*Ladění* a *vydání* jsou dvě sady Visual Studio výchozí konfigurace sestavení. Aktuální konfigurace sestavení se zobrazí na panelu nástrojů. Následující obrázek panelu nástrojů zobrazí, že Visual Studio je nakonfigurovaný pro vaši aplikaci v kompilaci **ladění** režimu.

   ![Panel nástrojů Visual Studio](./media/debugging-with-visual-studio/toolbar1.png)

By měl vždy začínají při testování aplikace v režimu ladění. Ladění režimu vypne většina optimalizace kompilátoru a poskytuje rozsáhlejší informace během procesu sestavení.

## <a name="setting-a-breakpoint"></a>Nastavením zarážky

Spusťte svůj program v režimu ladění a zkuste několik funkcí ladění:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. A *zarážku* dočasně přeruší provádění aplikace *před* provedením řádku se zarážkou. 

   Nastavit zarážku na řádek, který čte `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` kliknutím na levém okraji okna kódu na tomto řádku nebo kliknutím **ladění** > **Přepnout zarážku** položky nabídky řádku Vybrat. Jak ukazuje následující obrázek, Visual Studio určuje řádek, na kterém je nastavena zarážka ho zvýrazníte a zobrazením červené kolečko v jeho levého okraje.

   ![Visual Studio okna sadou zarážku](./media/debugging-with-visual-studio/setbreakpoint.png)

1. Spusťte program v režimu ladění tak, že vyberete **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů, stisknutím klávesy F5 nebo výběrem **ladění** > **spustit ladění**.

1. Zadejte řetězec v okně konzoly, když program vyzve k zadání názvu a stiskněte klávesu Enter.

1. Zastaví spuštění programu při dosažení zarážky a před `Console.WriteLine` metody. **Automatické hodnoty** okně zobrazí hodnoty proměnných, které se používají kolem aktuálního řádku. **Lokální** okno (které můžete zobrazit kliknutím **místní hodnoty** kartu) zobrazuje hodnoty proměnné, které jsou definovány v aktuálně prováděné metody.

   ![Okno aplikace Visual Studio](./media/debugging-with-visual-studio/break.png)

1. Můžete změnit hodnotu proměnné, chcete-li zjistit, jak to ovlivní váš program. Pokud **podokna** není viditelný, ho zobrazit výběrem **ladění** > **Windows** > **okamžité**položky nabídky. **Podokna** umožňuje pracovat s aplikací, kterou ladíte.

1. Interaktivní můžete změnit hodnoty proměnných. Zadejte `name = "Gracie"` v **podokna** a stiskněte klávesu Enter.

1. Zadejte `date = new DateTime(2016,11,01,11,59,00)` v **podokna** a stiskněte klávesu Enter.

   **Podokna** se zobrazí hodnota proměnné řetězce a vlastnosti <xref:System.DateTime> hodnotu. Kromě toho se aktualizuje hodnotu proměnné v **automatické hodnoty** a **lokální** systému windows.

   ![Okno Automatické hodnoty a příkazové podokno](./media/debugging-with-visual-studio/autosimmediate.png)

1. Pokračovat v provádění programu tak, že vyberete **pokračovat** tlačítko na panelu nástrojů nebo tak, že vyberete **ladění** > **pokračovat** položky nabídky. Hodnoty zobrazené v okně konzoly odpovídají změny provedené v **podokna**.

   ![Okno konzoly zadaná hodnota konektoru na to, co je vaše jméno? řádek následovaný Hello Gracie 11/1/2016 v 11:59](./media/debugging-with-visual-studio/changed.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a ukončení režimu ladění.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. A *zarážku* dočasně přeruší provádění aplikace *před* provedením řádku se zarážkou. 

   Nastavit zarážku na řádek, který čte `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` kliknutím na levém okraji okna kódu na tomto řádku nebo kliknutím **ladění** > **Přepnout zarážku** položky nabídky řádku Vybrat. Jak ukazuje následující obrázek, Visual Studio určuje řádek, na kterém je nastavena zarážka ho zvýrazníte a zobrazením červené kolečko v jeho levého okraje.

   ![Visual Studio okna sadou zarážku](./media/debugging-with-visual-studio/vb-setbreakpoint.png)

1. Spusťte program v režimu ladění tak, že vyberete **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů, stisknutím klávesy F5 nebo výběrem **ladění** > **spustit ladění**.

1. Zadejte řetězec v okně konzoly, když program vyzve k zadání názvu a stiskněte klávesu Enter.

1. Zastaví spuštění programu při dosažení zarážky a před `Console.WriteLine` metody. **Automatické hodnoty** okně zobrazí hodnoty proměnných, které se používají kolem aktuálního řádku. **Lokální** okno (které můžete zobrazit kliknutím **místní hodnoty** kartu) zobrazuje hodnoty proměnné, které jsou definovány v aktuálně prováděné metody.

   ![Okno aplikace Visual Studio](./media/debugging-with-visual-studio/vb-break.png)

1. Můžete změnit hodnotu proměnné, chcete-li zjistit, jak to ovlivní váš program. Pokud **podokna** není viditelný, ho zobrazit výběrem **ladění** > **Windows** > **okamžité**položky nabídky. **Podokna** umožňuje pracovat s aplikací, kterou ladíte.

1. Interaktivní můžete změnit hodnoty proměnných. Zadejte `name = "Gracie"` v **podokna** a stiskněte klávesu Enter.

1. Zadejte `currentDate = new DateTime(2016,11,01,11,59,00)` v **podokna** a stiskněte klávesu Enter.

1. Pokračovat v provádění programu tak, že vyberete **pokračovat** tlačítko na panelu nástrojů nebo tak, že vyberete **ladění** > **pokračovat** položky nabídky. Hodnoty zobrazené v okně konzoly odpovídají změny provedené v **podokna**.

   ![Zobrazuje změněné hodnoty zadané v příkazovém okně konzoly](./media/debugging-with-visual-studio/changed.png)

1. Stisknutím libovolné klávesy ukončete aplikaci a ukončení režimu ladění.
---

## <a name="setting-a-conditional-breakpoint"></a>Nastavením podmíněné zarážky

Program zobrazí řetězec, který uživatel zadá. Co se stane, když uživatel nezadal nic? Můžete ho otestovat pomocí užitečné funkce ladění *podmíněné zarážky*, které program konce provádění, pokud jeden nebo více podmínek.

Pokud chcete nastavit podmíněné zarážky a otestovat, co se stane, když uživatel nezadá řetězec, postupujte takto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Klikněte pravým tlačítkem na červenou tečku představující zarážku. V místní nabídce vyberte **podmínky** otevřít **nastavení zarážek** dialogového okna. Zaškrtněte políčko u **podmínky**.

   ![Panel nastavení zarážky](./media/debugging-with-visual-studio/breakpointsettings.png)

1. Pro **podmíněný výraz** nahradit "např. x == 5" následujícím kódem:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testování pro podmínku kód, který `String.IsNullOrEmpty(name)` volání metody je `true` buď protože *název* nebyla přiřazena hodnota nebo proto, že její hodnota je prázdný řetězec (""). Můžete také určit *počet průchodů*, které přerušení provádění programu, než se příkaz Spustit do zadaného počtu opakování, nebo *podmínka filtru*, který přerušení provádění podle například programu atributy jako identifikátor vlákna, název procesu nebo název vlákna.

1. Vyberte **zavřete** tlačítka zavřete dialogové okno.

1. Spusťte program v režimu ladění.

1. V okně konzoly stisknutím klávesy Enter po zobrazení výzvy zadejte své jméno.

1. Vzhledem k tomu, že jsme zadaná podmínka, `name` je buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, nebyla splněna, zastaví spuštění programu při dosažení zarážky a před `Console.WriteLine` metody.

1. Vyberte **lokální** okno, které zobrazuje hodnoty pro proměnné, které jsou vzhledem k aktuálně prováděné metody, která je `Main` metodu ve svém programu. Zda se zobrazila zpráva hodnotu `name` proměnná je `""`, nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte, hodnota je prázdný řetězec tak, že zadáte následující příkaz v **podokna**. Výsledkem je `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Příkazové podokno vrací hodnotu true, po provedení příkazu](./media/debugging-with-visual-studio/emptystring.png)

1. Vyberte **pokračovat** tlačítko na panelu nástrojů můžete pokračovat v provádění programu.

1. Stisknutím jakékoli klávesy zavřete okno konzoly a ukončení režimu ladění.

1. Vymazat zarážku kliknutím na tečku na levém okraji okna kódu nebo kliknutím **ladit > Přepnout zarážku** položky nabídky s vybraného řádku.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Klikněte pravým tlačítkem na červenou tečku představující zarážku. V místní nabídce vyberte **podmínky** otevřít **nastavení zarážek** dialogového okna. Zaškrtněte políčko u **podmínky**.

   ![Panel nastavení zarážky](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pro **podmíněný výraz** nahradit "např. x = 5" následujícím kódem:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testování pro podmínku kód, který `String.IsNullOrEmpty(name)` volání metody je `True` buď protože *název* nebyla přiřazena hodnota nebo proto, že její hodnota je prázdný řetězec (""). Můžete také určit *počet průchodů*, které přerušení provádění programu, než se příkaz Spustit do zadaného počtu opakování, nebo *podmínka filtru*, který přerušení provádění podle například programu atributy jako identifikátor vlákna, název procesu nebo název vlákna.

1. Vyberte **zavřete** tlačítka zavřete dialogové okno.

1. Spusťte program v režimu ladění.

1. V okně konzoly stisknutím klávesy Enter po zobrazení výzvy zadejte své jméno.

1. Vzhledem k tomu, že jsme zadaná podmínka, `name` je buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, nebyla splněna, zastaví spuštění programu při dosažení zarážky a před `Console.WriteLine` metody.

1. Vyberte **lokální** okno, které zobrazuje hodnoty pro proměnné, které jsou vzhledem k aktuálně prováděné metody, která je `Main` metodu ve svém programu. Zda se zobrazila zpráva hodnotu `name` proměnná je `""`, nebo <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potvrďte, hodnota je prázdný řetězec tak, že zadáte následující příkaz v **podokna**. Výsledkem je `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Příkazové podokno vrací hodnotu true, po provedení příkazu](./media/debugging-with-visual-studio/vb-emptystring.png)

1. Vyberte **pokračovat** tlačítko na panelu nástrojů můžete pokračovat v provádění programu.

1. Stisknutím jakékoli klávesy zavřete okno konzoly a ukončení režimu ladění.

1. Vymazat zarážku kliknutím na tečku na levém okraji okna kódu nebo kliknutím **ladit > Přepnout zarážku** položky nabídky s vybraného řádku.
---
## <a name="stepping-through-a-program"></a>Krokování pomocí programu

Visual Studio také umožňuje kroku řádek po řádku prostřednictvím programu a sledovat jeho výkon. Obvykle by nastavte zarážku a použít tuto funkci Pokud chcete postupovat podle toku programu, i když malou část programového kódu. Protože je malý program, můžete procházet celý program následujícím způsobem:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. V panelu nabídky zvolte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio zvýrazní a zobrazí šipky vedle položky na další řádek provádění.

   ![Okno Visual Studio](./media/debugging-with-visual-studio/stepinto1.png)

   V tomto okamžiku **automatické hodnoty** okno zobrazuje, že váš program má definovaný pouze jednu proměnnou, `args`. Protože jakékoli argumenty příkazového řádku nebyly předány do programu, jeho hodnota je prázdné pole řetězce. Kromě toho Visual Studio otevření okna konzoly prázdné.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio nyní zvýrazňuje další řádek provádění. Jak ukazuje obrázek, vždycky trvalo nejméně jeden milisekund ke spouštění kódu vytvořeného mezi poslední příkaz a ten. `args` zůstane pouze deklarované proměnné a v okně konzoly se zůstává prázdné.

   ![Okno Visual Studio](./media/debugging-with-visual-studio/stepinto2.png)

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio zvýrazní příkazu, který zahrnuje `name` přiřazení proměnné. **Automatické hodnoty** okno ukazuje, že `name` je `null`, a v okně konzoly se zobrazí řetězec "Jaký je název vašeho?".

1. Reakce na příkazovém řádku zadáte řetězec v okně konzoly a stisknutím klávesy Enter. Konzole přestane reagovat a v okně konzoly se nezobrazí řetězec zadáte ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda přesto zaznamenají váš vstup.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio zvýrazní příkazu, který zahrnuje `date` (v jazyce C#) nebo `currentDate` (v jazyce Visual Basic) přiřazení proměnné. **Automatické hodnoty** okno zobrazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnoty vrácené z volání <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda. V okně konzoly se také zobrazí řetězec zadá, když konzole zobrazí výzva k zadání vstupu.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. **Automatické hodnoty** okno zobrazuje hodnotu `date` po přiřazení z proměnné <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost. V okně konzoly se nezmění.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Volání sady Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metody. Hodnoty `date` (nebo `currentDate`) a `name` joinkind proměnné **automatické hodnoty** okna a v okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladění** > **Krokovat s Vystoupením** nebo stiskněte klávesu Shift a klávesy F11. Tím se zastaví provádění krok za krokem. V okně konzoly se zobrazí zprávu a čeká na stisknutím jakékoli klávesy.

1. Stisknutím jakékoli klávesy zavřete okno konzoly a ukončení režimu ladění.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. V panelu nabídky zvolte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio zvýrazní a zobrazí šipky vedle položky na další řádek provádění.

   ![Okno Visual Studio](./media/debugging-with-visual-studio/vb-stepinto1.png)

   AT tento bod, protože nebyly předány jakékoli argumenty příkazového řádku k programu, **automatické hodnoty** okno zobrazuje hodnotu `args` proměnná je pole prázdný řetězec. Kromě toho Visual Studio otevření okna konzoly prázdné.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio nyní zvýrazňuje další řádek provádění. Jak ukazuje obrázek, vždycky trvalo nejméně jeden milisekund ke spouštění kódu vytvořeného mezi poslední příkaz a ten. `args` zůstane pouze deklarované proměnné a v okně konzoly se zůstává prázdné.

   ![Okno Visual Studio](./media/debugging-with-visual-studio/vb-stepinto2.png)

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio zvýrazní příkazu, který zahrnuje `name` přiřazení proměnné. **Automatické hodnoty** okno ukazuje, že `name` je `Nothing`, a v okně konzoly se zobrazí řetězec "Jaký je název vašeho?".

1. Reakce na příkazovém řádku zadáte řetězec v okně konzoly a stisknutím klávesy Enter. Konzole přestane reagovat a v okně konzoly se nezobrazí řetězec zadáte ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda přesto zaznamenají váš vstup.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Visual Studio zvýrazní příkazu, který zahrnuje `date` (v jazyce C#) nebo `currentDate` (v jazyce Visual Basic) přiřazení proměnné. **Automatické hodnoty** okno zobrazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnoty vrácené z volání <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda. V okně konzoly se také zobrazí řetězec zadá, když konzole zobrazí výzva k zadání vstupu.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. **Automatické hodnoty** okno zobrazuje hodnotu `date` po přiřazení z proměnné <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost. V okně konzoly se nezmění.

1. Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesy F11. Volání sady Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metody. Hodnoty `date` (nebo `currentDate`) a `name` joinkind proměnné **automatické hodnoty** okna a v okně konzoly se zobrazí formátovaný řetězec.

1. Vyberte **ladění** > **Krokovat s Vystoupením** nebo stiskněte klávesu Shift a klávesy F11. Tím se zastaví provádění krok za krokem. V okně konzoly se zobrazí zprávu a čeká na stisknutím jakékoli klávesy.

1. Stisknutím jakékoli klávesy zavřete okno konzoly a ukončení režimu ladění.
---

## <a name="building-a-release-version"></a>Sestavení verze pro vydání

Jakmile jste otestovali sestavení pro ladění vaší aplikace, by měl také zkompilují a otestují vydanou verzi. Prodejní verze zahrnuje optimalizace kompilátoru, které mohou někdy negativně ovlivnit chování aplikace. Optimalizace kompilátoru, které jsou navržené ke zlepšení výkonu můžete například vytvořit časování v asynchronní nebo vícevláknových aplikacích.

Pro vytváření a testování verze vaší konzolové aplikace, změňte konfiguraci buildu na panelu nástrojů z **ladění** k **vydání**.

![Image](./media/debugging-with-visual-studio/toolbar2.png)

Při stisknutí klávesy F5 nebo vyberte **sestavit řešení** z **sestavení** nabídky sady Visual Studio zkompiluje verze vaší konzolové aplikace. Ji můžete otestovat, jako jste to udělali ladicí verze aplikace.

Po dokončení ladění vaší aplikace, dalším krokem je publikovat nasaditelný verzi vaší aplikace. Informace o tom, jak to provést, najdete v tématu [publikování aplikace Hello World pomocí sady Visual Studio 2017](./publishing-with-visual-studio.md).
