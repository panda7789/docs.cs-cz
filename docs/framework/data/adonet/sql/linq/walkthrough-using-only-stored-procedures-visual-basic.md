---
title: 'Návod: Použití jen uložených procedur (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 159b65b4b58b9142a168401ea2a881af2714df5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946630"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>Návod: Použití jen uložených procedur (Visual Basic)
Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům pouze pomocí uložených procedur. Tento přístup často používají správci databáze k omezení způsobu přístupu k úložišti dat.  
  
> [!NOTE]
> Uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacích můžete použít také k přepsání výchozího chování, zejména pro `Create`procesy, `Update`a `Delete` . Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Pro účely tohoto Názorného postupu použijete dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist. Mapování probíhá při spuštění nástroje příkazového řádku SqlMetal pro vygenerování souboru Visual Basic. Další informace najdete v části požadavky dále v tomto návodu.  
  
 Tento návod nespoléhá na Návrhář relací objektů. Vývojáři, kteří používají Visual Studio, mohou také použít návrháře O/R k implementaci funkcí uložených procedur. Viz [nástroje LINQ to SQL v aplikaci Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán pomocí Visual Basic nastavení vývoje.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod vyžaduje následující:  
  
- Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest3). Před zahájením tohoto návodu vytvořte tuto složku.  
  
- Ukázkovou databázi Northwind  
  
     Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft. Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest3.  
  
- Visual Basic soubor kódu vygenerovaný z databáze Northwind.  
  
     Tento návod byl napsán pomocí nástroje SqlMetal s následujícím příkazovým řádkem:  
  
     **SQLMetal/Code: "c:\linqtest3\northwind.vb"/Language: VB "c:\linqtest3\northwnd.mdf"/sprocs/Functions/pluralize**  
  
     Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá ze šesti hlavních úloh:  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nastavení řešení v aplikaci Visual Studio.  
  
- Do projektu se přidává sestavení System. data. Linq.  
  
- Do projektu se přidává soubor s kódem databáze.  
  
- Vytváří se připojení k databázi.  
  
- Nastavení uživatelského rozhraní  
  
- Spuštění a testování aplikace.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření řešení LINQ to SQL  
 V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
### <a name="to-create-a-linq-to-sql-solution"></a>Vytvoření řešení LINQ to SQL  
  
1. V nabídce **soubor** v aplikaci Visual Studio klikněte na **Nový projekt**.  
  
2. V podokně **typy projektů** v dialogovém okně **Nový projekt** rozbalte položku **Visual Basic**a potom klikněte na možnost **Windows**.  
  
3. V podokně **šablony** klikněte na **model Windows Forms aplikace**.  
  
4. Do pole **název** zadejte **SprocOnlyApp**.  
  
5. Klikněte na **OK**.  
  
     Otevře se Návrhář formulářů.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Přidání odkazu na sestavení LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není zahrnuto do šablony standardní model Windows Forms aplikace. Sestavení bude nutné přidat sami, jak je vysvětleno v následujících krocích:  
  
### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll  
  
1. V **Průzkumník řešení**klikněte na **Zobrazit všechny soubory**.  
  
2. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.  
  
3. V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.  
  
     Sestavení je přidáno do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru s kódem Northwind do projektu  
 Tento krok předpokládá, že jste použili nástroj SqlMetal k vygenerování souboru kódu z ukázkové databáze Northwind. Další informace najdete v části požadavky výše v tomto návodu.  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru s kódem Northwind do projektu  
  
1. V nabídce **projekt** klikněte na položku **Přidat existující položku**.  
  
2. V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest3\northwind.vb a pak klikněte na **Přidat**.  
  
     Do projektu se přidá soubor Northwind. vb.  
  
## <a name="creating-a-database-connection"></a>Vytvoření připojení k databázi  
 V tomto kroku nadefinujete připojení k ukázkové databázi Northwind. Tento návod používá jako cestu "c:\linqtest3\northwnd.mdf".  
  
### <a name="to-create-the-database-connection"></a>Vytvoření připojení k databázi  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1. vb**a pak klikněte na **Zobrazit kód**.  
  
     `Class Form1`zobrazí se v editoru kódu.  
  
