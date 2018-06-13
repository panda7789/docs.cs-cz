---
title: Pomocí aktivity InvokePowerShell
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: c5609556af94ed3e372538047ff6309a105975ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520237"
---
# <a name="using-the-invokepowershell-activity"></a>Pomocí aktivity InvokePowerShell
Ukázka InvokePowerShell ukazuje, jak má být vyvolán pomocí příkazů prostředí Windows PowerShell `InvokePowerShell` aktivity.  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Jednoduché inovací příkazů prostředí Windows PowerShell.  
  
-   Načtení hodnoty z kanálu výstup prostředí Windows PowerShell a uložit je do proměnné pracovního postupu.  
  
-   Jako vstupní kanál provádění příkazu předávání dat do systému windows PowerShell.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Diskusní  
 Tato ukázka obsahuje následující tři projekty.  
  
|Název projektu|Popis|Hlavní soubory|  
|------------------|-----------------|----------------|  
|CodedClient|Ukázkové aplikace klienta, která používá aktivitu prostředí PowerShell.|-   **Program.cs**: prostřednictvím kódu programu vytvoří pracovních postupů založených na pořadí, která volá InvokePowerShell aktivity.|  
|DesignerClient|Sadu vlastních aktivit, které obsahují `InvokePowerShell` vlastní aktivity a dalších různé vlastní aktivity a pracovní postup, který používá je.|<ul><li>Aktivity:<br /><br /> <ul><li>**PrintCollection.cs**: aktivitou pomocné rutiny, která zobrazí všechny položky v kolekci, do konzoly.</li><li>**ReadLine.cs**: Pomocná aktivity pro vstup čtení z konzoly.</li></ul></li><li>Systém souborů:<br /><br /> <ul><li>**Copy.XAML**: aktivitu, která zkopíruje soubor.</li><li>**CreateFile.xaml**: aktivitu, která vytvoří soubor.</li><li>**DeleteFile.xaml**: aktivitu, která odstraní soubor.</li><li>**MakeDir.xaml**: aktivitu, která vytvoří adresář.</li><li>**Move.XAML**: aktivitu, která přesune soubor.</li><li>**ReadFile.xaml**: aktivitu, která načte soubor a vrátí její obsah.</li><li>**TestPath.xaml**: aktivitu, která testů pro existenci cestu.</li></ul></li><li>Proces:<br /><br /> <ul><li>**GetProcess.xaml**: aktivitu, která načte seznam spuštěných procesů.</li><li>**StopProcess.xaml**: aktivitu, která zastaví konkrétní proces.</li></ul></li><li>**Program.cs**: volá Sequence1 pracovní postup.</li><li>**Sequence1.XAML**: pracovních postupů založených na pořadí.</li></ul>|  
|PowerShell|`InvokePowerShell` Aktivita a její přidružené designeru.|Soubory aktivit<br /><br /> -   **ExecutePowerShell.cs**: logiky hlavní provádění aktivity.<br />-   **InvokePowerShell.cs**: obálku kolem logiku hlavní spouštění, která obsahuje obecné (návratová hodnota) verze a verze neobecnou (zpětný hodnota). Toto je veřejné rozhraní pro aktivitu.<br />-   **NoPersistZone.cs**: Tato aktivita brání uložením žádné podřízené aktivity. Tato třída se používá v rámci `InvokePowerShell` aktivity implementace aktivity zabránit trvalé střední provádění.<br /><br /> Návrhář soubory:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: A Windows dialog, který umožňuje uživateli upravit argumentů `InvokePowerShell` aktivity.<br />2.  **GenericInvokePowerShellDesigner.xaml** a **GenericInvokePowerShellDesigner.xaml.cs**: definuje vzhled elementů obecná `InvokePowerShell` aktivity v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** a **InvokePowerShellDesigner.cs**: definuje vzhled elementů neobecnou `InvokePowerShell` aktivity v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Projekty klienta, jsou popsané nejprve, jako je jednodušší zjistit interní funkce prostředí PowerShell aktivity až odhalíte jeho použití.  
  
## <a name="using-this-sample"></a>Pomocí této ukázky  
 Následující části popisují způsob použití tří projektů ve vzorku.  
  
