---
title: Vlastní skládání využívající nativní aktivitu
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 2b922ef721ab4d125f390e908eb8ea4d3b087035
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142794"
---
# <a name="custom-composite-using-native-activity"></a>Vlastní skládání využívající nativní aktivitu
Tato ukázka ukazuje, <xref:System.Activities.NativeActivity> jak napsat, <xref:System.Activities.Activity> který naplánuje jiné objekty řídit tok provádění pracovního postupu. Tato ukázka používá dva společné toky řízení Sequence a While, chcete-li předvést, jak to provést.

## <a name="sample-details"></a>Podrobnosti ukázky
 Počínaje `MySequence`, první věc, kterou si všimnete, je, že pochází z <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity>je <xref:System.Activities.Activity> objekt, který zveřejňuje celou šířku běhu pracovního postupu prostřednictvím <xref:System.Activities.NativeActivityContext> předán metodě. `Execute`

 `MySequence`zpřístupňuje veřejnou <xref:System.Activities.Activity> kolekci objektů, které získá naplněný autor pracovního postupu. Před spuštěním pracovního postupu zavolá doba <xref:System.Activities.Activity.CacheMetadata%2A> běhu pracovního postupu metodu pro každou aktivitu v pracovním postupu. Během tohoto procesu runtime vytvoří vztahy nadřazený podřízený pro obory dat a správu životnosti. <xref:System.Activities.Activity.CacheMetadata%2A> Výchozí implementace metody používá <xref:System.ComponentModel.TypeDescriptor> třídu instance `MySequence` pro aktivitu k <xref:System.Activities.Activity> přidání <xref:System.Collections.IEnumerable> \< jakékoli veřejné vlastnosti typu nebo <xref:System.Activities.Activity>> jako podřízené objekty aktivity. `MySequence`

 Vždy, když aktivita zveřejňuje veřejnou kolekci podřízených aktivit, je pravděpodobné, že tyto podřízené aktivity sdílejí stav. Je osvědčeným postupem pro nadřazenou aktivitu, v tomto případě `MySequence`také vystavit kolekci proměnných, jejichž prostřednictvím podřízené aktivity můžete provést. Stejně jako <xref:System.Activities.Activity.CacheMetadata%2A> podřízené aktivity, <xref:System.Activities.Variable> <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable> metoda přidá veřejné vlastnosti typu nebo> jako proměnné přidružené k aktivitě. `MySequence`

 Kromě veřejných proměnných, s nimiž `MySequence`děti `MySequence` manipulují , musí také sledovat, kde se nachází při provádění svých dětí. Používá soukromou proměnnou, `currentIndex`, k dosažení tohoto cíle. Tato proměnná je registrována jako `MySequence` součást prostředí <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> přidáním `MySequence` volání <xref:System.Activities.Activity.CacheMetadata%2A> metody v rámci metody aktivity. Objekty <xref:System.Activities.Activity> přidané `MySequence` `Activities` do kolekce nemají přístup k proměnným přidaným tímto způsobem.

 Když `MySequence` je spuštěn a runtime, runtime <xref:System.Activities.NativeActivity.Execute%2A> volá jeho <xref:System.Activities.NativeActivityContext>metodu, předávání v . Je <xref:System.Activities.NativeActivityContext> proxy aktivity zpět do modulu runtime pro dereferencing argumenty <xref:System.Activities.Activity> a proměnné, stejně jako plánování jiných objektů, nebo `ActivityDelegates`. `MySequence`Používá `InternalExecute` metodu k zapouzdření logiky plánování první podřízené a všechny další podřízené v jedné metodě. Začíná odkazováním na `currentIndex`. Pokud se rovná počtu v `Activities` kolekci, pak sekvence je dokončena, aktivita vrátí bez plánování <xref:System.Activities.ActivityInstanceState.Closed> jakékoli práce a modul runtime přesune do stavu. Pokud `currentIndex` je menší než počet aktivit, další dítě `Activities` je `MySequence` získán <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>z kolekce a volání , <xref:System.Activities.CompletionCallback> předávání podřízené `InternalExecute` ho naplánovat a které body na metodu. Nakonec `currentIndex` je přírůstek a ovládací prvek je výnosně zpět do běhu. Tak dlouho, dokud `MySequence` instance <xref:System.Activities.Activity> má podřízený objekt naplánováno, modul runtime považuje za být ve stavu Provádění.

 Po dokončení podřízené aktivity <xref:System.Activities.CompletionCallback> je proveden. Smyčka pokračuje od vrcholu. Like `Execute`, <xref:System.Activities.CompletionCallback> trvá <xref:System.Activities.NativeActivityContext>, dává implementer přístup k běhu.

 `MyWhile`se liší `MySequence` od v tom, <xref:System.Activities.Activity> že plánuje jeden objekt opakovaně <xref:System.Activities.Activity%601> a\> v `Condition` tom, že používá<bool s názvem k určení, zda by mělo dojít k tomuto plánování. Podobně `MySequence` `MyWhile` , `InternalExecute` používá metodu centralizovat jeho plánování logiky. Naplánuje `Condition` <xref:System.Activities.Activity><bool\> s <xref:System.Activities.CompletionCallback%601> \<bool `OnEvaluationCompleted`> s názvem . Po dokončení `Condition` provádění jeho výsledek bude k <xref:System.Activities.CompletionCallback> dispozici prostřednictvím tohoto v `result`silně zadaný parametr s názvem . Pokud `true` `MyWhile` , <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>volání , `Body` <xref:System.Activities.Activity> předávání `InternalExecute` v <xref:System.Activities.CompletionCallback>objektu a jako . Po dokončení `Body` dokončení, `Condition` získá naplánováno `InternalExecute`znovu v , spuštění smyčky znovu. Když `Condition` vrátí `false`, instance `MyWhile` poskytuje řízení zpět do modulu runtime bez `Body` plánování <xref:System.Activities.ActivityInstanceState.Closed> a modul runtime přesune do stavu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete ukázkové řešení Composite.sln v sadě Visual Studio 2010.

2. Sestavte a spusťte řešení.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
