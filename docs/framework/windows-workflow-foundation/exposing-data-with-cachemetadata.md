---
title: Zveřejnění dat pomocí CacheMetadata
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945701"
---
# <a name="exposing-data-with-cachemetadata"></a>Zveřejnění dat pomocí CacheMetadata

Před provedením aktivity, modulu runtime pracovního postupu získá všechny informace o aktivitě, která potřebuje, aby byla zachována jeho spuštění. Získá tyto informace při provádění modulu runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metody. Výchozí implementace této metody poskytuje modul runtime se všemi veřejné argumenty, proměnných a podřízené aktivity, které jsou vystavené aktivity v době, kdy je spuštěn; Pokud aktivita musí poskytovat další informace k modulu runtime než to (například soukromé členy nebo aktivity k naplánování aktivita), tato metoda může být potlačena za účelem ho zadat.

## <a name="default-cachemetadata-behavior"></a>Výchozí chování CacheMetadata

Výchozí implementace <xref:System.Activities.NativeActivity.CacheMetadata%2A> pro aktivity, které jsou odvozeny z <xref:System.Activities.NativeActivity> zpracovává následující typy metoda následujícími způsoby:

- <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, nebo <xref:System.Activities.InOutArgument%601> (obecné argumenty): Tyto argumenty jsou vystaveny jako argumenty s názvem modulu runtime a zadejte rovna vystavené název a typ, směr příslušnou argumentem a některá data ověření.

- <xref:System.Activities.Variable> nebo jakékoliv podtřídy jejich: Tyto členy jsou vystaveny pro modul runtime jako veřejné proměnné.

- <xref:System.Activities.Activity> nebo jakékoliv podtřídy jejich: Tyto členy jsou vystaveny pro modul runtime jako veřejné podřízené aktivity. Výchozí chování můžete implementovat explicitně voláním <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>a předejte podřízené aktivity.

- <xref:System.Activities.ActivityDelegate> nebo jakékoliv podtřídy jejich: Tyto členy jsou vystaveny modul runtime jako veřejné delegátů.

- <xref:System.Collections.ICollection> typu <xref:System.Activities.Variable>: Všechny elementy v kolekci jsou vystaveny pro modul runtime jako veřejné proměnné.

- <xref:System.Collections.ICollection> typu <xref:System.Activities.Activity>: Všechny elementy v kolekci jsou vystaveny pro modul runtime jako veřejné podřízené položky.

- <xref:System.Collections.ICollection> typu <xref:System.Activities.ActivityDelegate>: Všechny elementy v kolekci jsou vystaveny modul runtime jako veřejné delegátů.

<xref:System.Activities.Activity.CacheMetadata%2A> Pro aktivity, které jsou odvozeny z <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, a <xref:System.Activities.AsyncCodeActivity> také funkci jak je uvedeno výše, vyjma následujících rozdílů:

- Třídy, které jsou odvozeny z <xref:System.Activities.Activity> nelze naplánovat podřízených aktivit nebo delegátů, tak, aby takové členy jsou vystaveny jako importované podřízené položky a delegáti;

- Třídy, které jsou odvozeny z <xref:System.Activities.CodeActivity> a <xref:System.Activities.AsyncCodeActivity> nepodporují proměnné, podřízené položky nebo delegátů, takže budou přístupné pouze argumenty.

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>Přepsání CacheMetadata poskytnout informace o modulu runtime

Následující fragment kódu ukazuje, jak přidat informace o členech metadat aktivity během provádění <xref:System.Activities.Activity.CacheMetadata%2A> metody. Všimněte si, že základní metoda je volána pro ukládání do mezipaměti všechny veřejné dat o aktivitě.

```csharp
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

## <a name="using-cachemetadata-to-expose-implementation-children"></a>Pomocí CacheMetadata vystavit podřízené položky implementace

Chcete-li předat data do podřízené aktivity, které jsou k naplánování aktivitou pomocí proměnných, je potřeba přidat proměnné jako proměnné implementace; veřejné proměnné nemůžou mít jejich hodnoty nastavit tímto způsobem. Důvodem je, že aktivity mají více provést, protože implementace funkce (které mají parametry), a ne zapouzdřený objekt třídy (které mají vlastnosti). Existují však situace, ve kterých jsou argumenty musí být explicitně nastaveny, například při použití <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, protože naplánované aktivity nemá přístup k Nadřazená aktivita argumentů tak, jak by podřízené aktivity.

Následující fragment kódu ukazuje, jak má být předán formulář argument nativní aktivity naplánované aktivity pomocí <xref:System.Activities.Activity.CacheMetadata%2A>.

```csharp
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
