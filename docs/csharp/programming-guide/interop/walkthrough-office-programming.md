---
title: 'Postupy: Programování pro Office (C# a Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 6c27442cb5c0c4172f503c945849e47560c2b33d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635350"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Postupy: Programování pro Office (C# a Visual Basic)

Visual Studio nabízí funkce v jazyce C# a Visual Basic, které zlepšují programování sady Microsoft Office. Užitečné funkce jazyka C# zahrnují pojmenované a `dynamic`volitelné argumenty a vrácené hodnoty typu . V programování com můžete vynechat `ref` klíčové slovo a získat přístup k indexované vlastnosti. Mezi funkce v jazyce Visual Basic patří automaticky implementované vlastnosti, příkazy ve výrazech lambda a inicializátory kolekce.

Oba jazyky umožňují vkládání informací o typu, což umožňuje nasazení sestavení, která interagují s komponentami modelu COM bez nasazení primárních mezioperačních sestavení (PIA) do počítače uživatele. Další informace naleznete [v tématu Návod: Vkládání typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).

Tento návod ukazuje tyto funkce v kontextu programování sady Office, ale mnoho z těchto funkcí jsou také užitečné v obecné programování. V návodu použijete aplikaci doplňku excelu k vytvoření excelového sešitu. Dále vytvoříte dokument aplikace Word, který obsahuje odkaz na sešit. Nakonec uvidíte, jak povolit a zakázat závislost PIA.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu je třeba mít v počítači nainstalovanou aplikaci Microsoft Office Excel a aplikaci Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Nastavení aplikace doplňku aplikace Excel

1. Spusťte Visual Studio.

2. V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.

3. V podokně **Nainstalované šablony** rozbalte **položku Visual Basic** nebo Visual **C#**, rozbalte **Office**a klikněte na rok verze produktu Office.

4. V podokně **Šablony** klikněte na **verzi aplikace Excel \<> doplňku**.

5. Podívejte se do horní části podokna **Šablony** a ujistěte se, že **rozhraní .NET Framework 4**nebo novější verze se zobrazí v poli **Cílová architektura.**

6. Pokud chcete, zadejte název projektu do pole **Název.**

7. Klikněte na tlačítko **OK**.

8. Nový projekt se zobrazí v **Průzkumníku řešení**.

### <a name="to-add-references"></a>Přidání odkazů

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a potom klikněte na **příkaz Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz.**