### <a name="using-the-coded-client-project"></a>Pomocí programového klientského projektu  
 Ukázka klient prostřednictvím kódu programu vytvoří pořadí aktivity, který obsahuje příklady několik různých metod, pomocí `InvokePowerShell` aktivity. První volání spustí program Poznámkový blok.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 Druhé volání získá seznam procesů spuštěných v místním počítači.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` slouží k ukládání výstupu příkazu proměnnou.  
  
 Další volání ukazuje, jak následného zpracování krok spustit v každé jednotlivé výstup volání prostředí PowerShell. `InitializationAction` je nastavena na funkce, která vrací řetězcovou reprezentaci jednotlivých procesů. Kolekce tyto řetězce je vrácený v `Output` proměnné pomocí `InvokePowerShell<string>` aktivity.  
  
 Úspěšné `InvokePowerShell` volání ukazují předávání dat do aktivity a získávání výstupy a chyby se.  
  
### <a name="using-the-designer-client-project"></a>Pomocí návrháře klientského projektu  
 Projekt DesignerClient obsahuje sadu vlastních aktivit, téměř všechny z nich jsou vytvořeny obsahující `InvokePowerShell` aktivity. Většina aktivity volejte neobecnou verzi `InvokePowerShell` aktivitu a Nečekejte návratovou hodnotu. Ostatní aktivity použijte obecné verzi `InvokePowerShell` aktivity a použití `InitializationAction` argument po zpracování výsledků.  
  
## <a name="using-the-powershell-project"></a>Pomocí prostředí PowerShell projektu  
 Hlavní akce aktivity probíhá `ExecutePowerShell` třídy. Protože provádění příkazů prostředí PowerShell by neměly blokovat vlákno hlavní pracovní postup, aktivity se vytvoří jako asynchronní aktivitu dědění ze <xref:System.Activities.AsyncCodeActivity> třídy.  
  
 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Metoda je volána modulem runtime pracovního postupu zahájíte běžící aktivity. Spustí voláním rozhraní API prostředí PowerShell vytvořit kanál prostředí PowerShell.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 Potom vytvoří příkaz prostředí PowerShell a naplní s parametry a proměnné.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 Vstupy přesměruje v se odesílá i do kanálu v tomto okamžiku. Nakonec kanálu je uzavřen do `PipelineInvokerAsyncResult` objektu a vrácena. `PipelineInvokerAsyncResult` Objekt zaregistruje naslouchací proces a vyvolá kanál.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Po dokončení provádění výstup a chyby jsou uložené v téže `PipelineInvokerAsyncResult` objektu a řízení je předat zpět do modulu runtime pracovního postupu voláním metody zpětného volání původně předaný <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 Na konci metody provedení volání modulu runtime pracovního postupu aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metoda.  
  
 `InvokePowerShell` Třídy zabalí `ExecutePowerShellCommand` třídy a vytvoří dvě verze aktivity; obecná verze a verze neobecnou. Verze neobecnou výstup spuštění prostředí PowerShell vrátí přímo, kdežto generic verze transformuje jednotlivé výsledky do obecného typu.  
  
 Obecné verzi aktivity je implementovaný jako sekvenční pracovní postup, který volá `ExecutePowerShellCommand` a po jeho výsledky. Pro každý prvek v kolekci výsledek následného zpracování krok volá `InitializationAction` Pokud je nastaveno. Jinak hodnota nemá jednoduchý přetypování.  
  
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
  
 Pro každou z těchto dvou `InvokePowerShell` aktivity (Obecné a neobecné), Návrhář byla vytvořena. InvokePowerShellDesigner.xaml a jeho přidružené .cs souboru definujte vzhled v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] neobecnou verzi `InvokePowerShell` aktivity. Uvnitř InvokePowerShellDesigner.xaml <xref:System.Windows.Controls.DockPanel> se používá k reprezentování grafické rozhraní.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Všimněte si, že `Text` vlastnost textového pole je obousměrný vazbu, která zajistí, že hodnota aktivity `CommandText` vlastnost je ekvivalentní hodnotu vstupem do návrháře.  
  
 GenericInvokePowerShellDesigner.xaml a jeho přidružené .cs souboru definovat grafické rozhraní pro obecné `InvokePowerShell` aktivity. Návrhář je trochu složitější, protože umožňuje uživatelům nastavit `InitializationAction`. Je klíčovým prvkem použití <xref:System.Activities.Presentation.WorkflowItemPresenter> umožňující přetažení a vyřadit podřízené aktivit do `InvokePowerShell` plochu návrháře.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 Návrhář vlastní nastavení se soubory XAML definující vzhled aktivity na plátně návrhu nezastaví. Dialogová okna slouží k zobrazení parametry aktivity lze upravit. Tyto parametry a proměnné prostředí PowerShell ovlivnit chování příkazy prostředí PowerShell. Aktivity zpřístupní je jako <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` typy. ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml a PropertyEditorResources.cs definovat okno, které slouží k úpravě těchto typů.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
 Je nutné nainstalovat prostředí Windows PowerShell pro tuto ukázku spustit. Prostředí Windows PowerShell můžete nainstalovat z tohoto umístění: [prostředí Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Spuštění programových klienta  
  
1.  Otevřete pomocí PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Klikněte pravým tlačítkem na řešení a sestavte jej.  
  
3.  Klikněte pravým tlačítkem myši **CodedClient** projektu a vyberte **nastavit jako spouštěný projekt**.  
  
4.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.  
  
#### <a name="to-run-the-designer-client"></a>Spuštění návrháře klienta  
  
1.  Otevřete pomocí PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Klikněte pravým tlačítkem na řešení a sestavte jej.  
  
3.  Klikněte pravým tlačítkem myši **DesignerClient** projektu a vyberte **nastavit jako spouštěný projekt**.  
  
4.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.  
  
## <a name="known-issues"></a>Známé problémy  
  
1.  Pokud odkazující `InvokePowerShell` sestavení aktivit nebo projekt z jiného projektu za následek chyby sestavení, musíte ručně přidat `<SpecificVersion>True</SpecificVersion>` element do souboru .csproj nový projekt v řádku, který odkazuje na `InvokePowerShell`.  
  
2.  Pokud není nainstalované prostředí Windows PowerShell, se následující chybová zpráva se zobrazí v sadě Visual Studio, jakmile přidáte `InvokePowerShell` aktivitu do pracovního postupu: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  V prostředí Windows PowerShell 2.0, prostřednictvím kódu programu volání `$input.MoveNext()` selže a skriptů pomocí `$input.MoveNext()` vytvořit neočekávaným chybám a výsledky. Chcete-li tento problém obejít, doporučujeme použít příkaz prostředí PowerShell `foreach` místo volání `MoveNext()` během iterace pole.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`