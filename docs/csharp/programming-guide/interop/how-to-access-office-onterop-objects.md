---
title: 'Postupy: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: d646a73cc8616821372c5a0078b595291829ac27
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970182"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C# (Průvodce programováním v C#)
Visual C# obsahuje funkce, které usnadňují přístup k objektům rozhraní API Office. Nové funkce patří pojmenované a nepovinné argumenty, nový typ s názvem `dynamic`a možnost předání argumentů do parametrů odkazu v metodách modelu COM, jako by byly parametry s hodnotou.  
  
 V tomto tématu použijete nové funkce napsat kód, který vytvoří a zobrazí list aplikace Microsoft Office Excel. Potom napíšete kód pro přidání dokumentu Office Word, který obsahuje ikonu, která je propojený Excelový list.  
  
 K dokončení tohoto návodu, musíte mít aplikaci Microsoft Office Excel 2007 a Microsoft Office Word 2007 nebo novější verze, v počítači nainstalována.  
  
 Pokud používáte operační systém, který je starší než [!INCLUDE[windowsver](~/includes/windowsver-md.md)], ujistěte se, že [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] je nainstalována.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-new-console-application"></a>Vytvořte novou konzolovou aplikaci  
  
1.  Spusťte Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**. Zobrazí se dialogové okno **Nový projekt**.  
  
3.  V **nainstalované šablony** podokně rozbalte **Visual C#** a potom klikněte na tlačítko **Windows**.  
  
4.  Hledat v horní části **nový projekt** dialogové okno že **rozhraní .NET Framework 4** (nebo novější verzi) je vybraná jako Cílová architektura.  
  
5.  V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.  
  
6.  Zadejte název pro váš projekt v **název** pole.  
  
7.  Klikněte na **OK**.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
## <a name="to-add-references"></a>Přidání odkazů  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz**. **Přidat odkaz** zobrazí se dialogové okno.  
  
2.  Na **sestavení** stránce **Microsoft.Office.Interop.Word** v **název komponenty** seznamu a pak podržte klávesu CTRL, klíče a vyberte  **Microsoft.Office.Interop.Excel**.  Pokud nevidíte sestavení, budete muset zajistit, jsou nainstalované a zobrazí (viz [jak: Instalace primárních sestavení vzájemné spolupráce Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))  
  
3.  Klikněte na **OK**.  
  
## <a name="to-add-necessary-using-directives"></a>Chcete-li přidat nezbytné direktivy using  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující `using` direktivy do horní části souboru kódu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]  
  
## <a name="to-create-a-list-of-bank-accounts"></a>Chcete-li vytvořit seznam účtů bank  
  
1.  Vložte následující definice třídy do **Program.cs**v části `Program` třídy.  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]  
  
2.  Přidejte následující kód, který `Main` metodu pro vytvoření `bankAccounts` seznam, který obsahuje dva účty.  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]  
  
## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Chcete-li deklarovat metodu, která se exportuje informace o účtu do Excelu  
  
1.  Přidejte následující metodu do `Program` třídy nastavit Excelového listu.  
  
     Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> je volitelný parametr určující konkrétní šablonu. Volitelné parametry, které jsou nové v [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], vám umožní argument pro tento parametr vynechat, pokud chcete použít výchozí hodnotu parametru. Protože je v následujícím kódu žádný argument `Add` používá výchozí šablonu a vytvoří nový sešit. Ekvivalentní příkaz ve starších verzích jazyka C# vyžaduje argument zástupný symbol: `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]  
  
2.  Přidejte následující kód na konci `DisplayInExcel`. Kód vloží hodnoty do prvních dvou sloupcích prvního řádku listu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]  
  
3.  Přidejte následující kód na konci `DisplayInExcel`. `foreach` Smyčky vloží informace ze seznamu účtů do prvních dvou sloupců po sobě jdoucích řádků z listu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]  
  
4.  Přidejte následující kód na konci `DisplayInExcel` upravit šířku sloupců podle obsahu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]  
  
     Starší verze jazyka C# vyžaduje explicitní přetypování pro tyto operace protože `ExcelApp.Columns[1]` vrátí `Object`, a `AutoFit` je aplikace Excel <xref:Microsoft.Office.Interop.Excel.Range> metody. Následující řádky zobrazují přetypování.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
     [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]a novějších verzích, převede vrácený `Object` k `dynamic` automaticky, pokud je sestavení odkazuje [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) – možnost kompilátoru nebo ekvivalentně, pokud v aplikaci Excel **Embed Interop Types**je nastavena na hodnotu true. Hodnota TRUE je výchozí hodnota této vlastnosti.  
  
## <a name="to-run-the-project"></a>Spustit projekt  
  
