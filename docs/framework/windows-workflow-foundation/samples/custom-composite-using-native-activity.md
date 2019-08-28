---
title: Vlastní skládání využívající nativní aktivitu
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 8a0d1077c058ecdbad10a2e7bd61ff5eb75e1cb5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044312"
---
# <a name="custom-composite-using-native-activity"></a>Vlastní skládání využívající nativní aktivitu
Tato ukázka předvádí <xref:System.Activities.NativeActivity> , jak napsat, který plánuje <xref:System.Activities.Activity> jiné objekty pro řízení toku provádění pracovního postupu. Tato ukázka používá dva běžné toky ovládacích prvků, sekvence a while k demonstraci toho, jak to udělat.

## <a name="sample-details"></a>Podrobnosti ukázky
 Počínaje verzí je první věc, kterou je třeba si všimnout, že je odvozena z <xref:System.Activities.NativeActivity>. `MySequence` <xref:System.Activities.NativeActivity>je objekt, který zpřístupňuje celou škálu modulu runtime pracovního postupu <xref:System.Activities.NativeActivityContext> prostřednictvím předané `Execute` metody. <xref:System.Activities.Activity>

 `MySequence`zpřístupňuje veřejnou kolekci <xref:System.Activities.Activity> objektů, které jsou vyplněny autorem pracovního postupu. Před provedením pracovního postupu volá <xref:System.Activities.Activity.CacheMetadata%2A> modul runtime pracovního postupu metodu pro každou aktivitu v pracovním postupu. Během tohoto procesu modul runtime vytváří vztahy mezi nadřazenými a podřízenými daty pro rozsah dat a správu životního cyklu. Výchozí implementace <xref:System.Activities.Activity.CacheMetadata%2A> metody <xref:System.Collections.IEnumerable> <xref:System.Activities.Activity> <xref:System.Activities.Activity> `MySequence` <xref:System.ComponentModel.TypeDescriptor> používá třídu instance pro aktivitu k přidání libovolné veřejné vlastnosti typu nebo \<> jako podřízené položky `MySequence` aktivita.

 Pokaždé, když aktivita zveřejňuje veřejnou kolekci podřízených aktivit, je pravděpodobný stav sdílení podřízených aktivit. Je osvědčeným postupem pro nadřazenou aktivitu, v tomto případě `MySequence`také k vystavení kolekce proměnných, pomocí kterých mohou podřízené aktivity dosáhnout. Podobně jako podřízené aktivity, <xref:System.Activities.Activity.CacheMetadata%2A> metoda přidává veřejné vlastnosti typu <xref:System.Activities.Variable> nebo <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> jako proměnné přidružené `MySequence` k aktivitě.

 Kromě veřejných proměnných, které jsou manipulovány podřízenými prvky `MySequence`, `MySequence` musí také sledovat, kde se nachází v provádění jejích podřízených objektů. K tomuto účelu používá soukromou `currentIndex`proměnnou. Tato proměnná je `MySequence` registrována jako součást prostředí přidáním volání <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> <xref:System.Activities.Activity.CacheMetadata%2A> metody v rámci `MySequence` metody aktivity. <xref:System.Activities.Activity> Objekty přidané `MySequence` dokolekcenemůžoupřistupovatkproměnnýmpřidaným`Activities` tímto způsobem.

 Pokud `MySequence` je spuštěn modulem runtime, modul runtime volá svou <xref:System.Activities.NativeActivity.Execute%2A> <xref:System.Activities.NativeActivityContext>metodu a předává. Je objekt proxy aktivity zpátky do modulu runtime pro přesměrování argumentů a proměnných a také plánování jiných <xref:System.Activities.Activity> objektů nebo `ActivityDelegates`. <xref:System.Activities.NativeActivityContext> `MySequence``InternalExecute` používá metodu k zapouzdření logiky plánování prvního podřízeného prvku a všech dalších podřízených objektů v rámci jediné metody. Spustí se pomocí přesměrování `currentIndex`. Pokud se rovná počtu v `Activities` kolekci, pak je sekvence dokončena, aktivita se vrátí bez plánování jakékoli práce a modul runtime je přesune <xref:System.Activities.ActivityInstanceState.Closed> do stavu. <xref:System.Activities.CompletionCallback> `MySequence` `Activities` `InternalExecute` <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>Pokud je menší než počet aktivit, další podřízený objekt získá z kolekce a volání, předání podřízeného objektu k naplánování a bodu na `currentIndex` Metoda. `currentIndex` Nakonec se zvýší a ovládací prvek se vrátí zpět do modulu runtime. Pokud je instance `MySequence` podřízeného <xref:System.Activities.Activity> objektu naplánovaná, modul runtime považuje za spuštěný stav.

 Po dokončení <xref:System.Activities.CompletionCallback> podřízené aktivity se spustí. Smyčka pokračuje od začátku. Podobně `Execute`jako <xref:System.Activities.CompletionCallback> , přebírá <xref:System.Activities.NativeActivityContext>a poskytuje implementátorovi přístup k modulu runtime.

 `MyWhile`se liší od `MySequence` v tom, že opakovaně plánuje <xref:System.Activities.Activity> jeden objekt a <xref:System.Activities.Activity%601>v tom, že používá < bool\> s názvem `Condition` k určení, zda toto plánování má nastat. Podobně jako `MySequence` používá`InternalExecute`Metoda k centralizaci své logiky plánování. `MyWhile` Naplánuje `Condition` <xref:System.Activities.Activity>< bool\> s použitím <xref:System.Activities.CompletionCallback%601>bool>s `OnEvaluationCompleted`názvem. \< Po dokončení provádění `Condition` je jeho výsledek k dispozici <xref:System.Activities.CompletionCallback> v parametru silného typu s názvem `result`. IF `true`, `MyWhile` volání<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>,předání v objektua`InternalExecute` jako. `Body` <xref:System.Activities.Activity> <xref:System.Activities.CompletionCallback> Po `Body` `InternalExecute`dokončení `Condition` naplánování v systému se znovu spustí smyčka. `Condition` Když vrátí `false`instance, poskytne řízení zpět modulu runtime bez plánování <xref:System.Activities.ActivityInstanceState.Closed> amodulruntimehopřesunedostavu.`Body` `MyWhile`

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete ukázkové řešení kompozitní. sln v aplikaci Visual Studio 2010.

2. Sestavte a spusťte řešení.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