2. Na kartě Sestavení vyberte v seznamu Název **součásti** položku **Microsoft.Office.Interop.Excel**(klíč `<version>.0.0.0` k číslům verzí produktu Office naleznete v části Verze **společnosti** [Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)a podržte klávesu CTRL a vyberte položku **Microsoft.Office.Interop.Word**. `version <version>.0.0.0` Pokud sestavy nevidíte, bude pravděpodobně nutné zajistit jejich instalaci a zobrazení (viz [Postup: Instalace primárních sestavení meziop sady Office).](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)

3. Klikněte na tlačítko **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Přidání potřebných příkazů Imports nebo direktiv using

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor **ThisAddIn.vb** nebo **ThisAddIn.cs** a potom klepněte na příkaz **Zobrazit kód**.

2. Přidejte `Imports` následující příkazy (Visual Basic) nebo `using` direktivy (C#) na začátek souboru kódu, pokud již nejsou k dispozici.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Vytvoření seznamu bankovních účtů

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu , klikněte na **Přidat**a potom klikněte na **Třídu**. Pokud používáte jazyk Visual Basic nebo Account.cs, pojmenujte třídu Account.vb, pokud používáte jazyk C#. Klikněte na **Přidat**.

2. Nahraďte definici třídy `Account` následujícím kódem. Definice tříd y používají *automaticky implementované vlastnosti*. Další informace naleznete [v tématu Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Chcete-li `bankAccounts` vytvořit seznam obsahující dva účty, `ThisAddIn_Startup` přidejte následující kód k metodě v souboru *ThisAddIn.vb* nebo *ThisAddIn.cs*. Prohlášení seznamu použít *inicializátory kolekce*. Další informace naleznete v [tématu Inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Export dat do Excelu

1. Ve stejném souboru přidejte do `ThisAddIn` třídy následující metodu. Metoda nastaví sešit aplikace Excel a exportuje do něj data.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     V této metodě se používají dvě nové funkce jazyka C#. Obě tyto funkce již existují v jazyce Visual Basic.

    - Metoda [Přidat](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) má *volitelný parametr* pro určení konkrétní šablony. Volitelné parametry, nové v C# 4, umožňují vynechat argument pro tento parametr, pokud chcete použít výchozí hodnotu parametru. Protože v předchozím příkladu není `Add` odeslán žádný argument, použije výchozí šablonu a vytvoří nový sešit. Ekvivalentní příkaz v dřívějších verzích jazyka C# `excelApp.Workbooks.Add(Type.Missing)`vyžaduje zástupný argument: .

         Další informace naleznete [v tématu Pojmenované a volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md).

    - `Range` Vlastnosti `Offset` a [Range](<xref:Microsoft.Office.Interop.Excel.Range>) objektu použít *indexované vlastnosti* funkce. Tato funkce umožňuje využívat tyto vlastnosti z typů COM pomocí následující typické syntaxe jazyka C#. Indexované vlastnosti také umožňují `Value` používat `Range` vlastnost objektu, což eliminuje `Value2` potřebu používat vlastnost. Vlastnost `Value` je indexována, ale index je volitelný. Volitelné argumenty a indexované vlastnosti spolupracují v následujícím příkladu.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         V dřívějších verzích jazyka je vyžadována následující speciální syntaxe.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Vlastní indexované vlastnosti nelze vytvořit. Funkce podporuje pouze spotřebu existujících indexovaných vlastností.

         Další informace naleznete v tématu [Použití indexovaných vlastností v programování mezi opcemi com](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. Přidejte následující kód na `DisplayInExcel` konci upravit šířky sloupců, aby odpovídaly obsahu.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Tyto dodatky ukazují jinou funkci `Object` v c#: zacházení s hodnotami vrácenými z hostitelů COM, jako je například Office, jako by měli [typ dynamické](../../language-reference/builtin-types/reference-types.md). K tomu dochází automaticky, když je nastavení typů `True`vložit **interop** nastavena na výchozí hodnotu , nebo ekvivalentní, když je sestavení odkazováno možností kompilátoru [-link.](../../language-reference/compiler-options/link-compiler-option.md) Typ `dynamic` umožňuje pozdní vazbu, již k dispozici v jazyce Visual Basic a vyhýbá explicitní přetypování požadované v jazyce C# 3.0 a starší verze jazyka.

     Například `excelApp.Columns[1]` vrátí `Object`a `AutoFit` je metoda [rozsah](<xref:Microsoft.Office.Interop.Excel.Range>) aplikace Excel. Bez `dynamic`, je nutné přetypování objektu vráceného `excelApp.Columns[1]` jako instance `Range` před voláním metody `AutoFit`.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Další informace o vkládání typů interop naleznete v postupech "Chcete-li najít odkaz PIA" a "Chcete-li obnovit závislost PIA" dále v tomto tématu. Další informace `dynamic`o tématu , naleznete [v tématu dynamické](../../language-reference/builtin-types/reference-types.md) [nebo pomocí typu dynamické](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Vyvolání aplikace DisplayInExcel

1. Na konec `ThisAddIn_StartUp` metody přidejte následující kód. Volání `DisplayInExcel` obsahuje dva argumenty. První argument je název seznamu účtů, které mají být zpracovány. Druhý argument je multiřádkový lambda výraz, který definuje, jak mají být data zpracována. Hodnoty `ID` `balance` a pro každý účet jsou zobrazeny v sousedních buňkách a řádek je zobrazen červeně, pokud je zůstatek menší než nula. Další informace naleznete v tématu [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Chcete-li program spustit, stiskněte klávesu F5. Zobrazí se list aplikace Excel, který obsahuje data z účtů.

### <a name="to-add-a-word-document"></a>Přidání wordové dokumentu

1. Přidejte následující kód na `ThisAddIn_StartUp` konec metody a vytvořte dokument aplikace Word, který obsahuje odkaz na sešit aplikace Excel.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Tento kód ukazuje několik nových funkcí v jazyce C#: `ref` schopnost vynechat klíčové slovo v programování COM, pojmenované argumenty a volitelné argumenty. Tyto funkce již existují v jazyce Visual Basic. Metoda [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) má sedm parametrů, které jsou definovány jako volitelné referenční parametry. Pojmenované a volitelné argumenty umožňují určit parametry, ke kterým chcete získat přístup podle názvu, a odesílat argumenty pouze těmto parametrům. V tomto příkladu jsou odeslány argumenty označující, že by měl být `Link`vytvořen odkaz na sešit ve schránce (parametr) `DisplayAsIcon`a že odkaz má být zobrazen v dokumentu aplikace Word jako ikona (parametr ). Visual C# také umožňuje vynechat `ref` klíčové slovo pro tyto argumenty.

### <a name="to-run-the-application"></a>Spuštění aplikace

1. Stisknutím klávesy F5 spusťte aplikaci. Aplikace Excel spustí a zobrazí tabulku obsahující informace `bankAccounts`ze dvou účtů v aplikaci . Pak se zobrazí dokument aplikace Word, který obsahuje odkaz na tabulku aplikace Excel.

### <a name="to-clean-up-the-completed-project"></a>Vyčištění dokončeného projektu

1. V sadě Visual Studio klikněte v nabídce **Sestavení** na **tlačítko Vyčistit řešení.** V opačném případě bude doplněk spuštěn při každém spuštění aplikace Excel v počítači.

### <a name="to-find-the-pia-reference"></a>Vyhledání odkazu PIA

1. Spusťte aplikaci znovu, ale neklepněte na tlačítko **Vyčistit řešení**.

2. Vyberte **možnost Start**. Vyhledejte **>\<verzi sady Microsoft Visual Studio** a otevřete příkazový řádek pro vývojáře.

3. Zadejte `ildasm` příkazový řádek pro vývojáře pro visual studio a stiskněte klávesu ENTER. Zobrazí se okno IL DASM.

4. V nabídce **Soubor** v okně IL DASM vyberte **Soubor** > **otevřít**. Poklikejte na **verzi sady Visual \<Studio>** a potom poklepejte na **položku Projekty**. Otevřete složku projektu a ve složce bin/Debug *vyhledejte název dll projektu.* Poklepejte na *název projektu*.dll. Nové okno zobrazuje atributy projektu, kromě odkazů na jiné moduly a sestavení. Všimněte si, že obory názvů `Microsoft.Office.Interop.Excel` a `Microsoft.Office.Interop.Word` jsou zahrnuty v sestavení. Ve výchozím nastavení v sadě Visual Studio kompilátor importuje typy, které potřebujete z odkazované PIA do vašeho sestavení.

     Další informace naleznete v [tématu How to: View Assembly Contents](../../../standard/assembly/view-contents.md).

5. Poklepejte na ikonu **MANIFEST.** Zobrazí se okno obsahující seznam sestavení, která obsahují položky, na které projekt odkazuje. `Microsoft.Office.Interop.Excel`a `Microsoft.Office.Interop.Word` nejsou zahrnuty v seznamu. Vzhledem k tomu, že typy, které projekt potřebuje byly importovány do sestavení, odkazy na PIA nejsou vyžadovány. To usnadňuje nasazení. Pia nemusí být přítomny v počítači uživatele a protože aplikace nevyžaduje nasazení konkrétní verze PIA, aplikace mohou být navrženy pro práci s více verzemi sady Office za předpokladu, že ve všech verzích existují potřebná rozhraní API .

     Vzhledem k tomu, že nasazení PIA již není nutné, můžete vytvořit aplikaci v pokročilých scénářích, která pracuje s více verzemi sady Office, včetně starších verzí. To však funguje pouze v případě, že váš kód nepoužívá žádná rozhraní API, která nejsou k dispozici ve verzi sady Office, se kterou pracujete. Není vždy jasné, zda konkrétní rozhraní API bylo k dispozici v dřívější verzi, a z tohoto důvodu se nedoporučuje pracovat s dřívějšími verzemi sady Office.

    > [!NOTE]
    > Před office 2003 úřad PIA nezveřejnil. Proto jediný způsob, jak generovat sestavení interop pro office 2002 nebo starší verze je importem odkazu COM.

6. Zavřete okno manifestu a okno sestavení.

### <a name="to-restore-the-pia-dependency"></a>Obnovení závislosti PIA

1. V **Průzkumníku řešení**klepněte na tlačítko **Zobrazit všechny soubory.** Rozbalte složku **Odkazy** a vyberte **microsoft.office.interop.excel**. Stisknutím klávesy F4 zobrazte okno **Vlastnosti.**

2. V okně **Vlastnosti** změňte vlastnost **Embed Interop Types** z **True** na **False**.

3. Opakujte kroky 1 a `Microsoft.Office.Interop.Word`2 v tomto postupu pro .

4. V C# zakomentujte `Autofit` dvě volání na `DisplayInExcel` konci metody.

5. Stisknutím klávesy F5 ověřte, zda projekt stále běží správně.

6. Opakujte kroky 1-3 z předchozího postupu a otevřete okno sestavy. Všimněte `Microsoft.Office.Interop.Word` `Microsoft.Office.Interop.Excel` si, že a již nejsou v seznamu vložených sestavení.

7. Poklepejte na ikonu **MANIFEST** a procházejte seznamem odkazovaných sestavení. Oba `Microsoft.Office.Interop.Word` `Microsoft.Office.Interop.Excel` a jsou v seznamu. Vzhledem k tomu, že aplikace odkazuje na excel ové a wordové PIA a vlastnost **Embed Interop Types** je nastavena na **hodnotu False**, musí existovat obě sestavení v počítači koncového uživatele.

8. V sadě Visual Studio klepněte na tlačítko **Vyčistit řešení** v nabídce **Sestavení** a vyčistěte dokončený projekt.

## <a name="see-also"></a>Viz také

- [Automaticky implementované vlastnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Automaticky implementované vlastnosti (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)
- [Volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Dynamické](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Lambda – výrazy (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Lambda výrazy (C#)](../statements-expressions-operators/lambda-expressions.md)
- [Jak použít indexované vlastnosti při programování interoperability COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md)
- [Návod: Vytvoření prvního doplňku VSTO pro Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [KOM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Vzájemná funkční spolupráce](./index.md)
