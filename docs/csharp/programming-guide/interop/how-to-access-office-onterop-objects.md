---
title: Přístup k objektům Interop Office – Průvodce programováním v C#
description: Přečtěte si o funkcích jazyka C#, které zjednodušují přístup k objektům rozhraní API Office. Pomocí nových funkcí můžete napsat kód, který vytvoří a zobrazí excelový list.
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: bc4b5755bf56a013a0deb4efdb821df18db5a18e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303020"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Přístup k objektům Interop Office (Průvodce programováním v C#)

Jazyk C# obsahuje funkce, které zjednodušují přístup k objektům rozhraní API systému Office. Nové funkce zahrnují pojmenované a nepovinné argumenty, nový typ s názvem `dynamic` a možnost předat argumenty odkazovým parametrům v metodách modelu COM, jako kdyby byly parametry hodnoty.

V tomto tématu použijete nové funkce k psaní kódu, který vytvoří a zobrazí systém Microsoft Office excelový list. Potom napíšete kód pro přidání dokumentu aplikace Office Word, který obsahuje ikonu, která je propojena s listem aplikace Excel.

K dokončení tohoto Názorného postupu musíte mít v počítači nainstalovanou systém Microsoft Office Excel 2007 a systém Microsoft Office Word 2007 nebo novější verze.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Vytvoření nové konzolové aplikace

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**. Zobrazí se dialogové okno **Nový projekt**.

3. V podokně **Nainstalované šablony** rozbalte položku **Visual C#** a potom klikněte na možnost **Windows**.

4. Podívejte se v horní části dialogového okna **Nový projekt** , abyste se ujistili, že je jako cílová architektura vybraná **.NET Framework 4** (nebo novější verze).

5. V podokně **šablony** klikněte na **Konzolová aplikace**.

6. Do pole **název** zadejte název projektu.

7. Klikněte na **OK**.

     Nový projekt se zobrazí v **Průzkumník řešení**.

## <a name="to-add-references"></a>Přidání odkazů

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz** .

