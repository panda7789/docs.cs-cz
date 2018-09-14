---
title: 'Návod: Vytváření rozšiřitelné aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45561013"
---
# <a name="walkthrough-creating-an-extensible-application"></a>Návod: Vytváření rozšiřitelné aplikace
Tento návod popisuje, jak vytvořit kanál pro doplněk, který provádí funkce jednoduchou kalkulačku. Nepředvádí reálný scénář; Místo toho ukazuje základní funkce kanálu a jak doplněk může poskytovat služby hostitele.  
  
 Tento návod popisuje následující úlohy:  
  
-   Vytváření řešení sady Visual Studio.  
  
-   Vytvoření adresářové struktury kanálu.  
  
-   Vytvoření kontraktu a zobrazení.  
  
-   Vytvoření adaptéru add-na straně.  
  
-   Vytváří se adaptér na straně hostitele.  
  
-   Vytváření hostitele.  
  
-   Vytvoření doplňku.  
  
-   Nasazení kanálu.  
  
-   Spuštění aplikace hostitele.  
  
 Tento kanál předá pouze Serializovatelné typy (<xref:System.Double> a <xref:System.String>), mezi hostitelem a doplňku. Příklad, který ukazuje, jak předat kolekce komplexních datových typů, najdete v části [návod: předávání kolekcí mezi hostiteli a doplňky](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Definuje smlouvu pro tento kanál objektový model, čtyři aritmetických operací: Přidání, odečíst, násobení a dělení. Hostitel poskytuje doplněk rovnice k výpočtu, jako je například 2 + 2, a doplněk vrátí výsledek do hostitele.  
  
 Verze 2-in Kalkulačka poskytuje více výpočtu možnosti a ukazuje, správu verzí. Je popsána v [návod: povolení zpětné kompatibility při změně vašeho hostitele](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat k dokončení tohoto návodu:  
  
-   Visual Studio.  
  
## <a name="creating-a-visual-studio-solution"></a>Vytváření řešení sady Visual Studio  
 Pomocí řešení obsahující projekty segmentů kanálu v sadě Visual Studio.  
  
#### <a name="to-create-the-pipeline-solution"></a>Chcete-li vytvořit kanál řešení  
  
1.  V sadě Visual Studio vytvořte nový projekt s názvem `Calc1Contract`. Založit na **knihovny tříd** šablony.  
  
2.  Pojmenujte řešení `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Vytvoření adresářové struktury kanálu  
 Model doplňku vyžaduje sestavení segment kanálu umístěny ve struktuře zadaný adresář. Další informace o struktuře kanálu najdete v tématu [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Chcete-li vytvořit strukturu adresářů kanálu  
  
1.  Vytvořte složku s aplikace kdekoli ve vašem počítači.  
  
2.  V této složce vytvořte následující strukturu:  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     Není nutné do kanálu strukturu složek ve složce vaší aplikace. Zde je použito pouze ke zvýšení pohodlí. Na příslušný krok průvodce vysvětluje, jak změnit kód v případě strukturu složek kanálu je v jiném umístění. Viz diskuze požadavky adresáře kanálu v [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  `CalcV2` Složky se nepoužívá v tomto názorném postupu; je zástupný symbol pro [návod: povolení zpětné kompatibility při změně vašeho hostitele](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Vytvoření kontraktu a zobrazení  
 Definuje kontrakt segmentu pro tento kanál `ICalc1Contract` rozhraní, která definuje čtyři metody: `add`, `subtract`, `multiply`, a `divide`.  
  
#### <a name="to-create-the-contract"></a>Vytvoření kontraktu  
  
1.  V řešení sady Visual Studio s názvem `CalculatorV1`, otevřete `Calc1Contract` projektu.  
  
2.  V **Průzkumníka řešení**, přidejte odkazy na následující sestavení, které chcete `Calc1Contract` projektu:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  V **Průzkumníka řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty.  
  
4.  V **Průzkumníka řešení**, přidat novou položku do projektu, použití **rozhraní** šablony. V **přidat novou položku** dialogové okno, název rozhraní `ICalc1Contract`.  
  
5.  V souboru rozhraní, přidejte odkazy na obor názvů pro <xref:System.AddIn.Contract> a <xref:System.AddIn.Pipeline>.  
  
6.  Použijte následující kód pro dokončení této smlouvy segmentu. Všimněte si, že toto rozhraní musí mít <xref:System.AddIn.Pipeline.AddInContractAttribute> atribut.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  Volitelně můžete vytvářejte řešení sady Visual Studio. Řešení nelze spustit, dokud posledním kroku, ale jeho sestavení po každý postup zajistí, že každý projekt je opravit.  
  
 Vzhledem k tomu, že zobrazení doplňku a hostitelem zobrazení doplňku mají obvykle stejný kód, zejména v první verzi doplňku, můžete snadno vytvořit zobrazení ve stejnou dobu. Se liší pouze jediný faktor: vyžaduje zobrazení doplňku <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut, zatímco zobrazení hostitele doplňku nevyžaduje žádné atributy.  
  
#### <a name="to-create-the-add-in-view"></a>Vytvoření zobrazení doplňku  
  
1.  Přidat nový projekt s názvem `Calc1AddInView` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníka řešení**, přidejte odkaz na System.AddIn.dll k `Calc1AddInView` projektu.  
  
3.  V **Průzkumníka řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu, použití **rozhraní** šablony. V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.  
  
4.  V souboru rozhraní, přidejte odkaz na obor názvů <xref:System.AddIn.Pipeline>.  
  
5.  Použijte následující kód k dokončení tohoto doplňku v zobrazení. Všimněte si, že toto rozhraní musí mít <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  Volitelně můžete vytvářejte řešení sady Visual Studio.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Chcete-li vytvořit zobrazení hostitele doplňku  
  
1.  Přidat nový projekt s názvem `Calc1HVA` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníka řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu, použití **rozhraní** šablony. V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.  
  
3.  V souboru rozhraní použijte následující kód k dokončení zobrazení hostitele doplňku.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  Volitelně můžete vytvářejte řešení sady Visual Studio.  
  
## <a name="creating-the-add-in-side-adapter"></a>Vytvoření adaptéru přidat v straně  
 Tento adaptér přidat – na straně se skládá z jednoho adaptéru zobrazení smlouvy. Tento segment kanálu převede typy ze zobrazení doplňku na kontrakt.  
  
 V tomto kanálu doplňku poskytuje službu na hostiteli a typy směrovat z doplňku do hostitele. Vzhledem k tomu, že žádné typy tok z hostitele do doplňku, nemají obsahovat zobrazení smlouvy adaptér na straně doplňku tohoto kanálu.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Chcete-li vytvořit adaptér přidat v na straně  
  
1.  Přidat nový projekt s názvem `Calc1AddInSideAdapter` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníka řešení**, přidejte odkazy na následující sestavení, které chcete `Calc1AddInSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Přidejte odkazy na projekty segmentů sousední kanálu:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **Kopírovat místně** k **False**. V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False** dva odkazy projektu.  
  
5.  Přejmenování projektu výchozí třídu `CalculatorViewToContractAddInSideAdapter`.  
  
6.  V souboru třídy přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.  
  
7.  V souboru třídy přidejte odkazy na obor názvů pro sousedící segmenty: `CalcAddInViews` a `CalculatorContracts`. (V jazyce Visual Basic, jsou tyto odkazy na obor názvů `Calc1AddInView.CalcAddInViews` a `Calc1Contract.CalculatorContracts`, pokud jste nevypnuli výchozích názvových prostorů v projektech Visual Basic.)  
  
8.  Použít <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut `CalculatorViewToContractAddInSideAdapter` třídy k jeho identifikaci jako adaptéru add-na straně.  
  
9. Ujistěte se, `CalculatorViewToContractAddInSideAdapter` dědit třídy <xref:System.AddIn.Pipeline.ContractBase>, která poskytuje výchozí implementaci třídy <xref:System.AddIn.Contract.IContract> rozhraní a implementují rozhraní kontraktu kanálu `ICalc1Contract`.  
  
10. Přidat veřejný konstruktor, který přijímá `ICalculator`ukládá do mezipaměti v soukromé pole a volá konstruktor základní třídy.  
  
11. K implementaci členů `ICalc1Contract`, jednoduše zavolejte odpovídající členů `ICalculator` instanci, která je předána do konstruktoru a vrátí výsledky. To se přizpůsobí zobrazení (`ICalculator`) pro kontrakt (`ICalc1Contract`).  
  
     Následující kód ukazuje dokončené adaptér přidat v straně.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. Volitelně můžete vytvářejte řešení sady Visual Studio.  
  
## <a name="creating-the-host-side-adapter"></a>Vytvoření adaptéru hostitelské  
 Tento adaptér hostitelské se skládá z jednoho adaptéru zobrazení smlouvy. Tento segment se přizpůsobí smlouvy na zobrazení hostitele doplňku.  
  
 V tomto kanálu doplňku poskytuje službu na hostiteli a flow typy z doplňku na hostitele. Vzhledem k tomu, že žádné typy tok z hostitele do doplňku, nemají obsahovat adaptér zobrazení smlouvy.  
  
 Implementace správy životního cyklu, použijte <xref:System.AddIn.Pipeline.ContractHandle> objektu, který chcete připojit ke kontraktu token doby života. Odkaz na tento ovladač je nutné zachovat v pořadí pro správu životního cyklu pro práci. Po použití tokenu není zapotřebí žádné další programování, protože v systému může uvolnila objekty když již nejsou déle používány a zpřístupnit je pro uvolnění paměti. Další informace najdete v tématu [Správa životního cyklu](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Chcete-li vytvořit adaptér na straně hostitele  
  
1.  Přidat nový projekt s názvem `Calc1HostSideAdapter` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníka řešení**, přidejte odkazy na následující sestavení, které chcete `Calc1HostSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Přidejte odkazy na projekty sousední segmentů:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **Kopírovat místně** k **False**. V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False** dva odkazy projektu.  
  
5.  Přejmenování projektu výchozí třídu `CalculatorContractToViewHostSideAdapter`.  
  
6.  V souboru třídy přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.  
  
7.  V souboru třídy přidejte odkazy na obor názvů pro sousedící segmenty: `CalcHVAs` a `CalculatorContracts`. (V jazyce Visual Basic, jsou tyto odkazy na obor názvů `Calc1HVA.CalcHVAs` a `Calc1Contract.CalculatorContracts`, pokud jste nevypnuli výchozích názvových prostorů v projektech Visual Basic.)  
  
8.  Použít <xref:System.AddIn.Pipeline.HostAdapterAttribute> atribut `CalculatorContractToViewHostSideAdapter` třídy k jeho identifikaci jako adaptéru hostitelské segmentu.  
  
9. Ujistěte se, `CalculatorContractToViewHostSideAdapter` třída implementovat rozhraní, které představuje zobrazení hostitele doplňku: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` v jazyce Visual Basic).  
  
10. Přidat veřejný konstruktor, který přijímá typ kontraktu kanálu `ICalc1Contract`. Konstruktor musí ukládat do mezipaměti odkaz na kontrakt. Musíte také vytvořit a mezipaměti nový <xref:System.AddIn.Pipeline.ContractHandle> pro kontrakt, ke správě životnosti doplňku.  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> Je důležité pro správu životního cyklu. Pokud selže zachovat odkaz na <xref:System.AddIn.Pipeline.ContractHandle> uvolňování paměti obnoví a kanál vypne, pokud váš program neočekává objektů. To může vést k chybám, které je obtížné diagnostikovat, jako například <xref:System.AppDomainUnloadedException>. Vypnutí je normální fázi běžný kanál, takže neexistuje žádný způsob, jak kód pro správu životního cyklu ke zjištění, že tato podmínka nastane chyba.  
  
11. K implementaci členů `ICalculator`, jednoduše zavolejte odpovídající členů `ICalc1Contract` instanci, která je předána do konstruktoru a vrátí výsledky. To se přizpůsobí kontrakt (`ICalc1Contract`) k zobrazení (`ICalculator`).  
  
     Následující kód ukazuje dokončené adaptér na straně hostitele.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. Volitelně můžete vytvářejte řešení sady Visual Studio.  
  
## <a name="creating-the-host"></a>Vytvoření hostitele  
 Hostitelská aplikace komunikuje s doplněk prostřednictvím zobrazení hostitele doplňku. Používá doplněk zjišťování a aktivaci metody poskytované objektem <xref:System.AddIn.Hosting.AddInStore> a <xref:System.AddIn.Hosting.AddInToken> třídy můžete provádět následující:  
  
-   Aktualizace mezipaměti informace o kanálu a doplňku.  
  
-   Hledání doplňků typu zobrazení hostitele `ICalculator`, v kořenovém adresáři zadané kanálu.  
  
-   Výzva k zadání která doplněk používat.  
  
-   Aktivujte vybrané doplněk v nové doméně aplikace se zadaným zabezpečením úrovně důvěryhodnosti.  
  
-   Spuštění vlastního `RunCalculator` metodu, která volá metody doplňku podle zobrazení hostitele doplňku.  
  
#### <a name="to-create-the-host"></a>Chcete-li vytvořit hostitele  
  
1.  Přidat nový projekt s názvem `Calc1Host` k `CalculatorV1` řešení. Založit na **konzolovou aplikaci** šablony.  
  
2.  V **Průzkumníka řešení**, přidejte odkaz na sestavení System.AddIn.dll `Calc1Host` projektu.  
  
3.  Přidat odkaz na projekt `Calc1HVA` projektu. Vyberte odkaz na projekt a v **vlastnosti** nastavit **Kopírovat místně** k **False**. V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False**.  
  
4.  Přejmenování souboru třídy (modulu v jazyce Visual Basic) `MathHost1`.  
  
5.  V jazyce Visual Basic použijte **aplikace** karty **vlastnosti projektu** dialogové okno nastavit **spouštěcí objekt** k **Sub Main**.  
  
6.  V souboru třídu nebo modul, přidejte odkaz na obor názvů <xref:System.AddIn.Hosting>.  
  
7.  V souboru třídu nebo modul, přidejte odkaz na obor názvů pro zobrazení hostitele doplňku: `CalcHVAs`. (V jazyce Visual Basic, tento odkaz na obor názvů je `Calc1HVA.CalcHVAs`, pokud jste nevypnuli výchozích názvových prostorů v projektech Visual Basic.)  
  
8.  V **Průzkumníku řešení**, vyberte řešení a od **projektu** nabídku zvolte **vlastnosti**. V **stránek vlastností řešení** dialogové okno, nastavte **jeden spouštěný projekt** na tomto projektu hostitelské aplikace.  
  
9. V souboru třídu nebo modul, použijte <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> způsob aktualizace mezipaměti. Použít <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodu pro získání kolekce tokeny a použít <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metoda aktivovat doplněk.  
  
     Následující kód ukazuje dokončené hostitelskou aplikaci.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Tento kód předpokládá, že struktura složek kanál se nachází ve složce aplikace. Pokud jste ho jinde, změňte řádek kódu, který nastaví `addInRoot` proměnné, tak, že proměnná obsahuje cestu k strukturu kanálu.  
  
     Tento kód použije `ChooseCalculator` metoda seznam tokenů a výzva k výběru doplňku. `RunCalculator` Metody vyzve uživatele k jednoduché matematické výrazy, analyzuje výrazů pomocí `Parser` třídy a zobrazí výsledky vracené pomocí doplňku.  
  
10. Volitelně můžete vytvářejte řešení sady Visual Studio.  
  
## <a name="creating-the-add-in"></a>Vytváření v aplikaci  
 Doplněk implementuje metody určené v zobrazení. Tento doplněk implementuje `Add`, `Subtract`, `Multiply`, a `Divide` operace a vrací výsledky do hostitele.  
  
#### <a name="to-create-the-add-in"></a>Chcete-li vytvořit doplněk  
  
1.  Přidat nový projekt s názvem `AddInCalcV1` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníka řešení**, přidejte odkaz na sestavení System.AddIn.dll do projektu.  
  
3.  Přidat odkaz na projekt `Calc1AddInView` projektu. Vyberte odkaz na projekt a v **vlastnosti**, nastavte **Kopírovat místně** k **False**. V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False** pro odkaz na projekt.  
  
4.  Tuto třídu přejmenovat `AddInCalcV1`.  
  
5.  V souboru třídy přidejte odkaz na obor názvů <xref:System.AddIn> a segment zobrazení doplňku: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` v jazyce Visual Basic).  
  
6.  Použít <xref:System.AddIn.AddInAttribute> atribut `AddInCalcV1` třídy k identifikaci třídy jako doplněk.  
  
7.  Ujistěte se, `AddInCalcV1` třída implementovat rozhraní, které představuje zobrazení doplňku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` v jazyce Visual Basic).  
  
8.  Implementovat členy `ICalculator` tak, že vrací výsledky odpovídající výpočtů.  
  
     Následující kód ukazuje dokončené doplňku.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. Volitelně můžete vytvářejte řešení sady Visual Studio.  
  
## <a name="deploying-the-pipeline"></a>Nasazení kanálu  
 Nyní jste připraveni k sestavení a nasazení segmenty doplňku do struktury adresářů požadované kanálu.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>K nasazení segmenty kanálu  
  
1.  Pro každý projekt v řešení, použijte **sestavení** kartě **vlastnosti projektu** ( **kompilaci** kartu v jazyce Visual Basic) k nastavení hodnoty **výstupní cesta**  ( **výstupní cesta sestavení** v jazyce Visual Basic). Pokud název složky aplikace `MyApp`, například by vaše projekty sestavení do následující složky:  
  
    |Projekt|Cesta|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|Moje aplikace|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|Moje aplikace|  
  
    > [!NOTE]
    >  Pokud jste se rozhodli umístit vaše struktura složky kanálu do jiného umístění než složce vaší aplikace, je nutné upravit cesty uvedené v tabulce odpovídajícím způsobem. Viz diskuze požadavky adresáře kanálu v [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Sestavte řešení sady Visual Studio.  
  
3.  Zkontrolujte aplikaci a kanál adresáře pro zajištění, že sestavení byly zkopírovány do správného adresáře a, zda byly nainstalovány žádné další kopie sestavení ve složce nesprávné.  
  
    > [!NOTE]
    >  Pokud jste nezměnili **Kopírovat místně** k **False** pro `Calc1AddInView` odkaz v projektu `AddInCalcV1` projektu, zavaděč zamezili problémům zabrání doplněk se nachází.  
  
     Informace o nasazení do tohoto kanálu najdete v tématu [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Spuštění aplikace hostitele  
 Nyní jste připraveni spustit hostiteli a interakci s doplňku.  
  
#### <a name="to-run-the-host-application"></a>Ke spuštění aplikace hostitele  
  
1.  Na příkazovém řádku přejděte do adresáře aplikace a spuštění aplikace hostitele `Calc1Host.exe`.  
  
2.  Hostitel najde všechny dostupné doplňky jeho typu a výzva k výběru doplňku. Zadejte **1** pro pouze dostupnému doplňku.  
  
3.  Zadejte rovnice pro kalkulačky, jako například **2 + 2**. Musí existovat mezery mezi čísla a operátor.  
  
4.  Typ **ukončit** a stiskněte klávesu **Enter** zavřít aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Umožnění zpětné kompatibility při změně vašeho hostitele](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [Návod: Předávání kolekcí mezi hostiteli a doplňky](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Kontrakty, zobrazení a adaptéry](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [Vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md)
