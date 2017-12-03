---
title: "Pomocí zprostředkovatele komunikace s objekty aktivity v pracovním postupu rozhraní .NET Framework 4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa8bb873ed42d5ba717359f420855b605cbe423d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Pomocí zprostředkovatele komunikace s objekty aktivity v pracovním postupu rozhraní .NET Framework 4
Aktivity vytvořené pomocí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nebo [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] mohou být používány [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovní postup pomocí <xref:System.Activities.Statements.Interop> aktivity. Toto téma obsahuje základní informace o použití <xref:System.Activities.Statements.Interop> aktivity.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Aktivita se nezobrazí v panelu nástrojů Návrháře pracovního postupu nezadáte pracovního postupu projekt má svůj **cílové rozhraní** nastavení **rozhraní .net Framework 4** nebo novější.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Pomocí zprostředkovatele komunikace s objekty aktivity v pracovních postupech rozhraní .NET Framework 4.5  
 V tomto tématu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] knihovna aktivit je vytvořen, který obsahuje `DiscountCalculator` aktivity. `DiscountCalculator` Vypočítá slevu na základě množství nákupu a skládá se z <xref:System.Workflow.Activities.SequenceActivity> obsahující <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Používá aktivita vytvořená v tomto tématu <xref:System.Workflow.Activities.PolicyActivity> implementovat logiku aktivity. Je není potřeba použít vlastní [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivity nebo <xref:System.Activities.Statements.Interop> aktivitu, chcete-li použít pravidla v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Příklad použití pravidel v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu bez použití <xref:System.Activities.Statements.Interop> aktivity, najdete v článku [činnost zásad v rozhraní .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) ukázka.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Vytvoření projektu knihovny aktivit rozhraní .NET Framework 3.5  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a vyberte **nový** a potom **projektu...** z **souboru** nabídky.  
  
2.  Rozbalte položku **jiné typy projektů** uzlu **nainstalovaných šablonách** panelu a vyberte **řešení sady Visual Studio**.  
  
3.  Vyberte **prázdného řešení** z **řešení sady Visual Studio** seznamu. Typ `PolicyInteropDemo` v **název** pole a klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **PolicyInteropDemo** v **Průzkumníku řešení** a vyberte **přidat** a potom **nový projekt...** .  
  
    > [!TIP]
    >  Pokud **Průzkumníku řešení** okno není viditelná, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
5.  V **nainstalovaných šablonách** seznamu, vyberte **Visual C#** a potom **pracovního postupu**. Vyberte **rozhraní .NET Framework 3.5** z rozhraní .NET Framework verze rozevíracího seznamu a pak vyberte **knihovny aktivit pracovních postupů** z **šablony** seznamu.  
  
6.  Typ `PolicyActivityLibrary` v **název** pole a klikněte na tlačítko **OK**.  
  
7.  Klikněte pravým tlačítkem na **Activity1.cs** v **Průzkumníku řešení** a vyberte **odstranit**. Klikněte na tlačítko **OK** k potvrzení.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Chcete-li vytvořit DiscountCalculator aktivity  
  
1.  Klikněte pravým tlačítkem na **PolicyActivityLibrary** v **Průzkumníku řešení** a vyberte **přidat** a potom **aktivity...** .  
  
2.  Vyberte **aktivity (s odděleným kódem)** z **Visual C# položky** seznamu. Typ `DiscountCalculator` v **název** pole a klikněte na tlačítko **OK**.  
  
3.  Klikněte pravým tlačítkem na **DiscountCalculator.xoml** v **Průzkumníku řešení** a vyberte **kód zobrazení**.  
  
4.  Přidejte následující tři vlastnosti, které chcete `DiscountCalculator` třídy.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Klikněte pravým tlačítkem na **DiscountCalculator.xoml** v **Průzkumníku řešení** a vyberte **Návrhář zobrazení**.  
  
6.  Přetažení **zásad** aktivity z **v3.0 Windows Workflow** části **sada nástrojů** a umístěte jej do **DiscountCalculator** aktivity .  
  
    > [!TIP]
    >  Pokud **sada nástrojů** okno není viditelná, vyberte **sada nástrojů** z **zobrazení** nabídky.  
  
#### <a name="to-configure-the-rules"></a>Pro konfiguraci pravidel  
  
1.  Klikněte na nově přidaný **zásad** aktivity vyberte, pokud již není vybrána.  
  
2.  Klikněte na tlačítko **RuleSetReference** vlastnost **vlastnosti** okna vyberte ho a klikněte na tlačítko se třemi tečkami napravo od vlastnost.  
  
    > [!TIP]
    >  Pokud **vlastnosti** okno není viditelná, vyberte **vlastnosti – okno** z **zobrazení** nabídky.  
  
3.  Vyberte **klikněte na tlačítko Nový...** .  
  
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
  
14. Klikněte na tlačítko **OK** zavřete **Editor nastavit pravidla** dialogové okno.  
  
15. Zajistěte, aby nově vytvořené <xref:System.Workflow.Activities.Rules.RuleSet> vybrán **název** seznamu a klikněte na tlačítko **OK**.  
  
16. Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
 Pravidla přidán do `DiscountCalculator` aktivity v tomto postupu jsou uvedeny v následujícím příkladu kódu.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Když <xref:System.Workflow.Activities.PolicyActivity> provede tyto tři pravidla vyhodnotit a upravit `Subtotal`, `DiscountPercent`, a `Total` hodnot vlastností `DiscountCalculator` aktivity k výpočtu požadované slevy.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Aktivita DiscountCalculator pomocí zprostředkovatele komunikace s objekty aktivity  
 Použít `DiscountCalculator` aktivity uvnitř [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu, <xref:System.Activities.Statements.Interop> aktivita se používá. V této části dva pracovní postupy jsou vytvářeny, jeden pomocí kódu a pomocí návrháře pracovních postupů, které ukazují, jak používat <xref:System.Activities.Statements.Interop> aktivitu `DiscountCalculator` aktivity. Stejné hostitelské aplikace se používá pro obě pracovních postupů.  
  
#### <a name="to-create-the-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci  
  
1.  Klikněte pravým tlačítkem na **PolicyInteropDemo** v **Průzkumníku řešení** a vyberte **přidat**a potom **nový projekt...** .  
  
2.  Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework a vyberte **pracovního postupu konzolové aplikace** z **Visual C# položky** seznamu.  
  
3.  Typ `PolicyInteropHost` do **název** pole a klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníku řešení** a vyberte **vlastnosti**.  
  
5.  V **cílové rozhraní** rozevíracího seznamu, změňte výběr z **rozhraní .NET Framework 4 Client Profile** k **rozhraní .NET Framework 4.5**. Klikněte na tlačítko **Ano** k potvrzení.  
  
6.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníku řešení** a vyberte **přidat odkaz na...** .  
  
7.  Vyberte **PolicyActivityLibrary** z **projekty** a klikněte na **OK**.  
  
8.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníku řešení** a vyberte **přidat odkaz na...** .  
  
9. Vyberte **System.Workflow.Activities**, **System.Workflow.ComponentModel**a potom **System.Workflow.Runtime** z **.NET**a klikněte na **OK**.  
  
10. Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníku řešení** a vyberte **nastavit jako spouštěný projekt**.  
  
11. Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
### <a name="using-the-interop-activity-in-code"></a>Pomocí zprostředkovatele komunikace s objekty aktivity v kódu  
 V tomto příkladu se vytvoří pomocí kódu, který obsahuje definici pracovního postupu <xref:System.Activities.Statements.Interop> aktivity a `DiscountCalculator` aktivity. Tento pracovní postup je vyvolána pomocí <xref:System.Activities.WorkflowInvoker> a výsledky vyhodnocení pravidla se zapisují do pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Pomocí zprostředkovatele komunikace s objekty aktivity v kódu  
  
1.  Klikněte pravým tlačítkem na **Program.cs** v **Průzkumníku řešení** a vyberte **kód zobrazení**.  
  
2.  Přidejte následující `using` příkaz v horní části souboru.  
  
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
  
4.  Vytvoření nové metody v `Program` třídu s názvem `CalculateDiscountUsingCodeWorkflow` obsahující následující kód.  
  
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
    >  `Subtotal`, `DiscountPercent`, A `Total` vlastnosti `DiscountCalculator` aktivity jsou prezentované jako argumenty <xref:System.Activities.Statements.Interop> aktivity a proměnných vázaná na místní pracovní postup ve <xref:System.Activities.Statements.Interop> aktivity <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekce. `Subtotal`je přidána jako <xref:System.Activities.ArgumentDirection.In> argument protože `Subtotal` tok dat do <xref:System.Activities.Statements.Interop> aktivitu, a `DiscountPercent` a `Total` jsou přidány jako <xref:System.Activities.ArgumentDirection.Out> argumenty vzhledem k tomu, že jejich data proudí mimo <xref:System.Activities.Statements.Interop> aktivity. Všimněte si, že dva <xref:System.Activities.ArgumentDirection.Out> argumenty jsou přidány s názvy `DiscountPercentOut` a `TotalOut` k označení, že představují <xref:System.Activities.ArgumentDirection.Out> argumenty. `DiscountCalculator` Typ určený jako <xref:System.Activities.Statements.Interop> aktivity <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Stisknutím klávesy CTRL + F5 sestavení a spuštění aplikace. Nahraďte různé hodnoty pro `Subtotal` hodnotu k otestování úrovní záznamu do různých slevu poskytované `DiscountCalculator` aktivity.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Pomocí zprostředkovatele komunikace s objekty aktivity v Návrháři pracovních postupů  
 V tomto příkladu je pracovní postup vytvořený pomocí návrháře pracovních postupů. Tento pracovní postup má stejnou funkci jako předchozí příklad, s výjimkou než místo použití <xref:System.Activities.Statements.WriteLine> aktivita se má zobrazit slevu hostitelskou aplikaci načte a zobrazí informace o tomto slevu při dokončení pracovního postupu. Nepoužívejte proměnné místní pracovního postupu tak, aby obsahovala data také argumenty jsou vytvořené v Návrháři pracovních postupů a jsou hodnoty předané z hostitele při vyvolání pracovního postupu.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>K hostování aktivitě PolicyActivity pomocí návrháře pracovních postupů vytvořit pracovní postup  
  
1.  Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníku řešení** a vyberte **odstranit**. Klikněte na tlačítko **OK** k potvrzení.  
  
2.  Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku...** .  
  
3.  Rozbalte **Visual C# položky** uzel a vyberte možnost **pracovního postupu**. Vyberte **aktivity** z **Visual C# položky** seznamu.  
  
4.  Typ `DiscountWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
5.  Klikněte na tlačítko **argumenty** tlačítko na spodní levou stranu Návrháře pracovního postupu pro zobrazení **argumenty** podokně.  
  
6.  Klikněte na tlačítko **vytvořit Argument**.  
  
7.  Typ `Subtotal` do **název** vyberte **v** z **směr** rozevíracího seznamu, vyberte **dvojité** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER pro uložení argument.  
  
    > [!NOTE]
    >  Pokud **dvojité** se nepoužívá **typ argumentu** rozevíracího seznamu vyberte **Procházet pro typy...** , typ `System.Double` v **název typu** pole a klikněte na tlačítko **OK**.  
  
8.  Klikněte na tlačítko **vytvořit Argument**.  
  
9. Typ `DiscountPercent` do **název** vyberte **Out** z **směr** rozevíracího seznamu, vyberte **dvojité** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER pro uložení argument.  
  
10. Klikněte na tlačítko **vytvořit Argument**.  
  
11. Typ `Total` do **název** vyberte **Out** z **směr** rozevíracího seznamu, vyberte **dvojité** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER pro uložení argument.  
  
12. Klikněte **argumenty** tlačítko v levém dolním rohu zavřete návrháře pracovních postupů **argumenty** podokně.  
  
13. Přetažení **pořadí** aktivity z **tok řízení** části **sada nástrojů** na plochu návrháře pracovního postupu.  
  
14. Přetáhněte **zprostředkovatel komunikace s objekty** aktivity z **migrace** části **sada nástrojů** a umístěte jej do **pořadí** aktivity.  
  
15. Klikněte **zprostředkovatel komunikace s objekty** aktivity na **klikněte na tlačítko Procházet...** označení, zadejte **DiscountCalculator** v **název typu** pole a klikněte na tlačítko **OK**.  
  
    > [!NOTE]
    >  Když <xref:System.Activities.Statements.Interop> je přidána do pracovního postupu a `DiscountCalculator` typ určený jako jeho <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> aktivity zpřístupní tři <xref:System.Activities.ArgumentDirection.In> argumenty a tři <xref:System.Activities.ArgumentDirection.Out> argumenty, které představují tři veřejné vlastnosti `DiscountCalculator` aktivity. <xref:System.Activities.ArgumentDirection.In> Argumenty mít stejný název jako tři veřejné vlastnosti a tři <xref:System.Activities.ArgumentDirection.Out> argumenty mají stejné názvy s **Out** připojeným k názvu vlastnosti. V následujících krocích argumenty pracovního postupu vytvořili v předchozích krocích je vázána na <xref:System.Activities.Statements.Interop> argumenty aktivity.  
  
16. Typ `DiscountPercent` do **zadejte výraz VB** pole napravo od **DiscountPercentOut** vlastnost a stiskněte klávesu TAB.  
  
17. Typ `Subtotal` do **zadejte výraz VB** pole napravo od **Mezisoučet** vlastnost a stiskněte klávesu TAB.  
  
18. Typ `Total` do **zadejte výraz VB** pole napravo od **TotalOut** vlastnost a stiskněte klávesu TAB.  
  
19. Klikněte pravým tlačítkem na **Program.cs** v **Průzkumníku řešení** a vyberte **kód zobrazení**.  
  
20. Přidejte následující `using` příkaz v horní části souboru.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Komentář volání `CalculateDiscountInCode` metoda v `Main` metoda a přidejte následující kód.  
  
    > [!NOTE]
    >  Pokud není podle předchozího postupu a ve výchozím nastavení `Main` kód je k dispozici, nahradí obsah `Main` následujícím kódem.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Vytvoření nové metody v `Program` třídu s názvem `CalculateDiscountUsingDesignerWorkflow` obsahující následující kód.  
  
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
  
23. Stisknutím klávesy CTRL + F5 sestavení a spuštění aplikace. Pokud chcete zadat jinou `Subtotal` částka, změňte hodnotu `SubtotalValue` v následujícím kódu.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Přehled funkcí pravidla  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Stroj pravidel poskytuje podporu pro zpracování pravidel s podporou dál řetězení způsobem na základě priority. Pravidla může být vyhodnocen pro jednu položku nebo pro položky v kolekci. Přehled pravidla a informace o funkcích konkrétními pravidly naleznete v následující tabulce.  
  
|Funkce pravidel|Dokumentace|  
|-------------------|-------------------|  
|Přehled pravidel|[Úvod k modulu Windows Workflow Foundation pravidla](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|Sada pravidel pro|[Použití sady pravidel v pracovních postupech](http://go.microsoft.com/fwlink/?LinkId=178516) a<xref:System.Workflow.Activities.Rules.RuleSet>|  
|Vyhodnocení pravidla|[Vyhodnocení pravidla v sady pravidel](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Pravidla řetězení|[Předat dál řetězení řízení](http://go.microsoft.com/fwlink/?LinkId=178518) a [dál řetězení pravidel](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Zpracování kolekce pravidel|[Zpracování kolekce pravidel](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|Pomocí aktivitě PolicyActivity|[Pomocí aktivity aktivitě PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) a<xref:System.Workflow.Activities.PolicyActivity>|  
  
 Pracovní postupy vytvořené v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nepoužívejte všechny pravidla funkce poskytované [!INCLUDE[wf1](../../../includes/wf1-md.md)], jako jsou podmínky deklarativní aktivity a podmíněného aktivity, jako <xref:System.Workflow.Activities.ConditionedActivityGroup> a <xref:System.Workflow.Activities.ReplicatorActivity>. V případě potřeby, tato funkce je dostupná pro pracovní postupy vytvořené pomocí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Migrace pokyny](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
