---
title: "Postupy: přístup k objektům spolupráce sady Office pomocí Visual C# funkcí (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25e83195d5f0d8a49e402a5a32e61940960b052a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Postupy: přístup k objektům spolupráce sady Office pomocí Visual C# funkcí (C# Průvodce programováním)
Visual C# obsahuje funkce, které zjednodušují přístup k rozhraní API Office objekty. Nové funkce patří pojmenované a nepovinné argumenty, nový typ s názvem `dynamic`a schopnost předání argumentů odkaz parametrů metody modelu COM, jako kdyby byly parametry s hodnotou.  
  
 V tomto tématu budete používat nové funkce napsat kód, který vytvoří a zobrazí tabulku aplikace Microsoft Office Excel. Potom budete psát kód pro přidání dokumentu Office Word, který obsahuje ikonu, která je propojený s sešit aplikace Excel.  
  
 Pro dokončení tohoto návodu, musíte mít aplikaci Microsoft Office Excel 2007 a Microsoft Office Word 2007 nebo novější verze, v počítači nainstalována.  
  
 Pokud používáte operační systém, který je starší než [!INCLUDE[windowsver](~/includes/windowsver-md.md)], ujistěte se, že [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] je nainstalovaná.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Chcete-li vytvořit novou konzolovou aplikaci  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**. **Nový projekt** zobrazí se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně rozbalte **Visual C#**a potom klikněte na **Windows**.  
  
4.  Podívejte se v horní části **nový projekt** dialogovém okně Ujistěte se, že **rozhraní .NET Framework 4** (nebo novější verze) je jako cílové rozhraní vybrána.  
  
5.  V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.  
  
6.  Zadejte název pro svůj projekt v **název** pole.  
  
7.  Click **OK**.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
### <a name="to-add-references"></a>Chcete-li přidat odkazy  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz na**. **Přidat odkaz na** zobrazí se dialogové okno.  
  
2.  Na **sestavení** vyberte **Microsoft.Office.Interop.Word** v **název komponenty** seznamu a pak podržte klávesu CTRL klíče a vyberte možnost  **Microsoft.Office.Interop.Excel**.  Pokud nevidíte sestavení, musíte zajistit, jsou nainstalované a zobrazí (viz [postup: Instalace sestavení sady Office primární zprostředkovatel komunikace s objekty](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))  
  
3.  Click **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Chcete-li přidat potřebné pomocí direktiv  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na **kód zobrazení**.  
  
2.  Přidejte následující `using` direktivy na začátek souboru kódu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]  
  
### <a name="to-create-a-list-of-bank-accounts"></a>Chcete-li vytvořit seznam účtů, bank  
  
1.  Vložte následující definici třídy do **Program.cs**v části `Program` třídy.  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]  
  
2.  Přidejte následující kód, který `Main` metodu pro vytvoření `bankAccounts` seznamu, který obsahuje dva účty.  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]  
  
### <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Chcete-li deklarovat metodu, která exportuje informace o účtu do aplikace Excel  
  
1.  Přidejte následující metodu do `Program` třída nastavit listu aplikace Excel.  
  
     Metoda [přidat](http://go.microsoft.com/fwlink/?LinkId=210910) je volitelný parametr pro zadání konkrétní šablonu. Volitelné parametry, nové v [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], vám umožní argument pro tento parametr vynechat, pokud chcete použít výchozí hodnoty parametru. Vzhledem k tomu, že žádný argument je odesláno jako následující kód, `Add` používá výchozí šablonu a vytvoří nový sešit. Ekvivalentní příkaz v dřívějších verzích systému C# vyžaduje argument zástupný symbol: `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]  
  
2.  Přidejte následující kód na konci `DisplayInExcel`. Kód vloží hodnoty do první dva sloupce prvního řádku listu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]  
  
3.  Přidejte následující kód na konci `DisplayInExcel`. `foreach` Smyčky vloží informace ze seznamu účtů do první dva sloupce po sobě jdoucích řádků listu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]  
  
4.  Přidejte následující kód na konci `DisplayInExcel` na šířku sloupců a přizpůsobit obsah.  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]  
  
     Starší verze jazyka C# vyžadují explicitní přetypování pro tyto operace, protože `ExcelApp.Columns[1]` vrátí `Object`, a `AutoFit` je aplikace Excel [rozsah](http://go.microsoft.com/fwlink/?LinkId=210911) metoda. Zobrazit následující řádky přetypování.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
     [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]a novější verze, převede vrácený `Object` k `dynamic` automaticky, pokud je sestavení odkazuje [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) – možnost kompilátoru nebo ekvivalentně, pokud aplikace Excel **vložit zprostředkovatel komunikace s objekty typy** je nastavena na hodnotu true. Hodnota TRUE, je výchozí hodnota pro tuto vlastnost.  
  
### <a name="to-run-the-project"></a>Spusťte projekt  
  
