---
title: 'Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: f86509b7257f25e8faaadfc107ad70ca794aeee0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883794"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)
Pojmenované argumenty a nepovinné argumenty, počínaje [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zvyšuje pohodlí, flexibilitu a lepší čitelnost v programování v jazyce C#. Kromě toho tyto funkce výrazně usnadňují přístup k rozhraní modelu COM, jako je například rozhraní API automatizace Microsoft Office.  
  
 V následujícím příkladu metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) má šestnáct parametry, které představují vlastnosti tabulky, například počet sloupců a řádků, formátování, ohraničení, písma a barvy. Všechny šestnáct parametry jsou volitelné, protože ve většině případů nechcete zadat konkrétní hodnoty pro všechny z nich. Ale bez pojmenované a nepovinné argumenty, hodnotu nebo hodnotu zástupného symbolu musí být k dispozici pro každý parametr. U pojmenovaných a nepovinných argumentů můžete zadat pouze hodnoty parametrů, které jsou požadovány pro váš projekt.  
  
 Musíte mít aplikaci Microsoft Office Word nainstalována v počítači pro dokončení těchhle postupů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Vytvořte novou konzolovou aplikaci  
  
1.  Spusťte sadu Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V **kategorií šablon** podokně rozbalte **Visual C#** a potom klikněte na tlačítko **Windows**.  
  
4.  Hledat v horní části **šablony** podokno a ujistěte se, že **rozhraní .NET Framework 4** se zobrazí v **Cílová architektura** pole.  
  
5.  V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.  
  
6.  Zadejte název pro váš projekt v **název** pole.  
  
7.  Klikněte na tlačítko **OK**.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
### <a name="to-add-a-reference"></a>Přidání odkazu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz**. **Přidat odkaz** zobrazí se dialogové okno.  
  
2.  Na **.NET** stránce **Microsoft.Office.Interop.Word** v **název komponenty** seznamu.  
  
3.  Klikněte na tlačítko **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Chcete-li přidat nezbytné direktivy using  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující `using` direktivy do horní části souboru kódu.  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>K zobrazení textu v dokumentu aplikace Word  
  
1.  V `Program` třídy v souboru Program.cs, přidejte následující metodu pro vytvoření aplikace Word a Wordový dokument. [Přidat](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) metoda má čtyři volitelné parametry. Tento příklad používá výchozí hodnoty. Proto jsou nezbytné v příkazu volání bez argumentů.  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  Přidejte následující kód na konci metody určit, kde k zobrazení textu v dokumentu a jaký text k zobrazení.  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
1.  Main přidejte následující příkaz.  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Stiskněte kombinaci kláves CTRL + F5 ke spuštění projektu. Zobrazí se Wordový dokument, který obsahuje zadaný text.  
  
### <a name="to-change-the-text-to-a-table"></a>Chcete-li změnit text do tabulky  
  
1.  Použití `ConvertToTable` metoda k uzavření text v tabulce. Tato metoda má šestnácti volitelné parametry. Technologie IntelliSense obklopuje volitelné parametry v hranatých závorkách, jak je znázorněno na následujícím obrázku.  
  
     ![Seznam parametrů pro metodu ConvertToTable. ](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
Parametry ConvertToTable  
  
     Pojmenované a nepovinné argumenty umožňují zadat hodnoty parametrů, které chcete změnit. Přidejte následující kód na konec metody `DisplayInWord` k vytvoření jednoduché tabulky. Argument určuje, že čárkami v textu řetězce v `range` oddělení buňky tabulky.  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     V dřívějších verzích jazyka C#, volání `ConvertToTable` vyžaduje argument odkazu pro každého parametru, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Stiskněte kombinaci kláves CTRL + F5 ke spuštění projektu.  
  
### <a name="to-experiment-with-other-parameters"></a>Můžete experimentovat s další parametry  
  
1.  Chcete-li změnit tabulku tak, aby měl jeden sloupec a třemi řádky, nahraďte na posledním řádku `DisplayInWord` s následující příkaz a zadejte CTRL + F5.  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  Chcete-li zadat předdefinovaný formát pro tabulku, nahraďte poslední řádek v `DisplayInWord` s následující příkaz a zadejte CTRL + F5. Formát lze rozdělit [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) konstanty.  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje úplný příklad.  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>Viz také

- [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
