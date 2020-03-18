---
title: Přístup k objektům interop sady Office – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700832"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Přístup k objektům interop sady Office (Průvodce programováním jazyka C#)

C# má funkce, které zjednodušují přístup k objektům rozhraní API sady Office. Nové funkce zahrnují pojmenované a volitelné argumenty, nový typ s názvem `dynamic`a schopnost předat argumenty referenčním parametrům v metodách COM, jako by se jednalo o parametry hodnoty.

V tomto tématu budete používat nové funkce k napsání kódu, který vytvoří a zobrazí list aplikace Microsoft Office Excel. Poté napíšete kód pro přidání dokumentu aplikace Office Word, který obsahuje ikonu propojenou s listem aplikace Excel.

Chcete-li tento návod dokončit, musíte mít v počítači nainstalovanou aplikaci Microsoft Office Excel 2007 a Microsoft Office Word 2007 nebo novější verze.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Vytvoření nové konzolové aplikace

1. Spusťte Visual Studio.

2. V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**. Zobrazí se dialogové okno **Nový projekt**.

3. V podokně **Nainstalované šablony** rozbalte **položku Visual C#** a klepněte na tlačítko **Windows**.

4. Podívejte se na začátek dialogového okna **Nový projekt** a ujistěte se, že **rozhraní .NET Framework 4** (nebo novější verze) je vybránjako cílová architektura.

5. V podokně **Šablony** klepněte na položku **Konzolová aplikace**.

6. Do pole **Název** zadejte název projektu.

7. Klikněte na tlačítko **OK**.

     Nový projekt se zobrazí v **Průzkumníku řešení**.

## <a name="to-add-references"></a>Přidání odkazů

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a potom klikněte na **příkaz Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz.**