1.  Přidejte následující řádek na konci `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]  
  
2.  Stisknutím klávesy CTRL + F5.  
  
     Zobrazí se listu aplikace Excel, která obsahuje data z dva účty.  
  
### <a name="to-add-a-word-document"></a>Chcete-li přidat dokument aplikace Word  
  
1.  Pro ilustraci další způsoby, ve kterém [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]a novější verze, zlepšuje Office programování, následující kód k otevření aplikace Word a vytvoří ikonu odkazující na sešit aplikace Excel.  
  
     Vložte metoda `CreateIconInWordDoc`, zadané později v tomto kroku do `Program` třídy. `CreateIconInWordDoc`pojmenované a nepovinné argumenty používá ke snížení složitosti metoda volání [přidat](http://go.microsoft.com/fwlink/?LinkId=210937) a [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099). Tyto volání začlenit dva další nové funkce, zavedená v [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] , volání metod modelu COM, které mají odkaz parametry zjednodušit. První můžete odeslat argumenty k parametrům reference, jako kdyby byly parametry s hodnotou. To znamená můžete odeslat hodnoty přímo, bez vytvoření proměnnou pro každý odkaz na parametr. Kompilátor vygeneruje dočasné proměnné, do kterých argument hodnoty a proměnné, zahodí se při návratu z volání. Druhý, můžete vynechat `ref` – klíčové slovo v seznamu argumentů.  
  
     `Add` Metoda má čtyři odkaz parametry, které jsou volitelné. V [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], nebo novější verze, pokud chcete použít výchozí hodnoty, můžete vynechat argumenty pro všechny parametry. V [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] a starších verzí, je třeba zadat argument pro každý parametr a argument musí být proměnná, protože parametry jsou parametry odkaz.  
  
     `PasteSpecial` Metoda vloží obsah schránky. Metoda má sedm odkaz parametry, které jsou volitelné. Následující kód určuje argumenty pro dvě z nich: `Link`, abyste vytvořili odkaz na zdroj obsah schránky a `DisplayAsIcon`, zobrazí odkaz jako ikona. V [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], můžete použít pojmenované argumenty pro tyto dva a ostatní vynechejte. I když jsou tyto parametry odkaz, není nutné použít `ref` – klíčové slovo, nebo k vytvoření proměnné, které chcete poslat jako argumenty. Hodnoty můžete odeslat přímo. V [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] a starších verzí, je nutné odeslat argumentů proměnných pro každý odkaz na parametr.  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]  
  
     V [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] nebo starší verze jazyka, následující složitější kódu se vyžaduje.  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]  
  
2.  Přidejte následující příkaz na konci `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]  
  
3.  Přidejte následující příkaz na konci `DisplayInExcel`. `Copy` Metoda přidá listu do schránky.  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]  
  
4.  Stisknutím klávesy CTRL + F5.  
  
     Dokument aplikace Word se zobrazí, který obsahuje ikonu. Dvakrát klikněte na ikonu listu přenést do popředí.  
  
### <a name="to-set-the-embed-interop-types-property"></a>Nastavit vlastnost vložit zprostředkovatel komunikace s objekty typy  
  
1.  Další vylepšení je možné při volání COM typ, který nevyžaduje primární spolupracující sestavení (PIA) v době běhu. Odebráním závislosti na výsledky PIA ve verzi nezávislost a jednodušší nasazení. Další informace o výhodách programování bez PIA najdete v tématu [návod: vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
     Programování je navíc jednodušší, protože může být reprezentovaný typy, které jsou potřebné a vrácený metody modelu COM pomocí typu `dynamic` místo `Object`. Proměnné, které mají typ `dynamic` nevyhodnocují do doby běhu, která eliminuje potřebu explicitní přetypování. Další informace najdete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     V [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], vložení informací o typu místo použití PIA je výchozí chování. Z důvodu této výchozí řadu v předchozích příkladech jsou jednodušší, protože není potřeba explicitní přetypování. Například deklaraci `worksheet` v `DisplayInExcel` je zapsána jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` místo `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Volání `AutoFit` v stejnou metodu také by vyžadovaly explicitní přetypování bez výchozí, protože `ExcelApp.Columns[1]` vrátí `Object`, a `AutoFit` je metoda aplikace Excel. Následující kód ukazuje přetypování.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
2.  Chcete-li změnit výchozí nastavení a použít PIA místo vložení informací o typu, rozbalte **odkazy** uzlu v **Průzkumníku řešení** a pak vyberte **Microsoft.Office.Interop.Excel** nebo **Microsoft.Office.Interop.Word**.  
  
3.  Pokud nevidíte **vlastnosti** okno, stiskněte klávesu **F4**.  
  
4.  Najít **vložit zprostředkovatel komunikace s objekty typy** v seznamu vlastností a změňte jeho hodnotu na **False**. Ekvivalentně, můžete zkompilovat pomocí [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru místo [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) na příkazovém řádku.  
  
### <a name="to-add-additional-formatting-to-the-table"></a>Chcete-li přidat další formátování do tabulky  
  
1.  Nahraďte dvě volání `AutoFit` v `DisplayInExcel` s následující příkaz.  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]  
  
     [Automatický formát](http://go.microsoft.com/fwlink/?LinkId=210948) metoda má sedm parametry s hodnotou, což jsou volitelné. Pojmenované a nepovinné argumenty umožňují zadat argumenty pro none, některé nebo všechny z nich. V předchozím příkazu je argument zadaný pouze pro jeden z parametrů `Format`. Protože `Format` je první parametr v seznamu parametrů není nutné zadat název parametru. Příkaz však může být čtení snadněji pochopit, pokud název parametru je zahrnuta, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]  
  
2.  Stisknutím kláves CTRL + F5 zobrazíte výsledek. Ostatní formáty jsou uvedeny v [XlRangeAutoFormat](http://go.microsoft.com/fwlink/?LinkId=210967) výčtu.  
  
3.  Compare – příkaz v kroku 1 následující kód, který zobrazuje argumenty, které jsou potřeba v [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] nebo starší verze.  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad.  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Type.Missing?displayProperty=nameWithType>  
 [dynamické](../../../csharp/language-reference/keywords/dynamic.md)  
 [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Postupy: použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
