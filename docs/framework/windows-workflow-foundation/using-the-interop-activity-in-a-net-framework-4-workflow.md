---
title: Použití aktivity interoperability v pracovním postupu rozhraní .NET Framework 4
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528107"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Použití aktivity interoperability v pracovním postupu rozhraní .NET Framework 4
Aktivity vytvořené pomocí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nebo [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lze použít v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu pomocí <xref:System.Activities.Statements.Interop> aktivity. Toto téma obsahuje přehled používání <xref:System.Activities.Statements.Interop> aktivity.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Aktivity se nezobrazí v panelu nástrojů návrháře postupu, pokud projekt pracovního postupu neobsahuje jeho **Cílová architektura** nastavení **rozhraní .net Framework 4** nebo novější.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Použití aktivity interoperability v pracovních postupech rozhraní .NET Framework 4.5  
 V tomto tématu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] obsahující vytvoření knihovny aktivit `DiscountCalculator` aktivity. `DiscountCalculator` Vypočítá a uplatnit tak slevu na základě částky nákupu a skládá se z <xref:System.Workflow.Activities.SequenceActivity> , která obsahuje <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Používá aktivita vytvořená v tomto tématu <xref:System.Workflow.Activities.PolicyActivity> implementovat logiku aktivity. To není nutné používat vlastní [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivity nebo <xref:System.Activities.Statements.Interop> aktivitu, chcete-li použít pravidla v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Příklad použití pravidel v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu bez použití <xref:System.Activities.Statements.Interop> aktivity, najdete v článku [aktivita Policy v rozhraní .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) vzorku.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Vytvoření projektu knihovny aktivit rozhraní .NET Framework 3.5  
  
1.  Otevřít [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a vyberte **nový** a potom **projektu...** z **souboru** nabídky.  
  
2.  Rozbalte **ostatní typy projektů** uzlu **nainstalované šablony** podokně a vyberte **řešení sady Visual Studio**.  
  
3.  Vyberte **prázdné řešení** z **řešení sady Visual Studio** seznamu. Typ `PolicyInteropDemo` v **název** pole a klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **PolicyInteropDemo** v **Průzkumníka řešení** a vyberte **přidat** a potom **nový projekt...** .  
  
    > [!TIP]
    >  Pokud **Průzkumníka řešení** okno není viditelný, vyberte **Průzkumníka řešení** z **zobrazení** nabídky.  
  
5.  V **nainstalované šablony** seznamu vyberte **Visual C#** a potom **pracovního postupu**. Vyberte **rozhraní .NET Framework 3.5** z rozhraní .NET Framework verze rozevíracího seznamu a pak vyberte **knihovny aktivit pracovních postupů** z **šablony** seznamu.  
  
6.  Typ `PolicyActivityLibrary` v **název** pole a klikněte na tlačítko **OK**.  
  
7.  Klikněte pravým tlačítkem na **Activity1.cs** v **Průzkumníka řešení** a vyberte **odstranit**. Klikněte na tlačítko **OK** potvrďte.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Vytvořit aktivitu DiscountCalculator  
  
1.  Klikněte pravým tlačítkem na **PolicyActivityLibrary** v **Průzkumníka řešení** a vyberte **přidat** a potom **aktivit...** .  
  
2.  Vyberte **aktivita (s rozdělením kódu)** z **položky Visual C#** seznamu. Typ `DiscountCalculator` v **název** pole a klikněte na tlačítko **OK**.  
  
3.  Klikněte pravým tlačítkem na **DiscountCalculator.xoml** v **Průzkumníka řešení** a vyberte **zobrazit kód**.  
  
4.  Přidejte následující tři vlastnosti, které chcete `DiscountCalculator` třídy.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Klikněte pravým tlačítkem na **DiscountCalculator.xoml** v **Průzkumníka řešení** a vyberte **Návrhář zobrazení**.  
  
6.  Přetáhněte **zásady** aktivita z **v3.0 pracovního postupu Windows** část **nástrojů** a umístěte jej do **DiscountCalculator** aktivity .  
  
    > [!TIP]
    >  Pokud **nástrojů** okno není viditelný, vyberte **nástrojů** z **zobrazení** nabídky.  
  
#### <a name="to-configure-the-rules"></a>Konfigurace pravidla  
  
1.  Klikněte na nově přidaných **zásady** aktivity vyberte, pokud ještě není vybraná.  
  
2.  Klikněte na tlačítko **RuleSetReference** vlastnost **vlastnosti** okno ho vyberte a klikněte na tlačítko se třemi tečkami napravo od vlastnost.  
  
    > [!TIP]
    >  Pokud **vlastnosti** okno se nezobrazuje, vyberte **okno vlastností** z **zobrazení** nabídky.  
  
3.  Vyberte **na nový...** .  
  
4.  Klikněte na tlačítko **přidat pravidlo**.  
  
5.  Zadejte následující výraz do **podmínku** pole.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Zadejte následující výraz do **pak akce** pole.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Klikněte na tlačítko **přidat pravidlo**.  
  
8.  Zadejte následující výraz do **podmínku** pole.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Zadejte následující výraz do **pak akce** pole.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Klikněte na tlačítko **přidat pravidlo**.  
  
11. Zadejte následující výraz do **podmínku** pole.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Zadejte následující výraz do **pak akce** pole.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Zadejte následující výraz do **Else akce** pole.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Klikněte na tlačítko **OK** zavřete **editoru nastavte pravidlo** dialogové okno.  
  
15. Ujistěte se, že nově vytvořené <xref:System.Workflow.Activities.Rules.RuleSet> výběru v **název** seznamu a klikněte na tlačítko **OK**.  
  
16. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
 Přidaná do pravidla `DiscountCalculator` aktivity v tomto postupu jsou uvedeny v následujícím příkladu kódu.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Když <xref:System.Workflow.Activities.PolicyActivity> spustí tyto tři pravidla vyhodnotit a upravit `Subtotal`, `DiscountPercent`, a `Total` hodnoty vlastností `DiscountCalculator` aktivity pro výpočet požadovaného slevy.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Použití aktivity DiscountCalculator pomocí aktivity interoperability  
 Použít `DiscountCalculator` aktivity uvnitř [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu, <xref:System.Activities.Statements.Interop> aktivita se používá. V této části dva pracovní postupy jsou vytvářeny, jeden pomocí kódu a pomocí návrháře pracovních postupů, které ukazují, jak používat <xref:System.Activities.Statements.Interop> aktivitu `DiscountCalculator` aktivity. Stejné hostitelské aplikace se používá pro obě pracovních postupů.  
  
#### <a name="to-create-the-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci  
  
1.  Klikněte pravým tlačítkem na **PolicyInteropDemo** v **Průzkumníka řešení** a vyberte **přidat**a potom **nový projekt...** .  
  
2.  Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework a vyberte **Konzolová aplikace pracovního postupu** z **položky Visual C#** seznamu.  
  
3.  Typ `PolicyInteropHost` do **název** pole a klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **vlastnosti**.  
  
5.  V **Cílová architektura** rozevírací seznamu, změnit výběr z **rozhraní .NET Framework 4 Client Profile** k **rozhraní .NET Framework 4.5**. Klikněte na tlačítko **Ano** potvrďte.  
  
6.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **přidat odkaz...** .  
  
7.  Vyberte **PolicyActivityLibrary** z **projekty** kartě a klikněte na tlačítko **OK**.  
  
8.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **přidat odkaz...** .  
  
9. Vyberte **System.Workflow.Activities**, **System.Workflow.ComponentModel**a potom **System.Workflow.Runtime** z **.NET**kartě a klikněte na tlačítko **OK**.  
  
10. Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **nastavit jako spouštěný projekt**.  
  
11. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
### <a name="using-the-interop-activity-in-code"></a>Použití aktivity interoperability v kódu  
 V tomto příkladu se vytvoří pomocí kódu, který obsahuje definici pracovního postupu <xref:System.Activities.Statements.Interop> aktivity a `DiscountCalculator` aktivity. Tento pracovní postup je vyvolán pomocí <xref:System.Activities.WorkflowInvoker> a výsledky vyhodnocení pravidla se zapisují do konzoly pomocí <xref:System.Activities.Statements.WriteLine> aktivity.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Použití aktivity interoperability v kódu  
  
1.  Klikněte pravým tlačítkem na **Program.cs** v **Průzkumníka řešení** a vyberte **zobrazit kód**.  
  
2.  Přidejte následující `using` příkazu v horní části souboru.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  Odebrat obsah `Main` metodu a nahraďte následujícím kódem.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  Vytvoření nové metody v `Program` třídu s názvem `CalculateDiscountUsingCodeWorkflow` , který obsahuje následující kód.  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  `Subtotal`, `DiscountPercent`, A `Total` vlastnosti `DiscountCalculator` aktivity jsou prezentované jako argumenty <xref:System.Activities.Statements.Interop> aktivity a pracovní postup vázaná na místní proměnné v <xref:System.Activities.Statements.Interop> aktivity <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekce. `Subtotal` se přidá jako <xref:System.Activities.ArgumentDirection.In> argument protože `Subtotal` data budou téci do <xref:System.Activities.Statements.Interop> aktivitu, a `DiscountPercent` a `Total` jsou přidány jako <xref:System.Activities.ArgumentDirection.Out> argumenty vzhledem k tomu, že svá data toky z celkového počtu <xref:System.Activities.Statements.Interop> aktivity. Všimněte si, že dva <xref:System.Activities.ArgumentDirection.Out> argumenty se dají s názvy `DiscountPercentOut` a `TotalOut` k označení, že představují <xref:System.Activities.ArgumentDirection.Out> argumenty. `DiscountCalculator` Type je zadaný jako <xref:System.Activities.Statements.Interop> aktivity <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci. Nahraďte různé hodnoty `Subtotal` hodnotu k otestování slevu na různé úrovně poskytovaných `DiscountCalculator` aktivity.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Použití aktivity interoperability v Návrháři postupu provádění  
 V tomto příkladu se vytvoří pracovní postup pomocí návrháře postupu provádění. Tento pracovní postup má stejnou funkci jako předchozí příklad s výjimkou než místo <xref:System.Activities.Statements.WriteLine> aktivita k zobrazení slevy, hostitelské aplikace načte a zobrazí informace o slevy po dokončení pracovního postupu. Také namísto použití místního pracovního postupu proměnné tak, aby obsahovala data, argumenty jsou vytvořené v Návrháři pracovních postupů a hodnoty jsou předány v z hostitele, když uživatel vyvolá pracovní postup.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>K hostování aktivitě PolicyActivity pomocí návrháře postupu provádění vytvoření pracovního postupu  
  
1.  Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníka řešení** a vyberte **odstranit**. Klikněte na tlačítko **OK** potvrďte.  
  
2.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **přidat**, **novou položku...** .  
  
3.  Rozbalte **položky Visual C#** uzel a vyberte možnost **pracovního postupu**. Vyberte **aktivity** z **položky Visual C#** seznamu.  
  
4.  Typ `DiscountWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
5.  Klikněte na tlačítko **argumenty** tlačítko v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.  
  
6.  Klikněte na tlačítko **vytvořit Argument**.  
  
7.  Typ `Subtotal` do **název** vyberte **v** z **směr** rozevíracího seznamu, vyberte **Double** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER, chcete-li uložit argument.  
  
    > [!NOTE]
    >  Pokud **Double** se nepoužívá **typ argumentu** rozevíracího seznamu vyberte **vyhledat typy...** , typ `System.Double` v **název typu** pole a klikněte na tlačítko **OK**.  
  
8.  Klikněte na tlačítko **vytvořit Argument**.  
  
9. Typ `DiscountPercent` do **název** vyberte **si** z **směr** rozevíracího seznamu, vyberte **Double** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER, chcete-li uložit argument.  
  
10. Klikněte na tlačítko **vytvořit Argument**.  
  
11. Typ `Total` do **název** vyberte **si** z **směr** rozevíracího seznamu, vyberte **Double** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER, chcete-li uložit argument.  
  
12. Klikněte na tlačítko **argumenty** tlačítko v levém dolním rohu návrháře postupu provádění, zavřete **argumenty** podokně.  
  
13. Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte jej na plochu návrháře pracovního postupu.  
  
14. Přetáhněte **zprostředkovatele komunikace s objekty** aktivita z **migrace** část **nástrojů** a umístěte jej do **pořadí** aktivity.  
  
15. Klikněte na tlačítko **zprostředkovatele komunikace s objekty** aktivity **klikněte na tlačítko Procházet...** Popisek, zadejte **DiscountCalculator** v **název typu** pole a klikněte na tlačítko **OK**.  
  
    > [!NOTE]
    >  Když <xref:System.Activities.Statements.Interop> je aktivita přidána do pracovního postupu a `DiscountCalculator` type je zadaný jako jeho <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> aktivita poskytuje tři <xref:System.Activities.ArgumentDirection.In> argumenty a tři <xref:System.Activities.ArgumentDirection.Out> argumenty, které představují tři public vlastnosti `DiscountCalculator` aktivity. <xref:System.Activities.ArgumentDirection.In> Argumentů mají stejný název jako tři veřejné vlastnosti a tři <xref:System.Activities.ArgumentDirection.Out> argumentů mají stejné názvy s **si** připojeným k názvu vlastnosti. V následujících krocích argumenty pracovní postup vytvořený v předchozích krocích jsou vázány na <xref:System.Activities.Statements.Interop> argumenty aktivity.  
  
16. Typ `DiscountPercent` do **zadejte výraz jazyka VB.** napravo od pole **DiscountPercentOut** vlastnosti a stiskněte klávesu TAB.  
  
17. Typ `Subtotal` do **zadejte výraz jazyka VB.** napravo od pole **Mezisoučet** vlastnosti a stiskněte klávesu TAB.  
  
18. Typ `Total` do **zadejte výraz jazyka VB.** napravo od pole **TotalOut** vlastnosti a stiskněte klávesu TAB.  
  
19. Klikněte pravým tlačítkem na **Program.cs** v **Průzkumníka řešení** a vyberte **zobrazit kód**.  
  
20. Přidejte následující `using` příkazu v horní části souboru.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Odkomentujte volání `CalculateDiscountInCode` metodu `Main` metoda a přidejte následující kód.  
  
    > [!NOTE]
    >  Pokud jste neřídil předchozího postupu a výchozí `Main` kód je k dispozici, nahradí obsah `Main` následujícím kódem.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Vytvoření nové metody v `Program` třídu s názvem `CalculateDiscountUsingDesignerWorkflow` , který obsahuje následující kód.  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci. Pokud chcete zadat jinou `Subtotal` amount, změňte hodnotu vlastnosti `SubtotalValue` v následujícím kódu.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Přehled funkcí pravidla  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Stroj pravidel poskytuje podporu pro zpracování pravidel na základě priority způsobem s podporou pro řetězení vpřed. Pravidla může být vyhodnocen pro jednu položku nebo položky v kolekci. Přehled pravidel a informace o funkcích konkrétními pravidly najdete v následující tabulce.  
  
|Funkce pravidel|Dokumentace|  
|-------------------|-------------------|  
|Přehled pravidel|[Úvod do pravidla modul Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|Sady pravidel|[Použití sady pravidel v pracovních postupech](https://go.microsoft.com/fwlink/?LinkId=178516) a <xref:System.Workflow.Activities.Rules.RuleSet>|  
|Vyhodnocení pravidel|[Vyhodnocení pravidla v sady pravidel](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|Pravidla řetězení|[Vpřed řetězení ovládací prvek](https://go.microsoft.com/fwlink/?LinkId=178518) a [vpřed řetězení pravidel](https://go.microsoft.com/fwlink/?LinkId=178519)|  
|Zpracování kolekce pravidel|[Zpracování kolekce pravidel](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|Pomocí aktivitě PolicyActivity|[Použití aktivity aktivitě PolicyActivity](https://go.microsoft.com/fwlink/?LinkId=178521) a <xref:System.Workflow.Activities.PolicyActivity>|  
  
 Pracovní postupy vytvořené v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nepoužívejte všechna pravidla funkcí poskytovaných službou [!INCLUDE[wf1](../../../includes/wf1-md.md)], jako je například deklarativní aktivita podmínky a podmíněné aktivity, jako <xref:System.Workflow.Activities.ConditionedActivityGroup> a <xref:System.Workflow.Activities.ReplicatorActivity>. Pokud je to nutné, tato funkce je dostupná pro pracovní postupy vytvořené pomocí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Další informace najdete v tématu [pokyny k migraci](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
