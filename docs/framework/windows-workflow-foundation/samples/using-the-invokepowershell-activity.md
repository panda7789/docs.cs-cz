---
title: Použití aktivity InvokePowerShell
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595276"
---
# <a name="using-the-invokepowershell-activity"></a>Použití aktivity InvokePowerShell
Ukázka InvokePowerShell ukazuje, jak vyvolat pomocí příkazů prostředí Windows PowerShell `InvokePowerShell` aktivity.  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Jednoduché inovace z příkazů prostředí Windows PowerShell.  
  
-   Načtení hodnot z výstupu kanálu Windows Powershellu a uložit je do proměnné pracovního postupu.  
  
-   Předejte data do windows Powershellu jako vstupní kanál pro provádění příkazu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka obsahuje následující tři projekty.  
  
|Název projektu|Popis|Hlavní soubory|  
|------------------|-----------------|----------------|  
|CodedClient|Ukázková klientská aplikace, která používá aktivitu prostředí PowerShell.|-   **Soubor program.cs**: prostřednictvím kódu programu pracovních postupů podle pořadí, která volá aktivity InvokePowerShell vytvoří.|  
|DesignerClient|Sadu vlastních aktivit, které obsahují `InvokePowerShell` vlastní aktivity a dalších vedlejších vlastní aktivity a pracovní postup, který je využívá.|<ul><li>Aktivity:<br /><br /> <ul><li>**PrintCollection.cs**: aktivitu pomocné rutiny, která vytiskne všechny položky v kolekci do konzoly.</li><li>**ReadLine.cs**: aktivita pomocné rutiny pro čtení vstupu z konzoly.</li></ul></li><li>Systém souborů:<br /><br /> <ul><li>**Copy.XAML**: aktivitu, která zkopíruje soubor.</li><li>**CreateFile.xaml**: aktivitu, která vytvoří soubor.</li><li>**DeleteFile.xaml**: aktivitu, která odstraní soubor.</li><li>**MakeDir.xaml**: aktivitu, která vytvoří adresář.</li><li>**Move.XAML**: aktivitu, která se přesune do souboru.</li><li>**ReadFile.xaml**: aktivitu, která načte soubor a vrátí jeho obsah.</li><li>**TestPath.xaml**: aktivitu, která otestuje existenci cestu.</li></ul></li><li>Proces:<br /><br /> <ul><li>**GetProcess.xaml**: aktivitu, která načte seznam spuštěných procesů.</li><li>**StopProcess.xaml**: aktivitu, která zastaví konkrétní proces.</li></ul></li><li>**Soubor program.cs**: volá Sequence1 pracovního postupu.</li><li>**Sequence1.XAML**: pracovních postupů založených na pořadí.</li></ul>|  
|PowerShell|`InvokePowerShell` Aktivita a její přidružené designeru.|Soubory aktivit<br /><br /> -   **ExecutePowerShell.cs**: logika hlavní spuštění aktivity.<br />-   **InvokePowerShell.cs**: obálku kolem logika hlavní spuštění, který obsahuje obecný (návratová hodnota) verze a verze neobecnou (bez návratová hodnota). Toto je veřejné rozhraní pro aktivitu.<br />-   **NoPersistZone.cs**: Tato aktivita zabraňuje uchování všechny podřízené aktivity. Tato třída se používá v rámci `InvokePowerShell` implementace aktivitu do aktivity brání trvalý uprostřed zpracování.<br /><br /> Soubory návrháře:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: dialogové okno A Windows, který umožňuje uživateli upravit argumentů `InvokePowerShell` aktivity.<br />2.  **GenericInvokePowerShellDesigner.xaml** a **GenericInvokePowerShellDesigner.xaml.cs**: definuje vzhled elementů Obecné `InvokePowerShell` aktivity v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** a **InvokePowerShellDesigner.cs**: definuje vzhled elementů neobecné `InvokePowerShell` aktivity v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Klientské projekty jsou popsány nejprve, jak je lze snáze pochopit vnitřní funkce Powershellu aktivity po jeho použití je srozumitelný.  
  
## <a name="using-this-sample"></a>Pomocí této ukázky  
 Následující části popisují způsob použití tří projektů v ukázce.  
  
