---
title: "Návod: Vytváření rozšiřitelné aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cee99346d19c632739bcc6540c43f1a35217a2f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-extensible-application"></a>Návod: Vytváření rozšiřitelné aplikace
Tento návod popisuje, jak vytvořit kanál pro doplněk provádí jednoduché Kalkulačka funkcí. Nepředvádí scénářem z reálného prostředí; Místo toho ukazuje základní funkce kanálu a jak doplňku poskytuje služby pro hostitele.  
  
 Tento návod popisuje následující úlohy:  
  
-   Vytváření řešení sady Visual Studio.  
  
-   Vytvoření kanálu adresářové struktury.  
  
-   Vytvoření kontraktu a zobrazení.  
  
-   Vytvoření adaptéru přidat straně.  
  
-   Vytvoření adaptéru straně hostitele.  
  
-   Vytváření hostitele.  
  
-   Vytváření v doplňku.  
  
-   Nasazení kanálu.  
  
-   Spuštění hostitelskou aplikaci.  
  
 Tento kanál předá pouze Serializovatelné typy (<xref:System.Double> a <xref:System.String>), mezi hostitelem a doplněk. Příklad, který ukazuje, jak předat kolekce komplexními datovými typy, naleznete v části [návod: předávání kolekce mezi hostiteli a doplňky](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Definuje smlouvu pro tento kanál objektový model čtyři aritmetických operací: přidat, odečíst, násobit a dělit. Hostitel poskytuje doplněk rovnici k výpočtu, jako je například 2 + 2, a v doplňku vrátí výsledek na hostitele.  
  
 Verze 2-in kalkulačky poskytuje více výpočtu možnosti a předvádí správy verzí. Je popsán v [návod: povolení zpětné kompatibility jako vaše změny hostitele](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat k dokončení tohoto názorného postupu:  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="creating-a-visual-studio-solution"></a>Vytváření řešení sady Visual Studio  
 Použít řešení v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] tak, aby obsahovala projektů segmenty kanálu.  
  
#### <a name="to-create-the-pipeline-solution"></a>Chcete-li vytvořit kanál řešení  
  
1.  V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vytvořte nový projekt s názvem `Calc1Contract`. Založit na **knihovny tříd** šablony.  
  
2.  Název řešení `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Vytvoření kanálu adresářové struktury  
 Model doplněk vyžaduje sestavení segment kanálu, které chcete umístit do struktury určeného adresáře. Další informace o struktuře kanálu najdete v tématu [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Chcete-li vytvořit strukturu adresáře kanálu  
  
1.  Vytváření složky aplikace kdekoli v počítači.  
  
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
  
     Není nutné uvést struktura složek kanálu ve složce aplikace; se provádí zde pouze ke zvýšení pohodlí. V příslušné kroku průvodce vysvětluje, jak změnit kód v případě struktura složek kanálu je v jiném umístění. Přečtěte si diskuzi o kanálu directory požadavky v [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  `CalcV2` Složky není použit v tomto návodu, je zástupný symbol pro [návod: povolení zpětné kompatibility jako vaše změny hostitele](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Vytvoření kontraktu a zobrazení  
 Definuje kontrakt segmentu pro tento kanál `ICalc1Contract` rozhraní, které definuje čtyři metody: `add`, `subtract`, `multiply`, a `divide`.  
  
#### <a name="to-create-the-contract"></a>K vytvoření kontraktu  
  
1.  V sadě Visual Studio řešení s názvem `CalculatorV1`, otevřete `Calc1Contract` projektu.  
  
2.  V **Průzkumníku řešení**, přidáte odkazy na následující sestavení, které chcete `Calc1Contract` projektu:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  V **Průzkumníku řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty.  
  
4.  V **Průzkumníku řešení**, přidejte novou položku do projektu, pomocí **rozhraní** šablony. V **přidat novou položku** dialogové okno, název rozhraní `ICalc1Contract`.  
  
5.  V souboru rozhraní, přidejte odkazy na obor názvů pro <xref:System.AddIn.Contract> a <xref:System.AddIn.Pipeline>.  
  
6.  Použijte následující kód k dokončení tohoto kontraktu segmentu. Všimněte si, že musí mít toto rozhraní <xref:System.AddIn.Pipeline.AddInContractAttribute> atribut.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  Volitelně můžete sestavte řešení sady Visual Studio. Řešení nelze spustit, dokud poslední postup, ale vytváření ho po každý postup zajišťuje, že každý projekt, opravte.  
  
 Protože zobrazení add-in a hostitel zobrazení doplněk obvykle mají stejný kód, zejména v první verzi doplňku, můžete snadno vytvořit zobrazení ve stejnou dobu. Se liší pouze jediný faktor: Zobrazit doplněk vyžaduje <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributu při zobrazení hostitele add-in nevyžaduje žádné atributy.  
  
#### <a name="to-create-the-add-in-view"></a>Vytvoření zobrazení doplňku  
  
1.  Přidat nový projekt s názvem `Calc1AddInView` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníku řešení**, přidejte odkaz na System.AddIn.dll k `Calc1AddInView` projektu.  
  
3.  V **Průzkumníku řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu pomocí **rozhraní** šablony. V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.  
  
4.  V souboru rozhraní přidat odkaz na obor názvů <xref:System.AddIn.Pipeline>.  
  
5.  Použijte následující kód k dokončení tohoto doplňku zobrazení. Všimněte si, že musí mít toto rozhraní <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  Volitelně můžete sestavte řešení sady Visual Studio.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Vytvoření zobrazení hostitele add-in  
  
1.  Přidat nový projekt s názvem `Calc1HVA` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníku řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu pomocí **rozhraní** šablony. V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.  
  
3.  V souboru rozhraní použijte následující kód k dokončení hostitelském zobrazení v doplňku.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  Volitelně můžete sestavte řešení sady Visual Studio.  
  
## <a name="creating-the-add-in-side-adapter"></a>Vytvoření adaptéru přidat straně  
 Tento adaptér přidat straně se skládá z jednoho zobrazení kontrakt adaptéru. Tento kanál segment převede typy ze zobrazení doplněk kontrakt.  
  
 U tohoto kanálu v doplňku poskytuje službu na hostiteli a typy toku z v doplňku na hostitele. Protože žádné typy toku z hostitele na doplněk, nemáte zahrnují adaptér kontrakt zobrazení na straně doplňku tohoto kanálu.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Chcete-li vytvořit adaptér přidat straně  
  
1.  Přidat nový projekt s názvem `Calc1AddInSideAdapter` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníku řešení**, přidáte odkazy na následující sestavení, které chcete `Calc1AddInSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Přidejte odkazy na projekt na projekty na segmenty přiléhající kanál:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **místní kopie** k **False**. V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False** pro dva odkazy na projekt.  
  
5.  Přejmenování projektu výchozí třídu `CalculatorViewToContractAddInSideAdapter`.  
  
6.  V souboru třídy, přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.  
  
7.  V souboru třídy, přidejte odkazy na obor názvů pro přiléhající segmenty: `CalcAddInViews` a `CalculatorContracts`. (V jazyku Visual Basic, jsou tyto odkazy na obor názvů `Calc1AddInView.CalcAddInViews` a `Calc1Contract.CalculatorContracts`, pokud jste vypnuli výchozí obory názvů v projektech Visual Basic.)  
  
8.  Použít <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut `CalculatorViewToContractAddInSideAdapter` třída identifikovat jako adaptér přidat straně.  
  
9. Ujistěte se, `CalculatorViewToContractAddInSideAdapter` dědění třídy <xref:System.AddIn.Pipeline.ContractBase>, který poskytuje výchozí implementaci třídy <xref:System.AddIn.Contract.IContract> rozhraní a implementovat rozhraní kontraktu pro kanál, `ICalc1Contract`.  
  
10. Přidejte konstruktor public, který přijímá `ICalculator`, ukládá do mezipaměti v soukromé pole a volá konstruktor základní třídy.  
  
11. K implementaci členů `ICalc1Contract`, jednoduše volání odpovídající členů `ICalculator` instance, který je předaný konstruktoru a vrátí výsledky. Toto přizpůsobení zobrazení (`ICalculator`) se smlouvou (`ICalc1Contract`).  
  
     Následující kód ukazuje dokončené adaptér přidat straně.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. Volitelně můžete sestavte řešení sady Visual Studio.  
  
## <a name="creating-the-host-side-adapter"></a>Vytvoření adaptéru straně hostitele  
 Tento adaptér hostitelské se skládá z jednoho zobrazení smlouvy adaptéru. Tento segment přizpůsobuje smlouvy na hostitelském zobrazení v doplňku.  
  
 U tohoto kanálu v doplňku poskytuje službu na hostiteli a typy toku z doplněk k hostiteli. Protože žádné typy toku z hostitele na doplněk, nemáte zahrnují adaptér zobrazení kontrakt.  
  
 Chcete-li implementovat správu životního cyklu, použijte <xref:System.AddIn.Pipeline.ContractHandle> objekt, který chcete přiřadit kontrakt doba platnosti tokenu. Odkaz na tento popisovač musí zůstat v pořadí pro správu životního cyklu pro práci. Po použití tokenu žádné další programování není nutná, protože v systému může odstranění objektů při jejich se již nepoužívají a zpřístupnit pro uvolňování paměti. Další informace najdete v tématu [správu životního cyklu](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Chcete-li vytvořit adaptér straně hostitele  
  
1.  Přidat nový projekt s názvem `Calc1HostSideAdapter` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníku řešení**, přidáte odkazy na následující sestavení, které chcete `Calc1HostSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Přidejte odkazy na projekt na projekty na sousedících segmenty:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **místní kopie** k **False**. V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False** pro dva odkazy na projekt.  
  
5.  Přejmenování projektu výchozí třídu `CalculatorContractToViewHostSideAdapter`.  
  
6.  V souboru třídy, přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.  
  
7.  V souboru třídy, přidejte odkazy na obor názvů pro přiléhající segmenty: `CalcHVAs` a `CalculatorContracts`. (V jazyku Visual Basic, jsou tyto odkazy na obor názvů `Calc1HVA.CalcHVAs` a `Calc1Contract.CalculatorContracts`, pokud jste vypnuli výchozí obory názvů v projektech Visual Basic.)  
  
8.  Použít <xref:System.AddIn.Pipeline.HostAdapterAttribute> atribut `CalculatorContractToViewHostSideAdapter` třída identifikovat jako adaptér hostitelské segment.  
  
9. Ujistěte se, `CalculatorContractToViewHostSideAdapter` třída implementovat rozhraní, které představuje hostitelském zobrazení v doplňku: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` v jazyce Visual Basic).  
  
10. Přidejte konstruktor public, který přijímá kontrakt typ kanálu `ICalc1Contract`. Konstruktor musí mezipaměti odkaz na kontrakt. Musíte také vytvořit a mezipaměti novou <xref:System.AddIn.Pipeline.ContractHandle> pro kontrakt, Správa životního cyklu add-in.  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> Je důležité pro správu životního cyklu. Pokud se nepodaří zachovat odkaz na <xref:System.AddIn.Pipeline.ContractHandle> objektu uvolňování paměti se uvolnit ho a kanál vypne, pokud váš program neočekává. To může způsobit chyby, které je obtížné diagnostikovat, jako například <xref:System.AppDomainUnloadedException>. Vypnutí je normální úsek dobu životnosti kanál, takže neexistuje žádný způsob pro kód životního cyklu správy ke zjištění, zda tento stav se o chybu.  
  
11. K implementaci členů `ICalculator`, jednoduše volání odpovídající členů `ICalc1Contract` instance, který je předaný konstruktoru a vrátí výsledky. Toto přizpůsobení kontrakt (`ICalc1Contract`) k zobrazení (`ICalculator`).  
  
     Následující kód ukazuje dokončené adaptér straně hostitele.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. Volitelně můžete sestavte řešení sady Visual Studio.  
  
## <a name="creating-the-host"></a>Vytváření hostitele  
 Komunikuje se službou doplněk prostřednictvím hostitelském zobrazení doplněk hostitelskou aplikaci. Využívá doplněk zjišťování a aktivaci metody poskytované <xref:System.AddIn.Hosting.AddInStore> a <xref:System.AddIn.Hosting.AddInToken> třídy proveďte následující:  
  
-   Aktualizace mezipaměti kanálu a doplněk informací.  
  
-   Najít doplňky typu zobrazení hostitele, `ICalculator`, v kořenovém adresáři zadané kanálu.  
  
-   Vyzvat uživatele k určení, které doplněk používat.  
  
-   Aktivujte vybrané v aplikaci v nové doméně aplikace s úrovní důvěryhodnosti zadaný zabezpečení.  
  
-   Spusťte vlastní `RunCalculator` metodu, která volá metody v doplňku na podle specifikace hostitelském zobrazení v doplňku.  
  
#### <a name="to-create-the-host"></a>Chcete-li vytvořit hostitele  
  
1.  Přidat nový projekt s názvem `Calc1Host` k `CalculatorV1` řešení. Založit na **konzolové aplikace** šablony.  
  
2.  V **Průzkumníku řešení**, přidejte odkaz na sestavení System.AddIn.dll do `Calc1Host` projektu.  
  
3.  Přidat odkaz na projekt `Calc1HVA` projektu. Vyberte odkaz na projekt a v **vlastnosti** nastavit **místní kopie** k **False**. V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False**.  
  
4.  Přejmenujte soubor – třída (modulu v jazyce Visual Basic) `MathHost1`.  
  
5.  V jazyce Visual Basic, použijte **aplikace** kartě **vlastnosti projektu** dialogové okno nastavit **spouštěcí objekt** k **Sub Main**.  
  
6.  V souboru třídy nebo modulu Přidat odkaz na obor názvů <xref:System.AddIn.Hosting>.  
  
7.  V souboru třídy nebo modulu Přidat odkaz na obor názvů pro hostitele zobrazení add-in: `CalcHVAs`. (V jazyku Visual Basic, je tento odkaz na obor názvů `Calc1HVA.CalcHVAs`, pokud jste vypnuli výchozí obory názvů v projektech Visual Basic.)  
  
8.  V **Průzkumníku řešení**, vyberte řešení a z **projektu** nabídce zvolte **vlastnosti**. V **stránky vlastností řešení** dialogové okno, sada **jeden spouštěný projekt** jako tento projekt aplikace hostitele.  
  
9. V souboru třídy nebo modulu, použijte <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> metodu za účelem aktualizace mezipaměti. Použít <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodu za účelem získání kolekce tokenů a použít <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metodu pro aktivaci v.  
  
     Následující kód ukazuje dokončené hostitelskou aplikaci.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Tento kód předpokládá, že struktura složek kanál se nachází ve složce aplikace. Pokud jste ho jinam, změňte řádek kódu, který nastaví `addInRoot` proměnné tak, aby se proměnná obsahuje cestu k kanálu adresářové struktury.  
  
     Kód používá `ChooseCalculator` metoda seznam tokenů a aby se zobrazila výzva k výběru doplňku. `RunCalculator` Metoda vyzve uživatele k jednoduché matematické výrazy, analyzuje výrazy pomocí `Parser` třídy a zobrazí výsledky vracené pomocí doplňku.  
  
10. Volitelně můžete sestavte řešení sady Visual Studio.  
  
## <a name="creating-the-add-in"></a>Vytváření v aplikaci  
 Doplněk implementuje metody zadaný v zobrazení. Tento doplněk implementuje `Add`, `Subtract`, `Multiply`, a `Divide` operace a vrací výsledky do hostitele.  
  
#### <a name="to-create-the-add-in"></a>Chcete-li vytvořit v doplňku  
  
1.  Přidat nový projekt s názvem `AddInCalcV1` k `CalculatorV1` řešení. Založit na **knihovny tříd** šablony.  
  
2.  V **Průzkumníku**, přidejte odkaz na sestavení System.AddIn.dll do projektu.  
  
3.  Přidat odkaz na projekt `Calc1AddInView` projektu. Vyberte odkaz na projekt a v **vlastnosti**, nastavte **místní kopie** k **False**. V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False** pro odkaz na projekt.  
  
4.  Přejmenování třídy `AddInCalcV1`.  
  
5.  V souboru třídy, přidejte odkaz na obor názvů <xref:System.AddIn> a doplněk zobrazení segmentu: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` v jazyce Visual Basic).  
  
6.  Použít <xref:System.AddIn.AddInAttribute> atribut `AddInCalcV1` třída k identifikaci třídy jako doplněk.  
  
7.  Ujistěte se, `AddInCalcV1` třída implementovat rozhraní, které představuje zobrazení doplňku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` v jazyce Visual Basic).  
  