2. Na stránce **sestavení** vyberte v seznamu **název součásti** možnost **Microsoft. Office. Interop. Word** a pak stiskněte klávesu CTRL a vyberte **Microsoft. Office. Interop. Excel**.  Pokud nevidíte sestavení, možná budete muset zajistit, aby byly nainstalované a zobrazené. Viz [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. Klikněte na **OK**.

## <a name="to-add-necessary-using-directives"></a>Přidání nezbytných direktiv using

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *program.cs* a pak klikněte na **Zobrazit kód**.

2. `using`Do horní části souboru kódu přidejte následující direktivy:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Vytvoření seznamu bankovních účtů

1. Vložte následující definici třídy do **program.cs**v rámci `Program` třídy.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. Přidejte následující kód do `Main` metody k vytvoření `bankAccounts` seznamu, který obsahuje dva účty.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Deklarace metody, která exportuje informace o účtu do Excelu

1. Přidejte následující metodu do `Program` třídy pro nastavení listu aplikace Excel.

     Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> má volitelný parametr pro určení konkrétní šablony. Volitelné parametry, novinka v C# 4, umožňují vynechat argument pro tento parametr, pokud chcete použít výchozí hodnotu parametru. Vzhledem k tomu, že žádný argument není odesílán v následujícím kódu, `Add` používá výchozí šablonu a vytvoří nový sešit. Ekvivalent příkazu v dřívějších verzích jazyka C# vyžaduje zástupný argument: `ExcelApp.Workbooks.Add(Type.Missing)` .

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. Přidejte následující kód na konec `DisplayInExcel` . Kód vloží hodnoty do prvních dvou sloupců prvního řádku listu.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. Přidejte následující kód na konec `DisplayInExcel` . `foreach`Smyčka vloží informace ze seznamu účtů do prvního dvou sloupců po sobě jdoucích řádků listu.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. Přidejte následující kód na konec `DisplayInExcel` a upravte šířku sloupce tak, aby odpovídaly obsahu.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     Starší verze jazyka C# vyžadují explicitní přetypování pro tyto operace `ExcelApp.Columns[1]` , protože vrací `Object` a `AutoFit` je metoda aplikace Excel <xref:Microsoft.Office.Interop.Excel.Range> . Následující řádky ukazují přetypování.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     V C# 4 a novějších verzích převede vrácené hodnoty `Object` na `dynamic` automaticky, pokud je sestavení odkazováno pomocí možnosti kompilátoru [-Link](../../language-reference/compiler-options/link-compiler-option.md) nebo obdobně, pokud je vlastnost Excel **Embed Interop Types** nastavená na true. Hodnota true je výchozí hodnota pro tuto vlastnost.

## <a name="to-run-the-project"></a>Spuštění projektu

1. Přidejte následující řádek na konci `Main` .

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. Stiskněte klávesy CTRL + F5.

     Zobrazí se excelový list obsahující data ze dvou účtů.

## <a name="to-add-a-word-document"></a>Přidání dokumentu aplikace Word

1. Pro ilustraci dalších způsobů, jak C# 4 a novější verze vylepšuje programování v Office, následující kód otevře aplikaci Word a vytvoří ikonu, která odkazuje na excelový list.

     Metoda vložení `CreateIconInWordDoc` , která je v tomto kroku k dispozici, do `Program` třídy. `CreateIconInWordDoc`používá pojmenované a volitelné argumenty ke snížení složitosti volání metody do <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> a <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A> . Tato volání zahrnují dvě další nové funkce, které byly zavedeny v C# 4, které zjednodušují volání metod modelu COM, které mají referenční parametry. Nejprve můžete odeslat argumenty parametrům reference, jako by to byly parametry hodnoty. To znamená, že můžete odesílat hodnoty přímo, bez vytváření proměnné pro každý parametr odkazu. Kompilátor generuje dočasné proměnné pro uchovávání hodnot argumentů a zahodí proměnné při návratu ze volání. Za druhé můžete `ref` klíčové slovo vynechat v seznamu argumentů.

     `Add`Metoda má čtyři referenční parametry, z nichž všechny jsou volitelné. V C# 4,0 a novějších verzích můžete vynechat argumenty pro všechny nebo všechny parametry, pokud chcete použít výchozí hodnoty. V jazyce C# 3,0 a starších verzích musí být k dispozici argument pro každý parametr a argument musí být proměnná, protože parametry jsou referenční parametry.

     `PasteSpecial`Metoda vloží obsah schránky. Metoda má sedm referenčních parametrů, z nichž všechny jsou volitelné. Následující kód Určuje argumenty pro dva z nich: `Link` , chcete-li vytvořit odkaz na zdroj obsahu schránky a `DisplayAsIcon` Zobrazit odkaz jako ikonu. V C# 4,0 a novějších verzích můžete použít pojmenované argumenty pro tyto dva a vynechat ostatní. I když se jedná o parametry odkazu, nemusíte používat `ref` klíčové slovo nebo k vytvoření proměnných pro odeslání jako argumenty. Hodnoty můžete přímo odeslat. V jazyce C# 3,0 a starších verzích je nutné dodat argument proměnné pro každý parametr odkazu.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     V jazyce C# 3,0 a starších verzích jazyka je vyžadován následující složitější kód.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. Přidejte následující příkaz na konci `Main` .

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. Přidejte následující příkaz na konci `DisplayInExcel` . `Copy`Metoda přidá list do schránky.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. Stiskněte klávesy CTRL + F5.

     Zobrazí se dokument aplikace Word obsahující ikonu. Dvojitým kliknutím na ikonu přeneste list do popředí.

## <a name="to-set-the-embed-interop-types-property"></a>Nastavení vlastnosti Embed Interop Types

1. Další vylepšení jsou možná při volání typu modelu COM, který nevyžaduje primární definiční sestavení (PIA) v době běhu. Výsledkem odebrání závislosti na PIA je nezávislost verzí a snazší nasazení. Další informace o výhodách programování bez PIA naleznete v tématu [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).

     Kromě toho programování je snazší, protože typy, které jsou požadovány a vraceny metodou COM, lze reprezentovat pomocí typu `dynamic` namísto `Object` . Proměnné, které mají typ `dynamic` , nejsou vyhodnocovány až do doby běhu, což eliminuje nutnost explicitního přetypování. Další informace naleznete v tématu [použití typu Dynamic](../types/using-type-dynamic.md).

     V C# 4 je jako výchozí chování použito vkládání informací o typu namísto použití PIA. Z důvodu tohoto výchozího nastavení je několik z předchozích příkladů zjednodušeno, protože explicitní přetypování není vyžadováno. Například deklarace `worksheet` v `DisplayInExcel` je zapsána jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` spíše než `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet` . Volání `AutoFit` ve stejné metodě by také vyžadovala explicitní přetypování bez výchozí hodnoty, protože `ExcelApp.Columns[1]` vrací `Object` a `AutoFit` je metoda aplikace Excel. Následující kód ukazuje přetypování.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Chcete-li změnit výchozí nastavení a použít PIA namísto vložení informací o typu, rozbalte uzel **odkazy** v **Průzkumník řešení** a pak vyberte **Microsoft. Office. Interop. Excel** nebo **Microsoft. Office. Interop. Word**.

3. Pokud se okno **vlastnosti** nezobrazí, stiskněte **F4**.

4. Vyhledejte **typy spolupráce pro vložení** v seznamu vlastností a změňte její hodnotu na **false**. Ekvivalentně můžete kompilovat pomocí možnosti kompilátoru [-reference](../../language-reference/compiler-options/reference-compiler-option.md) namísto [odkazu](../../language-reference/compiler-options/link-compiler-option.md) na příkazovém řádku.

## <a name="to-add-additional-formatting-to-the-table"></a>Přidání dalšího formátování do tabulky

1. Nahraďte dvě volání do `AutoFit` v `DisplayInExcel` pomocí následujícího příkazu.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A>Metoda má sedm parametrů hodnot, z nichž všechny jsou volitelné. Pojmenované a volitelné argumenty umožňují zadat argumenty pro žádné, některé nebo všechny. V předchozím příkazu je argument zadán pouze pro jeden z parametrů, `Format` . Protože `Format` je prvním parametrem v seznamu parametrů, nemusíte zadávat název parametru. Příkaz však může být snazší pochopit, zda je název parametru zahrnut, jak je uvedeno v následujícím kódu.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Výsledek zobrazíte stisknutím kombinace kláves CTRL + F5. Další formáty jsou uvedeny ve <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> výčtu.

3. Porovnejte příkaz v kroku 1 s následujícím kódem, který ukazuje argumenty vyžadované v C# 3,0 a starších verzích.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Příklad

Následující kód ukazuje kompletní příklad.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Viz také:

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamické](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Jak použít pojmenované a nepovinné argumenty v programování pro sadu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