2. Na stránce **Sestavení** vyberte v seznamu **Název součásti** položku **Microsoft.Office.Interop.Word** a podržte klávesu CTRL a vyberte **položku Microsoft.Office.Interop.Excel**.  Pokud sestavy nevidíte, bude pravděpodobně nutné zajistit jejich instalaci a zobrazení. Postup: [Instalace primárních sestavení mezi opačnou operací sady Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. Klikněte na tlačítko **OK**.

## <a name="to-add-necessary-using-directives"></a>Chcete-li přidat nezbytné pomocí směrnic

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *soubor Program.cs* a potom klepněte na příkaz Zobrazit **kód**.

2. Do horní `using` části souboru kódu přidejte následující direktivy:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Vytvoření seznamu bankovních účtů

1. Vložte následující definici třídy `Program` do **Program.cs**pod třídu.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. Přidejte následující kód `Main` do metody `bankAccounts` a vytvořte seznam, který obsahuje dva účty.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Deklarování metody, která exportuje informace o účtu do aplikace Excel

1. Přidejte do třídy následující metodu `Program` pro nastavení listu aplikace Excel.

     Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> má volitelný parametr pro určení konkrétní šablony. Volitelné parametry, nové v C# 4, umožňují vynechat argument pro tento parametr, pokud chcete použít výchozí hodnotu parametru. Protože v následujícím kódu není `Add` odeslán žádný argument, použije výchozí šablonu a vytvoří nový sešit. Ekvivalentní příkaz v dřívějších verzích jazyka C# `ExcelApp.Workbooks.Add(Type.Missing)`vyžaduje zástupný argument: .

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. Na konec přidejte následující `DisplayInExcel`kód . Kód vloží hodnoty do prvních dvou sloupců prvního řádku listu.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. Na konec přidejte následující `DisplayInExcel`kód . Smyčka `foreach` umístí informace ze seznamu účtů do prvních dvou sloupců po sobě jdoucích řádků listu.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. Přidejte následující kód na `DisplayInExcel` konci upravit šířky sloupců, aby odpovídaly obsahu.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     Dřívější verze jazyka C# vyžadují explicitní `ExcelApp.Columns[1]` přetypování pro tyto `Object`operace, protože vrací , a `AutoFit` je metoda aplikace Excel. <xref:Microsoft.Office.Interop.Excel.Range> Následující řádky ukazují odlévání.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     C# 4 a novější verze `Object` převádí vrácené automaticky, `dynamic` pokud je sestavení odkazováno volbou kompilátoru [-link](../../language-reference/compiler-options/link-compiler-option.md) nebo ekvivalentním ekvivalentem, pokud je vlastnost Excel **Embed Interop Types** nastavena na hodnotu true. True je výchozí hodnota pro tuto vlastnost.

## <a name="to-run-the-project"></a>Spuštění projektu

1. Na konec položky `Main`přidejte následující řádek .

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. Stiskněte kombinaci kláves CTRL+F5.

     Zobrazí se list aplikace Excel, který obsahuje data z obou účtů.

## <a name="to-add-a-word-document"></a>Přidání wordové dokumentu

1. Chcete-li ilustrovat další způsoby, ve kterém C# 4 a novější verze, vylepšuje programování sady Office, následující kód otevře aplikaci Word a vytvoří ikonu, která odkazuje na list aplikace Excel.

     Vložit `CreateIconInWordDoc`metodu , která je k `Program` dispozici dále v tomto kroku, do třídy. `CreateIconInWordDoc`používá pojmenované a volitelné argumenty ke snížení složitosti volání metody <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> a <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. Tato volání obsahují dvě další nové funkce zavedené v C# 4, které zjednodušují volání metod COM, které mají referenční parametry. Nejprve můžete odeslat argumenty do referenčních parametrů, jako by se jednalo o parametry hodnoty. To znamená, že můžete odesílat hodnoty přímo, bez vytvoření proměnné pro každý referenční parametr. Kompilátor generuje dočasné proměnné pro uložení hodnot argumentů a zahodí proměnné při návratu z volání. Za druhé můžete vynechat `ref` klíčové slovo v seznamu argumentů.

     Metoda `Add` má čtyři referenční parametry, z nichž všechny jsou volitelné. V C# 4.0 a novější verze můžete vynechat argumenty pro některé nebo všechny parametry, pokud chcete použít jejich výchozí hodnoty. V C# 3.0 a starší verze argument musí být k dispozici pro každý parametr a argument musí být proměnná, protože parametry jsou referenční parametry.

     Metoda `PasteSpecial` vloží obsah schránky. Metoda má sedm referenčních parametrů, z nichž všechny jsou volitelné. Následující kód určuje argumenty pro dva `Link`z nich: , chcete-li vytvořit odkaz `DisplayAsIcon`na zdroj obsahu schránky a , zobrazit odkaz jako ikonu. V C# 4.0 a novější verze můžete použít pojmenované argumenty pro tyto dva a vynechat ostatní. Přestože se jedná o referenční parametry, `ref` není třeba použít klíčové slovo nebo vytvořit proměnné pro odeslání jako argumenty. Hodnoty můžete odeslat přímo. V C# 3.0 a staršíverze, musíte zadat argument proměnné pro každý referenční parametr.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     V jazyce C# 3.0 a staršíverze jazyka je vyžadován následující složitější kód.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. Na konec příkazu přidejte následující příkaz `Main`.

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. Na konec příkazu přidejte následující příkaz `DisplayInExcel`. Metoda `Copy` přidá list do schránky.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. Stiskněte kombinaci kláves CTRL+F5.

     Zobrazí se dokument aplikace Word, který obsahuje ikonu. Poklepáním na ikonu přenesete list do popředí.

## <a name="to-set-the-embed-interop-types-property"></a>Nastavení vlastnosti Vložit interop typy

1. Další vylepšení jsou možná při volání typu COM, který nevyžaduje primární sestavení interop (PIA) za běhu. Odebrání závislosti na PIA má za následek nezávislost verze a snadnější nasazení. Další informace o výhodách programování bez pia naleznete [v návodu: Vkládání typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).

     Programování je navíc jednodušší, protože typy, které jsou požadovány a vráceny metodami COM, mohou být reprezentovány pomocí typu `dynamic` namísto `Object`. Proměnné, které `dynamic` mají typ nejsou vyhodnoceny až do běhu, což eliminuje potřebu explicitní odlévání. Další informace naleznete [v tématu Použití dynamického typu](../types/using-type-dynamic.md).

     V C# 4 vkládání informací o typu namísto použití PIA je výchozí chování. Z důvodu tohoto výchozího nastavení jsou některé z předchozích příkladů zjednodušeny, protože explicitní přetypování není vyžadováno. Například prohlášení `worksheet` in `DisplayInExcel` je zapsán `Excel._Worksheet workSheet = excelApp.ActiveSheet` jako `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`spíše než . Volání `AutoFit` ve stejné metodě by také vyžadovalo explicitní `ExcelApp.Columns[1]` přetypování bez výchozího, protože vrátí metodu `Object`aplikace a `AutoFit` je metodou aplikace Excel. Následující kód ukazuje přetypování.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Chcete-li změnit výchozí nastavení a místo vkládání informací o typu použít pia, rozbalte uzel **Odkazy** v **Průzkumníku řešení** a vyberte **položku Microsoft.Office.Interop.Excel** nebo **Microsoft.Office.Interop.Word**.

3. Pokud okno **Vlastnosti** nevidíte, stiskněte **klávesu F4**.

4. V seznamu vlastností najdete **typy vložit interop** a změňte jeho hodnotu na **False**. Ekvivalentem můžete zkompilovat pomocí možnosti kompilátoru [-reference](../../language-reference/compiler-options/reference-compiler-option.md) namísto [-link](../../language-reference/compiler-options/link-compiler-option.md) na příkazovém řádku.

## <a name="to-add-additional-formatting-to-the-table"></a>Přidání dalšího formátování do tabulky

1. Nahraďte dvě `AutoFit` `DisplayInExcel` volání v následujícím příkazu.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     Metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> má sedm parametry hodnoty, z nichž všechny jsou volitelné. Pojmenované a volitelné argumenty umožňují poskytnout argumenty pro žádné, některé nebo všechny z nich. V předchozím příkazu je zadán argument pouze pro `Format`jeden z parametrů . Protože `Format` je první parametr v seznamu parametrů, není třeba zadat název parametru. Příkaz však může být srozumitelnější, pokud je zahrnut název parametru, jak je znázorněno v následujícím kódu.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Stisknutím kláves CTRL+F5 zobrazíte výsledek. Ostatní formáty jsou <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> uvedeny ve výčtu.

3. Porovnejte příkaz v kroku 1 s následujícím kódem, který zobrazuje argumenty, které jsou požadovány v C# 3.0 a starších verzích.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Příklad

Následující kód ukazuje úplný příklad.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Viz také

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [Dynamické](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Použití pojmenovaných a volitelných argumentů v programování sady Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