8.  Implementace členů `ICalculator` vrácením výsledky odpovídající výpočtů.  
  
     Následující kód ukazuje dokončené doplňku.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. Volitelně můžete sestavte řešení sady Visual Studio.  
  
## <a name="deploying-the-pipeline"></a>Nasazení kanálu  
 Nyní jste připraveni k sestavení a nasazení segmenty doplněk do struktury adresářů požadované kanálu.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>K nasazení segmentů do kanálu  
  
1.  Pro každý projekt v řešení použít **sestavení** kartě **vlastnosti projektu** ( **zkompilovat** karta v jazyce Visual Basic) nastavit hodnotu **výstupní cesta**  ( **výstupní cesta sestavení** v jazyce Visual Basic). Pokud název vaší aplikace složky `MyApp`, například by vašich projektů sestavení do následující složky:  
  
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
    >  Pokud jste se rozhodli vrátit strukturu kanálu složku v umístění než složce aplikace, musíte upravit cesty uvedené v tabulce odpovídajícím způsobem. Přečtěte si diskuzi o kanálu directory požadavky v [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Sestavte řešení sady Visual Studio.  
  
3.  Zkontrolujte adresáře aplikace a kanál zajistit, že sestavení byly zkopírovány do adresáře správný a zda byly nainstalovány žádné další kopie sestavení v nesprávný složky.  
  
    > [!NOTE]
    >  Pokud jste nezměnili **místní kopie** k **False** pro `Calc1AddInView` odkaz v projektu `AddInCalcV1` projektu, problémů kontextu zavaděč zabrání v doplňku by byly umístěny.  
  
     Informace o nasazení do kanálu najdete v tématu [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Spuštění aplikace hostitele  
 Nyní jste připraveni ke spuštění hostitele a interakci s doplněk.  
  
#### <a name="to-run-the-host-application"></a>Ke spuštění aplikace hostitele  
  
1.  Na příkazovém řádku přejděte do adresáře aplikace a spusťte aplikaci hostitele `Calc1Host.exe`.  
  
2.  Hostitel vyhledá všechny add in k dispozici jeho typu a výzva k výběru doplňku. Zadejte **1** pro k dispozici pouze v aplikaci.  
  
3.  Zadejte rovnici kalkulačky, jako například **2 + 2**. Musí existovat mezery mezi čísla a operátor.  
  
4.  Typ **ukončete** a stiskněte klávesu **Enter** klíč aplikace se zavře.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Povolení zpětné kompatibility jako hostitele změny](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [Návod: Předávání kolekce mezi hostiteli a doplňky](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Kontrakty, zobrazení a adaptéry](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [Vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md)