1.  Přidejte následující řádek na konci `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]  
  
2.  Stisknutím kláves CTRL + F5.  
  
     Zobrazí se Excelového listu, který obsahuje data z obou účtů.  
  
## <a name="to-add-a-word-document"></a>Chcete-li přidat dokument aplikace Word  
  
1.  Pro ilustraci další způsoby [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]a novějších verzích vylepšuje Office programování, následující kód se otevře aplikace Word a vytvoří ikonu, která odkazuje na Excelový list.  
  
     Vložit metodu `CreateIconInWordDoc`, k dispozici dále v tomto kroku do `Program` třídy. `CreateIconInWordDoc` pojmenované a nepovinné argumenty používá ke snížení složitosti volání metody <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> a <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. Tato volání začlenit dvě další nové vlastnosti představené v [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] , která zjednodušují volání metody COM, které mají parametry odkazů. Nejprve můžete poslat argumenty parametrů odkazu jako by byly parametry s hodnotou. To znamená můžete odeslat hodnoty přímo, bez vytváření proměnných pro každý odkaz na parametr. Kompilátor generuje dočasné proměnné pro uložení hodnoty argumentů a zahodí proměnné při návratu z volání. Za druhé, můžete vynechat `ref` – klíčové slovo v seznamu argumentů.  
  
     `Add` Metoda má čtyři parametry odkazu, z nichž všechny jsou volitelné. V [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], nebo novější verze, pokud chcete použít výchozí hodnoty, můžete vynechat argumenty pro některé nebo všechny parametry. V [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] a starší verze pro každý parametr je třeba zadat argument a argument musí být proměnná, protože parametry jsou parametry odkazů.  
  
     `PasteSpecial` Metoda vloží obsah schránky. Metoda má sedm parametrů odkazu, z nichž všechny jsou volitelné. Následující kód určuje argumenty pro dva z nich: `Link`, chcete-li vytvořit odkaz na zdroj obsah schránky a `DisplayAsIcon`, aby se zobrazil na odkaz jako ikona. V [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], můžete použít pojmenované argumenty pro tyto dvě a ostatní vynechat. I když jsou parametry odkazů, není potřeba použít `ref` – klíčové slovo, nebo k vytvoření proměnné k odeslání jako argumenty. Hodnoty můžete odeslat přímo. V [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] a starší verze, je nutné odeslat argumentů proměnných pro každý odkaz na parametr.  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]  
  
     V [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] nebo starší verze jazyka následující složitější kód je povinný.  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]  
  
2.  Přidejte následující příkaz na konci `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]  
  
3.  Přidejte následující příkaz na konci `DisplayInExcel`. `Copy` Metoda přidá do listu do schránky.  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]  
  
4.  Stisknutím kláves CTRL + F5.  
  
     Zobrazí se Wordový dokument, který obsahuje ikonu. Poklepejte na ikonu na listu přenést do popředí.  
  
## <a name="to-set-the-embed-interop-types-property"></a>Nastavení vlastnosti vložit typy spolupráce  
  
1.  Další vylepšení je možné při volání typu COM, který nevyžaduje, aby primární definiční sestavení (PIA) v době běhu. Odebráním závislosti na výsledky sestavení PIA v nezávislosti na verzi a nasazení. Další informace o výhodách programování bez PIA, naleznete v tématu [názorný postup: Vložení typů ze spravovaných sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
     Programování je navíc jednodušší, protože typy, které vyžadují a vrácené z metody modelu COM lze znázornit pomocí typu `dynamic` místo `Object`. Proměnné, které mají typ `dynamic` není u nich vyhodnoceno až do spuštění, která eliminuje potřebu explicitní přetypování. Další informace najdete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     V [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], vložení informací o typu namísto použití sestavení PIA je výchozí chování. Z důvodu tuto výchozí hodnotu některé z předchozích příkladech jsou jednodušší, protože není nutné explicitní přetypování. Například, deklarace `worksheet` v `DisplayInExcel` je zapsán jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` spíše než `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Volání `AutoFit` v stejným způsobem také by vyžadovaly explicitní přetypování bez výchozí, protože `ExcelApp.Columns[1]` vrátí `Object`, a `AutoFit` je metoda aplikace Excel. Následující kód ukazuje, přetypování.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
2.  Chcete-li změnit výchozí nastavení a použití sestavení PIA místo vložení informací o typu, rozbalte **odkazy** uzel v **Průzkumníka řešení** a pak vyberte **Microsoft.Office.Interop.Excel** nebo **Microsoft.Office.Interop.Word**.  
  
3.  Pokud nevidíte **vlastnosti** okna, stisknutím klávesy **F4**.  
  
4.  Najít **Embed Interop Types** v seznamu vlastností a změňte tuto hodnotu na **False**. Ekvivalentně, můžete zkompilovat pomocí [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru místo [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) z příkazového řádku.  
  
## <a name="to-add-additional-formatting-to-the-table"></a>Chcete-li přidat další formátování do tabulky  
  
1.  Nahraďte dvě volání na `AutoFit` v `DisplayInExcel` pomocí následujícího příkazu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]  
  
     <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Metoda má sedm parametry s hodnotou, z nichž všechny jsou volitelné. Pojmenované a nepovinné argumenty umožňují zadat argumenty pro none, některé nebo všechny z nich. V předchozí prohlášení, je zadán argument pouze pro jeden z parametrů, `Format`. Protože `Format` je první parametr v seznamu parametrů, není nutné poskytnout název parametru. Příkaz může být však lze snáze pochopit, pokud název parametru je součástí, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]  
  
2.  Stisknutím kláves CTRL + F5 k zobrazení výsledku. Další formáty jsou uvedeny v <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> výčtu.  
  
3.  Porovnání příkazu v kroku 1 s následujícím kódem, který ukazuje argumenty, které jsou nezbytné [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] nebo starší verze.  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad.  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
