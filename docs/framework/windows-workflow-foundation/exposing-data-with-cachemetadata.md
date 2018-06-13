---
title: Vystavení dat s CacheMetadata
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: 386bbb8734e26eff8079f2913284668125a8a774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515249"
---
# <a name="exposing-data-with-cachemetadata"></a>Vystavení dat s CacheMetadata
Před provedením aktivitu, modulu runtime pracovního postupu získá všechny informace o aktivitě, která je nutné, aby byla zachována jeho spuštění. Získá tyto informace při provádění modulu runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metoda. Výchozí implementace této metody poskytuje modul runtime s všechny veřejné argumenty, proměnné a podřízené aktivity vystavené aktivity v době, kdy je se provedla; Pokud aktivita musí poskytnout další informace pro modul runtime než to (například soukromé členy, nebo aktivity plánování pomocí aktivity), k tomu lze přepsat tuto metodu.  
  
## <a name="default-cachemetadata-behavior"></a>Výchozí chování CacheMetadata  
 Výchozí implementaci <xref:System.Activities.NativeActivity.CacheMetadata%2A> pro aktivity, které jsou odvozeny od <xref:System.Activities.NativeActivity> zpracovává následující typy metoda následujícími způsoby:  
  
-   <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, nebo <xref:System.Activities.InOutArgument%601> (obecné argumenty): tyto argumenty jsou zveřejněné modulu runtime jako argumenty s názvem a zadejte rovna zveřejněné vlastnost název a typ, směr odpovídající argument a některá data ověření.  
  
-   <xref:System.Activities.Variable> nebo jakékoli její podtřídou: tito členové jsou viditelné na modulu runtime jako veřejné proměnné.  
  
-   <xref:System.Activities.Activity> nebo jakékoli její podtřídou: tito členové jsou viditelné na modulu runtime jako veřejné podřízené aktivity. Výchozí chování může být implementováno výslovně voláním <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>a předejte podřízené aktivity.  
  
-   <xref:System.Activities.ActivityDelegate> nebo jakékoli její podtřídou: tito členové jsou viditelné na modulu runtime jako veřejné delegáti.  
  
-   <xref:System.Collections.ICollection> typu <xref:System.Activities.Variable>: všechny elementy v kolekci jsou viditelné na modulu runtime jako veřejné proměnné.  
  
-   <xref:System.Collections.ICollection> typu <xref:System.Activities.Activity>: všechny elementy v kolekci jsou viditelné na modulu runtime jako veřejné podřízené objekty.  
  
-   <xref:System.Collections.ICollection> typu <xref:System.Activities.ActivityDelegate>: všechny elementy v kolekci jsou viditelné na modulu runtime jako veřejné delegáti.  
  
 <xref:System.Activities.Activity.CacheMetadata%2A> Pro aktivity, které jsou odvozeny od <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, a <xref:System.Activities.AsyncCodeActivity> také fungovat jako výše, vyjma následujících rozdílů:  
  
-   Třídy, které jsou odvozeny od <xref:System.Activities.Activity> nelze naplánovat podřízené aktivity nebo delegáti, takže tito členové jsou zveřejněné jako importované podřízené objekty a delegáti;  
  
-   Třídy, které jsou odvozeny od <xref:System.Activities.CodeActivity> a <xref:System.Activities.AsyncCodeActivity> nepodporují proměnné, děti nebo delegáti, takže se zveřejní pouze argumenty.  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>Přepsání CacheMetadata poskytovat informace o modulu runtime  
 Následující fragment kódu ukazuje, jak přidat informace o členech do metadat aktivity během provádění <xref:System.Activities.Activity.CacheMetadata%2A> metoda. Všimněte si, že základní metoda je volána pro ukládání do mezipaměti všechny veřejná data o aktivitě.  
  
```  
protected override void CacheMetadata(NativeActivityMetadata metadata)  
{      
    base.CacheMetadata(metadata);  
    metadata.AddImplementationChild(this._writeLine);  
    metadata.AddVariable(this._myVariable);  
    metadata.AddImplementationVariable(this._myImplementationVariable);  
  
    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));  
    metadata.Bind(argument, this.SomeName);  
    metadata.AddArgument(argument);  
}  
```  
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a>Pomocí CacheMetadata vystavit implementace podřízené objekty  
 Chcete-li předat data do podřízené aktivity, které chcete naplánovat aktivitou pomocí proměnných, je potřeba přidat proměnné jako proměnné implementace; veřejné proměnné nemůže mít jejich hodnotami nastavenými tímto způsobem. Důvodem je, že aktivity mají za cíl více provést, protože implementace funkce (která mají parametry), nikoli zapouzdřené třídy (která mají vlastnosti). Existují však situace, ve kterých jsou argumenty musí být explicitně nastaveny, například při použití <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, od naplánovanou činností nemá přístup k nadřazené aktivity argumenty způsobem by podřízené aktivity.  
  
 Následující fragment kódu ukazuje, jak má být předán formuláře argument nativní aktivity naplánované aktivity pomocí <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
```  
public sealed class ChildActivity : NativeActivity  
{  
    public WriteLine _writeLine;  
    public InArgument<string> Message { get; set; }  
    private Variable<string> MessageVariable { get; set; }  
    public ChildActivity()  
    {  
        MessageVariable = new Variable<string>();  
        _writeLine = new WriteLine  
        {  
            Text = new InArgument<string>(MessageVariable),  
        };  
    }  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        metadata.AddImplementationVariable(this.MessageVariable);  
        metadata.AddImplementationChild(this._writeLine);  
    }  
    protected override void Execute(NativeActivityContext context)  
    {  
        string configuredMessage = context.GetValue(Message);  
        context.SetValue(MessageVariable, configuredMessage);  
        context.ScheduleActivity(this._writeLine);  
    }  
}  
```