### <a name="using-the-coded-client-project"></a>Pomocí programového klientský projekt  
 Klient ukázka vytvoří prostřednictvím kódu programu sekvenční aktivitu, která obsahuje příklady použití několika různých metod `InvokePowerShell` aktivity. Před prvním vyvoláním spustí program Poznámkový blok.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 Druhé volání získá seznam procesů spuštěných na místním počítači.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` slouží k uložení výstupu příkazu proměnné.  
  
 Další volání ukazuje, jak spustit krok následného zpracování na každé jednotlivé výstupu při vyvolání prostředí PowerShell. `InitializationAction` je nastaven na funkce, jejichž výstupem jsou řetězcovou reprezentaci pro každý proces. V je vrácena kolekci z těchto řetězců `Output` proměnnou `InvokePowerShell<string>` aktivity.  
  
 Následných `InvokePowerShell` volání ukazují předání dat do aktivity a výstupů a chyby navýšení kapacity.  
  
### <a name="using-the-designer-client-project"></a>Pomocí návrháře klientský projekt  
 Projekt DesignerClient sestává ze sady vlastních aktivit, téměř všechny z nich jsou sestaveny obsahující `InvokePowerShell` aktivity. Většina aktivit volání obecné verzi `InvokePowerShell` aktivitu a ne očekávají, že návratová hodnota. Další aktivity použít obecné verzi `InvokePowerShell` aktivity a použití `InitializationAction` argument následného zpracování výsledků.  
  
## <a name="using-the-powershell-project"></a>Pomocí prostředí PowerShell projektu  
 Hlavní akce aktivity probíhá `ExecutePowerShell` třídy. Protože spouštění příkazů prostředí PowerShell by neměla blokovat vlákno hlavní pracovního postupu, vytvoří se aktivity být asynchronní aktivita děděním z <xref:System.Activities.AsyncCodeActivity> třídy.  
  
 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Metoda je volána modulem runtime pracovního postupu zahájíte spuštění aktivity. Spustí voláním rozhraní API prostředí PowerShell k vytvoření kanálu prostředí PowerShell.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 Potom příkaz prostředí PowerShell vytvoří a naplní s parametry a proměnné.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 Vstupy směrované v se také odesílají do kanálu v tomto okamžiku. Nakonec je obalen kanálu `PipelineInvokerAsyncResult` objekt a vrátí. `PipelineInvokerAsyncResult` Objekt zaregistruje naslouchací proces a vyvolá kanál.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Po dokončení provádění výstup a chyby jsou uloženy v rámci stejného `PipelineInvokerAsyncResult` objektu a ovládací prvek bude předán zpět do modulu runtime pracovního postupu zavoláním metody zpětného volání původně předána <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 Na konci metody provedení volání modulu runtime pracovního postupu aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody.  
  
 `InvokePowerShell` Třídy zalomí `ExecutePowerShellCommand` třídy a vytvoří dvě verze aktivity; obecné verzi a obecné verze. Verze neobecnou vrátí její výstup spouštění prostředí PowerShell přímo, zatímco transformuje jednotlivé výsledky obecného typu Obecné verze.  
  
 Obecné verzi aktivity je implementovaný jako sekvenční pracovní postup, který volá `ExecutePowerShellCommand` a následného zpracovává jeho výsledky. Pro každý prvek v kolekci výsledek volání krok následného zpracování `InitializationAction` Pokud je nastavena. V opačném případě provádí jednoduché přetypování.  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 Pro každý z nich `InvokePowerShell` aktivity (obecných a neobecných), návrháře byl vytvořen. InvokePowerShellDesigner.xaml a její přidružené .cs souboru definujte vzhled v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] obecné verzi `InvokePowerShell` aktivity. Uvnitř InvokePowerShellDesigner.xaml <xref:System.Windows.Controls.DockPanel> se používá k reprezentování grafické rozhraní.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Všimněte si, že `Text` vlastnosti textového pole je obousměrnou vazbu, která zajistí, že hodnota aktivity `CommandText` vlastnost je ekvivalentní hodnotu vstupu do návrháře.  
  
 GenericInvokePowerShellDesigner.xaml a její přidružené .cs soubor definují grafické rozhraní pro obecné `InvokePowerShell` aktivity. Návrhář je o něco složitější, protože umožňuje uživatelům nastavit `InitializationAction`. Je klíčovým prvkem použití <xref:System.Activities.Presentation.WorkflowItemPresenter> povolení přetažení myší podřízených aktivit do `InvokePowerShell` návrhové ploše.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 Přizpůsobení řešení pro banku návrháře, ale nezastaví se soubory .xaml, které definují vzhled aktivity na plátno s návrhem. Dialogová okna slouží k zobrazení parametry aktivity se taky dají upravit. Tyto parametry a proměnné prostředí PowerShell ovlivňují chování příkazů Powershellu. Aktivita poskytuje jako <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` typy. ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml a PropertyEditorResources.cs definovat dialogovém okně, které slouží k úpravě těchto typů.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
 Je nutné nainstalovat prostředí Windows PowerShell pro tuto ukázku spustit. Prostředí Windows PowerShell můžete nainstalovat z tohoto umístění: [prostředí Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Spustit programový klienta  
  
1.  Otevřít pomocí PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Klikněte pravým tlačítkem na řešení a sestavte ho.  
  
3.  Klikněte pravým tlačítkem myši **CodedClient** projektu a vyberte **nastavit jako spouštěný projekt**.  
  
4.  Stisknutím kláves CTRL + F5 spusťte aplikaci.  
  
#### <a name="to-run-the-designer-client"></a>Ke spuštění návrháře klienta  
  
1.  Otevřít pomocí PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Klikněte pravým tlačítkem na řešení a sestavte ho.  
  
3.  Klikněte pravým tlačítkem myši **DesignerClient** projektu a vyberte **nastavit jako spouštěný projekt**.  
  
4.  Stisknutím kláves CTRL + F5 spusťte aplikaci.  
  
## <a name="known-issues"></a>Známé problémy  
  
1.  Pokud odkazující `InvokePowerShell` sestavení aktivit nebo z jiného projektu výsledkem chyba sestavení projektu, budete muset ručně přidat `<SpecificVersion>True</SpecificVersion>` elementu do nového projektu v rámci řádku, který odkazuje na soubor .csproj `InvokePowerShell`.  
  
2.  Pokud není nainstalováno prostředí Windows PowerShell, tato chybová zpráva se zobrazí v sadě Visual Studio, jakmile přidáte `InvokePowerShell` aktivitu do pracovního postupu: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  V rozhraní Windows PowerShell 2.0, programově volá `$input.MoveNext()` selže a skriptů pomocí `$input.MoveNext()` neúmyslným chybám a výsledky. Chcete-li tento problém obejít, zvažte použití příkaz prostředí PowerShell `foreach` namísto volání metody `MoveNext()` při iteraci pole.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`