---
title: 'Průvodce: Programování pro Office (C# a Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 76d48b588db17a712ac698b604828520e38776a9
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223153"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Průvodce: Programování pro Office (C# a Visual Basic)
Visual Studio nabízí funkce v jazyce C# a Visual Basic, které zlepšují programování pro sadu Microsoft Office. Užitečné funkce jazyka C# zahrnout pojmenované a nepovinné argumenty a návratové hodnoty typu `dynamic`. Programování v modelu COM, můžete vynechat `ref` – klíčové slovo a získat přístup k indexované vlastnosti. Funkce v jazyce Visual Basic zahrnují automaticky implementované vlastnosti příkazy ve výrazech lambda a inicializátory kolekce.

Oba jazyky umožňují vkládání informací o typu, který umožňuje nasazení sestavení, které komunikují s komponentami modelu COM bez nasazení primárních sestavení vzájemné spolupráce (PIA) na počítači uživatele. Další informace najdete v tématu [názorný postup: Vložení typů ze spravovaných sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
Tento názorný postup ukazuje tyto funkce v rámci programování pro Office, ale mnohé z těchto funkcí jsou také užitečné, obecně programování. V tomto návodu použijete k vytvoření Excelového sešitu aplikace Excel Add-in. V dalším kroku vytvořte Wordový dokument, který obsahuje odkaz na sešit. A konečně naleznete v tématu Jak povolit a zakázat závislost PIA.  
  
## <a name="prerequisites"></a>Požadavky  

Musíte mít aplikaci Microsoft Office Excel a Microsoft Office Word nainstalována v počítači k dokončení tohoto návodu.  
  
 Pokud používáte operační systém, který je starší než [!INCLUDE[windowsver](~/includes/windowsver-md.md)], ujistěte se, že [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] je nainstalována.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>Chcete-li nastavit aplikaci Excel Add-in  
  
1.  Spusťte Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V **nainstalované šablony** podokně rozbalte **jazyka Visual Basic** nebo **Visual C#**, rozbalte **Office**a potom klikněte na verzi rok Produktu Office.  
  
4.  V **šablony** podokně klikněte na tlačítko **Excel \<verze > Add-in**.  
  
5.  Hledat v horní části **šablony** podokno a ujistěte se, že **rozhraní .NET Framework 4**, nebo novější verze, zobrazí se v **Cílová architektura** pole.  
  
6.  Zadejte název pro váš projekt v **název** pole, pokud chcete.  
  
7.  Klikněte na **OK**.  
  
8.  Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
### <a name="to-add-references"></a>Přidání odkazů  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz**. **Přidat odkaz** zobrazí se dialogové okno.  
  
2.  Na **sestavení** kartu, vyberte možnost **Microsoft.Office.Interop.Excel**, verze `<version>.0.0.0` (klávesy čísla verze produktů Office, naleznete v tématu [Versions Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)) v **název komponenty** seznamu a pak podržte klávesu CTRL, klíče a vyberte **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Pokud nevidíte sestavení, budete muset zajistit, jsou nainstalované a zobrazí (viz [jak: Instalace primárních sestavení vzájemné spolupráce Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).  
  
3.  Klikněte na **OK**.  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Přidání potřebných příkazů Imports nebo direktiv using  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ThisAddIn.vb** nebo **ThisAddIn.cs** souboru a pak klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující `Imports` příkazy (Visual Basic) nebo `using` direktivy (C#) na začátek souboru kódu, pokud již nejsou k dispozici.  
  
     [!code-csharp[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]

     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]
  
### <a name="to-create-a-list-of-bank-accounts"></a>Chcete-li vytvořit seznam účtů bank  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vašeho projektu, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **třídy**. Název třídy Account.vb, pokud používáte Visual Basic nebo Account.cs Pokud používáte C#. Klikněte na **Přidat**.  
  
2.  Nahraďte definici `Account` třídy následujícím kódem. Definice tříd pomocí *automaticky implementované vlastnosti*. Další informace najdete v tématu [implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-csharp[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]

     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  Chcete-li vytvořit `bankAccounts` seznam, který obsahuje dva účty, přidejte následující kód, který `ThisAddIn_Startup` metoda ve *ThisAddIn.vb* nebo *ThisAddIn.cs*. Pomocí seznamu deklarace *inicializátory kolekce*. Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-csharp[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]

     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>Export dat do Excelu  
  
1.  Ve stejném souboru přidejte následující metodu do `ThisAddIn` třídy. Metoda nastavuje Excelový sešit a exportuje data do ní.  
  
     [!code-csharp[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]

     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     V této metodě se používají dvě nové funkce C#. Obě tyto funkce již existují v jazyce Visual Basic.  
  
    -   Metoda [přidat](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) má *volitelný parametr* pro určení konkrétní šablonu. Volitelné parametry, které jsou nové v [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], vám umožní argument pro tento parametr vynechat, pokud chcete použít výchozí hodnotu parametru. Vzhledem k tomu, že v předchozím příkladu je odeslán žádný argument `Add` používá výchozí šablonu a vytvoří nový sešit. Ekvivalentní příkaz ve starších verzích jazyka C# vyžaduje argument zástupný symbol: `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Další informace najdete v tématu [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   `Range` a `Offset` vlastnosti [rozsah](<xref:Microsoft.Office.Interop.Excel.Range>) používají *indexovaných vlastností* funkce. Tato funkce umožňuje, abyste mohli využívat tyto vlastnosti z typů modelu COM s použitím typické C# syntaxi. Indexované vlastnosti také umožňují používat `Value` vlastnost `Range` objektu, takže odpadá nutnost používat `Value2` vlastnost. `Value` Indexované vlastnosti, ale index je volitelné. Volitelné argumenty a indexované vlastnosti společně v následujícím příkladu.  
  
         [!code-csharp[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         V předchozích verzích tohoto jazyka se vyžaduje následující speciální syntaxi.  
  
         [!code-csharp[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         Nelze vytvořit indexované vlastnosti. Tato funkce podporuje pouze využití stávající indexované vlastnosti.  
  
         Další informace najdete v tématu [jak: Použití indexovaných vlastností při programování v modelu COM Interop](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  Přidejte následující kód na konci `DisplayInExcel` upravit šířku sloupců podle obsahu.  
  
     [!code-csharp[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]

     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     Tyto doplňky ukazují další funkce v jazyce C#: považuje `Object` jako v případě, že mají typ vrácené hodnoty z hostitelů modelu COM, jako je například Office [dynamické](../../../csharp/language-reference/keywords/dynamic.md). K tomu dojde automaticky při **Embed Interop Types** je nastavena na výchozí hodnotu, `True`, nebo ekvivalentně, když sestavení odkazuje [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) – možnost kompilátoru. Typ `dynamic` umožňuje pozdní vazby již k dispozici v jazyce Visual Basic a zabraňuje explicitní přetypování nutné Visual C# 2008 a starší verze jazyka.  
  
     Například `excelApp.Columns[1]` vrátí `Object`, a `AutoFit` je aplikace Excel [rozsah](<xref:Microsoft.Office.Interop.Excel.Range>) metody. Bez `dynamic`, musíte přetypovat vrácený objekt `excelApp.Columns[1]` jako instance `Range` před voláním metody `AutoFit`.  
  
     [!code-csharp[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     Další informace o vkládání typů spolupráce naleznete v tématu postupy "najít odkazy PIA" a "obnovit závislost PIA" dále v tomto tématu. Další informace o `dynamic`, naleznete v tématu [dynamické](../../../csharp/language-reference/keywords/dynamic.md) nebo [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### <a name="to-invoke-displayinexcel"></a>K vyvolání DisplayInExcel  
  
1.  Přidejte následující kód na konci `ThisAddIn_StartUp` metody. Volání `DisplayInExcel` obsahuje dva argumenty. Prvním argumentem je název seznamu účtů na zpracování. Druhý argument je víceřádkového výrazu lambda výraz, který definuje, jak se data mají být zpracovány. `ID` a `balance` sousedících buněk se zobrazují hodnoty pro každý účet, a řádek je zobrazen červeně, pokud zůstatek na účtu je menší než nula. Další informace najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-csharp[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]

     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  Chcete-li spustit program, stiskněte klávesu F5. Zobrazí se Excelového listu, který obsahuje data z účtů.  
  
### <a name="to-add-a-word-document"></a>Chcete-li přidat dokument aplikace Word  
  
1.  Přidejte následující kód na konci `ThisAddIn_StartUp` metodu pro vytvoření dokumentu aplikace Word, který obsahuje odkaz na Excelový sešit.  
  
     [!code-csharp[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]

     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     Tento kód ukazuje několik nových funkcí v jazyce C#: možnost chcete vynechat, nechte `ref` – klíčové slovo v programování v modelu COM, pojmenované argumenty a nepovinné argumenty. Tyto funkce se již existují v jazyce Visual Basic. [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) metoda má sedm parametry, které jsou definovány jako s volitelnými parametry. Pojmenované a nepovinné argumenty umožňují označit parametry, které chcete získat přístup podle názvu a argumenty odesílat jenom tyto parametry. V tomto příkladu jsou argumenty odesílat udávající, že by měl být vytvářeny odkaz k sešitu do schránky (parametr `Link`) a že je odkaz zobrazený v dokumentu jako ikona (parametr `DisplayAsIcon`). Visual C# také umožňuje vynechat, nechte `ref` – klíčové slovo pro tyto argumenty.
  
### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
1.  Stisknutím klávesy F5 spusťte aplikaci. Excel spustí a zobrazí tabulku s informacemi z dva účty v `bankAccounts`. Pak se zobrazí Wordový dokument, který obsahuje odkaz na tabulku aplikace Excel.  
  
### <a name="to-clean-up-the-completed-project"></a>Vyčistit dokončený projekt  
  
1.  V sadě Visual Studio, klikněte na tlačítko **Vyčistit řešení** na **sestavení** nabídky. V opačném případě doplněk se spustí při každém otevření aplikace Excel na vašem počítači.  
  
### <a name="to-find-the-pia-reference"></a>PIA odkaz  
  
1.  Spusťte aplikaci znovu spustit, ale neklikejte na **Vyčistit řešení**.  
  
2.  Vyberte **Start**. Vyhledejte **sady Microsoft Visual Studio \<verze >** a otevřete příkazový řádek pro vývojáře.  
  
3.  Typ `ildasm` v příkazový řádek vývojáře pro Visual Studio okno a potom stiskněte klávesu ENTER. Zobrazí se okno IL DASM.  
  
4.  Na **souboru** nabídky v okně IL DASM vyberte **souboru** > **otevřít**. Dvakrát klikněte na panel **sady Visual Studio \<verze >** a potom dvakrát klikněte na panel **projekty**. Otevřete složku pro váš projekt a podívejte se do složky bin/Debug *název vašeho projektu*.dll. Dvakrát klikněte na panel *název vašeho projektu*.dll. Nové okno zobrazuje atributy váš projekt, kromě odkazy na jiných modulů a sestavení. Všimněte si, že obory názvů `Microsoft.Office.Interop.Excel` a `Microsoft.Office.Interop.Word` jsou součástí sestavení. Ve výchozím nastavení v sadě Visual Studio kompilátor importuje typy, které potřebujete z odkazované PIA do vašeho sestavení.  
  
     Další informace najdete v tématu [jak: Zobrazení obsahu sestavení](../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
5.  Dvakrát klikněte **MANIFEST** ikonu. Zobrazí se okno obsahující seznam sestavení, které obsahují položky, které jsou odkazované projektem. `Microsoft.Office.Interop.Excel` a `Microsoft.Office.Interop.Word` nejsou zahrnuty v seznamu. Vzhledem k tomu, že typy, které projekt potřebuje se naimportovaly do vašeho sestavení, odkazy na PIA nejsou povinné. To usnadňuje nasazení. PIA nemusí být k dispozici v počítači uživatele, a protože aplikace nevyžaduje, aby nasazení na konkrétní verzi nástroje PIA, aplikace může být navržené pro práci s více verzemi systému Office, za předpokladu, že nezbytné rozhraní API existují ve všech verzích .  
  
     Protože nasazení PIA, již není nezbytné, můžete vytvořit aplikaci v pokročilých scénářích, které pracuje s více verzemi systému Office, včetně starších verzí. To ale funguje pouze v případě, že váš kód nepoužívá žádná rozhraní API, které nejsou k dispozici ve verzi Office, že pracujete s. Není vždy jasné, jestli byl k dispozici ve starší verzi a pro, že práce s předchozími verzemi sady Office z důvodu se nedoporučuje dané rozhraní API.  
  
    > [!NOTE]
    > Office nepublikoval PIA před Office 2003. Proto je jediný způsob, jak generování sestavení vzájemné spolupráce pro systém Office 2002 a předchozími verzemi importováním odkaz modelu COM.  
  
6.  Zavření okna manifestu a sestavení.  
  
### <a name="to-restore-the-pia-dependency"></a>Chcete-li obnovit PIA závislostí  
  
1.  V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko. Rozbalte **odkazy** a pak zvolte položku **Microsoft.Office.Interop.Excel**. Zobrazíte stisknutím klávesy F4 **vlastnosti** okna.  
  
2.  V **vlastnosti** okno Změnit **Embed Interop Types** vlastnost z **True** k **False**.  
  
3.  Opakujte kroky 1 a 2 v tomto postupu pro `Microsoft.Office.Interop.Word`.  
  
4.  V jazyce C#, okomentujte dvě volání na `Autofit` na konci `DisplayInExcel` metody.  
  
5.  Stiskněte klávesu F5, chcete-li ověřit, že projekt stále běží správně.  
  
6.  Opakujte kroky 1 až 3 z předchozího postupu otevřete okno sestavení. Všimněte si, že `Microsoft.Office.Interop.Word` a `Microsoft.Office.Interop.Excel` už nejsou v seznamu vložené sestavení.  
  
7.  Dvakrát klikněte **MANIFEST** ikonu a projděte si seznam odkazovaných sestavení. Obě `Microsoft.Office.Interop.Word` a `Microsoft.Office.Interop.Excel` jsou v seznamu. Protože aplikace Excel a Word PIA, odkazuje na aplikaci a **Embed Interop Types** je nastavena na **False**, obě sestavení musí být v počítači koncového uživatele.  
  
8.  V sadě Visual Studio, klikněte na tlačítko **Vyčistit řešení** na **sestavení** nabídky k vyčištění dokončený projekt.  
  
## <a name="see-also"></a>Viz také

- [Automaticky implementované vlastnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
- [Automaticky implementované vlastnosti (C#)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
- [Předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)  
- [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Výrazy lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
- [Výrazy lambda (C#)](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Postupy: Použití indexovaných vlastností při programování vzájemné spolupráce COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
- [Návod: Vložení informací o typu ze sestavení sady Microsoft Office](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)  
- [Návod: Vložení typů ze spravovaných sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)  
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
- [Interoperabilita](../../../csharp/programming-guide/interop/index.md)
