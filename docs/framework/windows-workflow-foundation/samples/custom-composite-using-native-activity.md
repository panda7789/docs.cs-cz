---
title: Vlastní skládání využívající nativní aktivitu
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 57c724ad55c3aa2960e9a2d11fcd8419a94a0c72
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715172"
---
# <a name="custom-composite-using-native-activity"></a>Vlastní skládání využívající nativní aktivitu
Tato ukázka předvádí, jak napsat <xref:System.Activities.NativeActivity>, který naplánuje ostatní objekty <xref:System.Activities.Activity> k řízení toku provádění pracovního postupu. Tato ukázka používá dva běžné toky ovládacích prvků, sekvence a while k demonstraci toho, jak to udělat.

## <a name="sample-details"></a>Podrobnosti ukázky
 Počínaje `MySequence`, první věc, kterou si všimnete, je, že je odvozená od <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> je objekt <xref:System.Activities.Activity>, který zpřístupňuje celou škálu modulu runtime pracovního postupu prostřednictvím <xref:System.Activities.NativeActivityContext> předaných metodě `Execute`.

 `MySequence` zveřejňuje veřejnou kolekci objektů <xref:System.Activities.Activity>, které jsou vyplněny autorem pracovního postupu. Před provedením pracovního postupu volá modul runtime pracovního postupu metodu <xref:System.Activities.Activity.CacheMetadata%2A> u každé aktivity v pracovním postupu. Během tohoto procesu modul runtime vytváří vztahy mezi nadřazenými a podřízenými daty pro rozsah dat a správu životního cyklu. Výchozí implementace metody <xref:System.Activities.Activity.CacheMetadata%2A> používá třídu <xref:System.ComponentModel.TypeDescriptor> instance pro aktivitu `MySequence` k přidání libovolné veřejné vlastnosti typu <xref:System.Activities.Activity> nebo <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Activity>> jako podřízených objektů aktivity `MySequence`.

 Pokaždé, když aktivita zveřejňuje veřejnou kolekci podřízených aktivit, je pravděpodobný stav sdílení podřízených aktivit. Je osvědčeným postupem pro nadřazenou aktivitu, v tomto případě `MySequence`k vystavení kolekce proměnných, jejichž prostřednictvím mohou podřízené aktivity dosáhnout. Podobně jako podřízené aktivity, <xref:System.Activities.Activity.CacheMetadata%2A> metoda přidává veřejné vlastnosti typu <xref:System.Activities.Variable> nebo <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Variable>> jako proměnné přidružené k aktivitě `MySequence`.

 Kromě veřejných proměnných, které jsou manipulovány podřízenými objekty `MySequence`, `MySequence` musí také sledovat, kde se nachází v provádění jejích podřízených prvků. K tomu slouží privátní proměnná, `currentIndex`. Tato proměnná je registrována jako součást prostředí `MySequence` přidáním volání metody <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> v rámci metody <xref:System.Activities.Activity.CacheMetadata%2A> aktivity `MySequence`. <xref:System.Activities.Activity> objektů přidaných do kolekce `Activities` `MySequence` nelze přistoupit k proměnným, které byly přidány tímto způsobem.

 Při spuštění `MySequence` modulem runtime zavolá modul runtime svou metodu <xref:System.Activities.NativeActivity.Execute%2A> a předá <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> je proxy aktivity zpět do modulu runtime pro přesměrování argumentů a proměnných a také plánování jiných objektů <xref:System.Activities.Activity> nebo `ActivityDelegates`. `MySequence` používá metodu `InternalExecute` k zapouzdření logiky plánování prvního podřízeného prvku a všech dalších podřízených objektů v rámci jediné metody. Začíná přeodkazováním `currentIndex`. Pokud se rovná počtu v kolekci `Activities`, pak je sekvence dokončena, aktivita se vrátí bez naplánování práce a modul runtime je přesune do stavu <xref:System.Activities.ActivityInstanceState.Closed>. Pokud je `currentIndex` menší než počet aktivit, další podřízený objekt získá z kolekce `Activities` a `MySequence` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, předání v podřízeném prvku k naplánování a <xref:System.Activities.CompletionCallback>, který odkazuje na `InternalExecute` metodu. Nakonec se `currentIndex` zvýší a řízení se vrátí zpět do modulu runtime. Pokud má instance `MySequence` podřízený objekt <xref:System.Activities.Activity> naplánovaný, modul runtime považuje za spuštěný stav.

 Po dokončení podřízené aktivity se <xref:System.Activities.CompletionCallback> spustí. Smyčka pokračuje od začátku. Podobně jako `Execute`<xref:System.Activities.CompletionCallback> přebírá <xref:System.Activities.NativeActivityContext>a poskytuje implementátorovi přístup k modulu runtime.

 `MyWhile` se liší od `MySequence` v tom, že opakovaně plánuje jeden <xref:System.Activities.Activity> objekt a v tom, že používá <xref:System.Activities.Activity%601>< bool\> s názvem `Condition` k určení, zda se má toto plánování provést. Podobně jako `MySequence``MyWhile` používá metodu `InternalExecute` k centralizaci své logiky plánování. Naplánuje `Condition`<xref:System.Activities.Activity>< bool\> pomocí <xref:System.Activities.CompletionCallback%601>\<bool > s názvem `OnEvaluationCompleted`. Po dokončení spuštění `Condition` bude jeho výsledek k dispozici prostřednictvím tohoto <xref:System.Activities.CompletionCallback> v parametru silného typu s názvem `result`. Pokud `true`, `MyWhile` volá <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, které přecházejí do objektu `Body`<xref:System.Activities.Activity> a `InternalExecute` jako <xref:System.Activities.CompletionCallback>. Po dokončení spuštění `Body` `Condition` znovu naplánovala v `InternalExecute`. Pokud `Condition` vrátí `false`, instance `MyWhile` poskytuje řízení zpět do modulu runtime bez naplánování `Body` a modul runtime ho přesune do stavu <xref:System.Activities.ActivityInstanceState.Closed>.

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete ukázkové řešení kompozitní. sln v aplikaci Visual Studio 2010.

2. Sestavte a spusťte řešení.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
