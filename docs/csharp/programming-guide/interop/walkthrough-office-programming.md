---
title: "Postupy: Programování pro Office (C# a Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 862f445107e0f58e8e00fba1708156c747165def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Postupy: Programování pro Office (C# a Visual Basic)
Visual Studio nabízí funkce v C# a Visual Basic, které vylepšují programování pro Microsoft Office. Užitečné C# – funkce zahrnují pojmenovaných a nepovinných argumentů a návratové hodnoty typu `dynamic`. Programování v modelu COM, můžete vynechat `ref` – klíčové slovo a získat přístup k indexované vlastnosti. Funkce v jazyce Visual Basic zahrnují automaticky implementované vlastnosti příkazy v lambda – výrazy a Inicializátory kolekcí.

Oba jazyky Povolit vložení informace o typu, který umožňuje nasazení sestavení, které pracují se komponenty modelu COM bez nasazení primární spolupracující sestavení (PIA) k počítači uživatele. Další informace najdete v tématu [návod: vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
Tento návod ukazuje tyto funkce v kontextu programování pro Office, ale mnoho z těchto funkcí je také užitečné obecné programování. V tomto návodu použijete aplikaci doplněk aplikace Excel k vytvoření sešitu aplikace Excel. Dále vytvořte dokument aplikace Word, který obsahuje odkaz k sešitu. Nakonec uvidíte postup povolení a zákaz PIA – závislost.  
  
## <a name="prerequisites"></a>Požadavky  

Musíte mít aplikaci Microsoft Office Excel a v počítači nainstalována aplikace Microsoft Office Word k dokončení tohoto postupu.  
  
 Pokud používáte operační systém, který je starší než [!INCLUDE[windowsver](~/includes/windowsver-md.md)], ujistěte se, že [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] je nainstalovaná.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>Nastavit aplikaci doplněk aplikace Excel  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
3.  V **nainstalovaných šablonách** podokně rozbalte **jazyka Visual Basic** nebo **Visual C#**, rozbalte položku **Office**a potom klikněte na rok verze Office produktu.  
  
4.  V **šablony** podokně klikněte na tlačítko **Excel \<verze > Add-in**.  
  
5.  Podívejte se v horní části **šablony** podokně Ujistěte se, že **rozhraní .NET Framework 4**, nebo na novější verzi, se zobrazí v **cílové rozhraní** pole.  
  
6.  Zadejte název pro svůj projekt v **název** pole, pokud chcete.  
  
7.  Click **OK**.  
  
8.  Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
### <a name="to-add-references"></a>Chcete-li přidat odkazy  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz na**. **Přidat odkaz na** zobrazí se dialogové okno.  
  
2.  Na **sestavení** vyberte **Microsoft.Office.Interop.Excel**, verze `<version>.0.0.0` (klíč na čísla verze produktu Office, najdete v části [Versions Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)) v **název komponenty** seznamu a pak podržte klávesu CTRL klíče a vyberte možnost **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Pokud nevidíte sestavení, musíte zajistit, jsou nainstalované a zobrazí (viz [postup: Instalace sestavení sady Office primární zprostředkovatel komunikace s objekty](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).  
  
3.  Click **OK**.  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Přidání potřebných příkazů Imports nebo direktiv using  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ThisAddIn.vb** nebo **ThisAddIn.cs** souboru a pak klikněte na **kód zobrazení**.  
  
2.  Přidejte následující `Imports` příkazy (Visual Basic) nebo `using` direktivy (C#) na začátek souboru kódu, pokud již nejsou přítomny.  
  
     [!code-csharp[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]

     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]
  
### <a name="to-create-a-list-of-bank-accounts"></a>Chcete-li vytvořit seznam účtů, bank  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vašeho projektu, klikněte na **přidat**a potom klikněte na **třída**. Název třídy Account.vb, pokud používáte Visual Basic nebo Account.cs Pokud používáte C#. Klikněte na tlačítko **přidat**.  
  
2.  Nahraďte definici třídy `Account` třídy následujícím kódem. Definice tříd pomocí *automaticky implementované vlastnosti*. Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-csharp[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]

     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  K vytvoření `bankAccounts` seznamu, který obsahuje dva účty, přidejte následující kód, který `ThisAddIn_Startup` metoda v *ThisAddIn.vb* nebo *ThisAddIn.cs*. Pomocí seznamu deklarace *Inicializátory kolekcí*. Další informace najdete v tématu [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-csharp[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]

     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>Export dat do aplikace Excel  
  
1.  Do stejného souboru přidejte následující metodu do `ThisAddIn` třídy. Metoda nastaví sešitu aplikace Excel a exportuje data do ní.  
  
     [!code-csharp[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]

     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     Tato metoda se používají dvě nové C# funkce. Obě tyto funkce již existují v jazyce Visual Basic.  
  
    -   Metoda [přidat](http://go.microsoft.com/fwlink/?LinkId=210910) má *volitelný parametr* pro zadání konkrétní šablonu. Volitelné parametry, nové v [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], vám umožní argument pro tento parametr vynechat, pokud chcete použít výchozí hodnoty parametru. Vzhledem k tomu, že žádný argument se odešlou v předchozím příkladu `Add` používá výchozí šablonu a vytvoří nový sešit. Ekvivalentní příkaz v dřívějších verzích systému C# vyžaduje argument zástupný symbol: `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Další informace najdete v tématu [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   `Range` a `Offset` vlastnosti [rozsah](http://go.microsoft.com/fwlink/?LinkId=210911) objektu použití *indexovaných vlastností* funkce. Tato funkce umožňuje využívat tyto vlastnosti z typů modelu COM pomocí typické C# syntaxi. Indexované vlastnosti taky umožňují používat `Value` vlastnost `Range` objekt, což eliminuje nutnost používat `Value2` vlastnost. `Value` Vlastnost je indexovaný, ale index je volitelné. Nepovinné argumenty a indexované vlastnosti společně v následujícím příkladu.  
  
         [!code-csharp[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         V dřívějších verzích jazyk není zapotřebí speciální syntaxe.  
  
         [!code-csharp[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         Nelze vytvořit indexované vlastnosti. Tato funkce podporuje jenom spotřeba existující indexované vlastnosti.  
  
         Další informace najdete v tématu [postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  Přidejte následující kód na konci `DisplayInExcel` na šířku sloupců a přizpůsobit obsah.  
  
     [!code-csharp[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]

     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     Tyto doplňky ukazují další funkcí v jazyce C#: považuje `Object` hodnoty vrácené z hostitelů COM, jako je Office, jako v případě, že mají typu [dynamické](../../../csharp/language-reference/keywords/dynamic.md). K tomu dojde automaticky při **vložit zprostředkovatel komunikace s objekty typy** je nastaven na výchozí hodnotu, `True`, nebo ekvivalentně, když sestavení se odkazuje [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) – možnost kompilátoru. Typ `dynamic` umožňuje pozdní vazby, již k dispozici v jazyce Visual Basic a zabraňuje explicitní přetypování potřebné v aplikaci Visual C# 2008 a starší verze jazyka.  
  
     Například `excelApp.Columns[1]` vrátí `Object`, a `AutoFit` je aplikace Excel [rozsah](http://go.microsoft.com/fwlink/?LinkId=210911) metoda. Bez `dynamic`, musíte vysílat pro objekt vrácený rutinou `excelApp.Columns[1]` jako instanci `Range` před voláním metody `AutoFit`.  
  
     [!code-csharp[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     Další informace o vložení typy spolupráce najdete v části postupy "najít odkaz na PIA –" a "obnovit závislost PIA –" dál v tomto tématu. Další informace o `dynamic`, najdete v části [dynamické](../../../csharp/language-reference/keywords/dynamic.md) nebo [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### <a name="to-invoke-displayinexcel"></a>K vyvolání DisplayInExcel  
  
1.  Přidejte následující kód na konci `ThisAddIn_StartUp` metoda. Volání `DisplayInExcel` obsahuje dva argumenty. První argument je název seznamu účtů, které mají být zpracovány. Druhý argument je Víceřádkový lambda výraz, který definuje, jak se zpracovat data. `ID` a `balance` hodnoty pro každý účet se zobrazí v sousedících buněk a řádku se zobrazí červeně v případě rovnováhu mezi je menší než nula. Další informace najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-csharp[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]

     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  Ke spuštění programu, stisknutím klávesy F5. Zobrazí se listu aplikace Excel, která obsahuje data z účty.  
  
### <a name="to-add-a-word-document"></a>Chcete-li přidat dokument aplikace Word  
  
1.  Přidejte následující kód na konci `ThisAddIn_StartUp` metodu pro vytvoření dokumentu aplikace Word, který obsahuje odkaz na sešitu aplikace Excel.  
  
     [!code-csharp[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]

     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     Tento kód ukazuje několik nových funkcí v jazyce C#: možnost vynechejte `ref` – klíčové slovo v programování COM, pojmenované argumenty a volitelné argumenty. Tato funkce již existují v jazyce Visual Basic. [PasteSpecial](https://msdn.microsoft.com/library/microsoft.office.interop.word.selection.pastespecial.aspx) metoda má sedm parametry, které jsou definovány jako s volitelnými parametry. Pojmenované a nepovinné argumenty umožňují určit parametry, které chcete pro přístup k podle názvu a odesílání argumenty jenom tyto parametry. V tomto příkladu jsou argumenty posílá udávající, že by měl být vytvářeny odkaz k sešitu do schránky (parametr `Link`), a že je odkaz na dokument aplikace Word jako ikona (parametr `DisplayAsIcon`). Visual C# můžete také vynechejte `ref` – klíčové slovo pro tyto argumenty.
  
### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
1.  Stisknutím klávesy F5 spusťte aplikaci. Spustí se aplikace Excel a zobrazí tabulku, která obsahuje informace z dva účty v `bankAccounts`. Pak se zobrazí dokument aplikace Word, který obsahuje odkaz na tabulku aplikace Excel.  
  
### <a name="to-clean-up-the-completed-project"></a>Vyčistěte dokončené projektu  
  
1.  V sadě Visual Studio, klikněte na tlačítko **Vyčistit řešení** na **sestavení** nabídky. V opačném doplněk se spustí při každém otevření aplikace Excel v počítači.  
  
### <a name="to-find-the-pia-reference"></a>PIA – odkaz  
  
1.  Spusťte aplikaci znovu, ale neklikejte na **Vyčistit řešení**.  
  
2.  Vyberte **spustit**. Vyhledejte **Microsoft Visual Studio \<verze >** a otevřete příkazový řádek vývojáře.  
  
3.  Typ `ildasm` v okně příkazového řádku Visual Studia a potom stiskněte klávesu ENTER. Zobrazí se okno IL DASM.  
  
4.  Na **soubor** nabídky v okně IL DASM vyberte **soubor** > **otevřete**. Klikněte dvakrát na **Visual Studio \<verze >**a potom dvakrát klikněte na **projekty**. Otevřete složku pro svůj projekt a podívejte se ve složce bin/Debug *název projektu*.dll. Klikněte dvakrát na *název projektu*.dll. Nové okno zobrazí atributy vašeho projektu, kromě odkazy na jiné moduly a sestavení. Všimněte si, že obory názvů `Microsoft.Office.Interop.Excel` a `Microsoft.Office.Interop.Word` jsou součástí sestavení. Ve výchozím nastavení v sadě Visual Studio naimportuje kompilátor do vaší sestavení z odkazované PIA – typy, které potřebujete.  
  
     Další informace najdete v tématu [postupy: zobrazení obsahu sestavení](../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
5.  Dvakrát klikněte **MANIFEST** ikonu. Zobrazí se okno obsahující seznam sestavení, které obsahují položky projektu. `Microsoft.Office.Interop.Excel`a `Microsoft.Office.Interop.Word` nejsou zahrnuty do seznamu. Protože typy, které projektu musí byly naimportovány do vašeho sestavení, odkazů na moduly PIA nejsou potřeba. To výrazně zjednodušuje nasazení. PIA nemusí být k dispozici v počítači uživatele, a vzhledem k tomu, že aplikace nevyžaduje nasazení na konkrétní verzi PIA, aplikace může být navrženy pro práci s více verzemi systému Office, za předpokladu, že rozhraní API pro potřeby existovat ve všech verzích .  
  
     Vzhledem k tomu, že nasazení PIA už není nezbytné, může vytvořit aplikaci v pokročilých scénářích, které pracuje s více verzí sady Office, včetně starší verze. Ale funguje pouze v případě, že váš kód nepoužívá žádné rozhraní API, které nejsou k dispozici ve verzi systému Office, že pracujete s. Není vždy zrušte jestli dané rozhraní API byla k dispozici ve starší verzi a že důvod práce s předchozími verzemi systému Office se nedoporučuje.  
  
    > [!NOTE]
    > Office nepublikoval PIA před Office 2003. Proto je jediný způsob, jak vygenerovat spolupracující sestavení Office 2002 nebo starší verze importováním odkaz na COM.  
  
6.  Zavřete okno manifestu a okna sestavení.  
  
### <a name="to-restore-the-pia-dependency"></a>Chcete-li obnovit PIA – závislost  
  
1.  V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko. Rozbalte **odkazy** složky a vyberte **Microsoft.Office.Interop.Excel**. Zobrazte stisknutím klávesy F4 **vlastnosti** okno.  
  
2.  V **vlastnosti**s okně změnu **vložit zprostředkovatel komunikace s objekty typy** vlastnost z **True** k **False**.  
  
3.  Opakujte kroky 1 a 2 v tomto postupu pro `Microsoft.Office.Interop.Word`.  
  
4.  V jazyce C#, komentář dvě volání `Autofit` na konci `DisplayInExcel` metoda.  
  
5.  Stisknutím klávesy F5 ověřte, že projektu stále běží správně.  
  
6.  Opakujte kroky 1 – 3 z předchozího postupu a otevřete okno sestavení. Všimněte si, že `Microsoft.Office.Interop.Word` a `Microsoft.Office.Interop.Excel` již nejsou v seznamu vložené sestavení.  
  
7.  Dvakrát klikněte **MANIFEST** ikonu a procházet seznam odkazovaná sestavení. Obě `Microsoft.Office.Interop.Word` a `Microsoft.Office.Interop.Excel` nejsou v seznamu. Protože aplikace odkazuje na aplikace Excel a Word PIA a **vložit zprostředkovatel komunikace s objekty typy** je nastavena na **False**, obě sestavení musí existovat na počítači koncového uživatele.  
  
8.  V sadě Visual Studio, klikněte na tlačítko **Vyčistit řešení** na **sestavení** nabídky vyčistěte dokončený projekt.  
  
## <a name="see-also"></a>Viz také  
 [Automaticky implementované vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)  
 [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Statické a pozdní vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamické](../../../csharp/language-reference/keywords/dynamic.md)  
 [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Lambda – výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 [Návod: Vložení informací o typu ze sestavení sady Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [Návod: Vložení typů z řízených sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Vzájemná funkční spolupráce](../../../csharp/programming-guide/interop/index.md)
