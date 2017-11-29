---
title: "Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office (Průvodce programováním v C#)
Pojmenované argumenty a volitelné argumenty, počínaje [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zvýšení pohodlí, flexibilitu a čitelnost v C# – programování. Kromě toho tyto funkce výrazně usnadnit přístup k rozhraní modelu COM, jako je například Microsoft Office automatizace rozhraní API.  
  
 V následujícím příkladu metoda [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) má šestnáct parametry, které představují vlastností tabulky jako počet sloupců a řádků, formátování, ohraničení, písma a barvy. Všechny šestnáct parametry jsou volitelné, protože ve většině případů nechcete zadat konkrétní hodnoty pro všechny z nich. Ale bez pojmenované a nepovinné argumenty, hodnotu nebo hodnotu zástupného symbolu je třeba zadat pro jednotlivé parametry. Pomocí pojmenovaných a nepovinných argumentů je určit pouze hodnoty parametrů, které jsou požadovány pro svůj projekt.  
  
 Musíte mít aplikaci Microsoft Office Word v počítači nainstalována k provedení těchto postupů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Chcete-li vytvořit novou konzolovou aplikaci  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
3.  V **kategorie šablony** podokně rozbalte **Visual C#**a potom klikněte na **Windows**.  
  
4.  Hledat v horní části **šablony** podokně Ujistěte se, že **rozhraní .NET Framework 4** se zobrazí v **cílové rozhraní** pole.  
  
5.  V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.  
  
6.  Zadejte název pro svůj projekt v **název** pole.  
  
7.  Click **OK**.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
### <a name="to-add-a-reference"></a>Přidání odkazu  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vašeho projektu a pak klikněte na tlačítko **přidat odkaz na**. **Přidat odkaz na** zobrazí se dialogové okno.  
  
2.  Na **.NET** vyberte **Microsoft.Office.Interop.Word** v **název komponenty** seznamu.  
  
3.  Click **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Chcete-li přidat potřebné pomocí direktiv  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Program.cs** souboru a pak klikněte na **kód zobrazení**.  
  
2.  Přidejte následující `using` direktivy na začátek souboru kódu.  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>Zobrazení textu v dokument aplikace Word  
  
1.  V `Program` třídy v souboru Program.cs, přidejte následující metodu pro vytvoření aplikace Word a dokument aplikace Word. [Přidat](http://go.microsoft.com/fwlink/?LinkId=145381) metoda má čtyři volitelné parametry. Tento příklad používá výchozí hodnoty. Proto jsou nezbytné v volání příkazu žádné argumenty.  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  Přidejte následující kód na konci metody určit, kde k zobrazení textu v dokumentu a jaký text k zobrazení.  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
1.  Přidejte následující příkaz na hlavní.  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Stisknutím kombinace kláves CTRL + F5 a spusťte projekt. Dokument aplikace Word se zobrazí, který obsahuje zadaný text.  
  
### <a name="to-change-the-text-to-a-table"></a>Chcete-li změnit text do tabulky  
  
1.  Použití `ConvertToTable` metodu uzavřete text v tabulce. Metoda má šestnáct volitelné parametry. IntelliSense uzavře volitelné parametry v závorkách, jak je znázorněno na následujícím obrázku.  
  
     ![Seznam parametrů pro metodu ConvertToTable. ] (../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
Parametry ConvertToTable  
  
     Pojmenované a nepovinné argumenty umožňují zadat hodnoty pro jenom parametry, které chcete změnit. Přidejte následující kód do konce metoda `DisplayInWord` k vytvoření jednoduché tabulky. Argument určuje, že řetězec čárky v textu v `range` oddělení buňky tabulky.  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     V dřívějších verzích systému C#, volání `ConvertToTable` vyžaduje argument typu odkaz pro všechny parametry, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Stisknutím kombinace kláves CTRL + F5 a spusťte projekt.  
  
### <a name="to-experiment-with-other-parameters"></a>A experimentovat s další parametry  
  
1.  Chcete-li změnit v tabulce tak, aby měl jeden sloupec a tři řádky, nahraďte na posledním řádku `DisplayInWord` s následující příkaz a pak zadejte CTRL + F5.  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  Pro určení předdefinované formátu pro tabulku, nahraďte na posledním řádku `DisplayInWord` s následující příkaz a pak zadejte CTRL + F5. Formát může být libovolná z [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) konstanty.  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje kompletní příklad.  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