2. Do `Form1` bloku kódu zadejte následující kód:  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
 V tomto úkolu vytvoříte rozhraní, aby uživatelé mohli spouštět uložené procedury pro přístup k datům v databázi. V aplikaci, kterou vyvíjíte pomocí tohoto Názorného postupu, mohou uživatelé získat přístup k datům v databázi pouze pomocí uložených procedur integrovaných v aplikaci.  
  
### <a name="to-set-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
  
1. Vraťte se do Návrhář formulářů (**Form1. vb [Design]** ).  
  
2. V nabídce **zobrazení** klikněte na příkaz **Sada nástrojů**.  
  
     Otevře se panel nástrojů.  
  
    > [!NOTE]
    > Klikněte na ikonu Automatické **skrývání** , aby se panel nástrojů otevřel při provádění zbývajících kroků v této části.  
  
3. Přetáhněte dvě tlačítka, dvě textová pole a dva popisky z panelu nástrojů na **Form1**.  
  
     Uspořádejte ovládací prvky jako v doprovodné ilustraci. Rozbalte **Form1** , aby se ovládací prvky vešly do jednoduchého umístění.  
  
4. Klikněte pravým tlačítkem na **Label1**a pak klikněte na **vlastnosti**.  
  
5. Změňte vlastnost **text** z **Label1** na **ENTER ČísloObjednávky:** .  
  
6. Stejným způsobem jako u **Label2**změňte vlastnost **text** z **Label2** na **ENTER CustomerID:** .  
  
7. Stejným způsobem změňte vlastnost **text** pro **Button1** na **Podrobnosti objednávky**.  
  
8. Změňte vlastnost **text** pro **Button2** na **Seřadit historii**.  
  
     Rozšiřte ovládací prvky tlačítko tak, aby byl veškerý text viditelný.  
  
### <a name="to-handle-button-clicks"></a>Pro zpracování kliknutí na tlačítko  
  
1. Poklikejte na **Podrobnosti objednávky** na **Form1** a vytvořte `Button1` obslužnou rutinu události a otevřete Editor kódu.  
  
2. Do `Button1` obslužné rutiny zadejte následující kód:  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. Nyní dvakrát klikněte na **Button2** na Form1 a vytvořte `Button2` obslužnou rutinu události a otevřete Editor kódu.  
  
4. Do `Button2` obslužné rutiny zadejte následující kód:  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní je čas testovat aplikaci. Všimněte si, že váš kontakt s úložištěm dat je omezený na jakékoli akce, které můžou tyto dvě uložené procedury provádět. Tyto akce mají vracet produkty zahrnuté do každé položky ČísloObjednávky, které zadáte, nebo vrátí historii produktů seřazených podle ID zákazníka, které zadáte.  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1. Stisknutím klávesy F5 spusťte ladění.  
  
     Zobrazí se Form1.  
  
2. Do pole **Zadejte ČísloObjednávky** zadejte **10249** a potom klikněte na **Seřadit podrobnosti**.  
  
     Okno se zprávou obsahuje seznam produktů obsažených v pořadí 10249.  
  
     Kliknutím na tlačítko **OK** zavřete okno se zprávou.  
  
3. Do pole **Zadejte CustomerID** zadejte `ALFKI`a pak klikněte na **Historie objednávek**.  
  
     V okně se zprávou je uveden seznam historie objednávek pro zákaznickou ALFKI.  
  
     Kliknutím na tlačítko **OK** zavřete okno se zprávou.  
  
4. Do pole **Zadejte ČísloObjednávky** zadejte `123`a potom klikněte na **Seřadit podrobnosti**.  
  
     Okno se zprávou zobrazí "žádné výsledky".  
  
     Kliknutím na tlačítko **OK** zavřete okno se zprávou.  
  
5. V nabídce **ladění** klikněte na položku **Zastavit ladění**.  
  
     Ladicí relace se zavře.  
  
6. Pokud jste dokončili experimentování, můžete kliknout na **Zavřít projekt** v nabídce **soubor** a po zobrazení výzvy projekt uložit.  
  
## <a name="next-steps"></a>Další kroky  
 Tento projekt můžete vylepšit tím, že provedete nějaké změny. Můžete například zobrazit seznam dostupných uložených procedur v seznamu a nechat uživatele vybrat, které procedury provést. Výstup sestav můžete také streamovat do textového souboru.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
