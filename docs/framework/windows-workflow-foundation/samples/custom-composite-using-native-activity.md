---
title: Vlastní skládání využívající nativní aktivitu
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: bf2b8123619df8977b0687c72663c6b482e35654
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200877"
---
# <a name="custom-composite-using-native-activity"></a>Vlastní skládání využívající nativní aktivitu
Tato ukázka předvádí, jak napsat <xref:System.Activities.NativeActivity> , který plánuje jiné <xref:System.Activities.Activity> objekty pro řízení toku provádění pracovního postupu. Tato ukázka používá dva běžné toky ovládacích prvků, sekvence a while k demonstraci toho, jak to udělat.

## <a name="sample-details"></a>Podrobnosti ukázky
 Počínaje verzí `MySequence` je první věc, kterou je třeba si všimnout, že je odvozena z <xref:System.Activities.NativeActivity> . <xref:System.Activities.NativeActivity>je <xref:System.Activities.Activity> objekt, který zpřístupňuje celou škálu modulu runtime pracovního postupu prostřednictvím <xref:System.Activities.NativeActivityContext> předané `Execute` metody.

 `MySequence`zpřístupňuje veřejnou kolekci <xref:System.Activities.Activity> objektů, které jsou vyplněny autorem pracovního postupu. Před provedením pracovního postupu volá modul runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metodu pro každou aktivitu v pracovním postupu. Během tohoto procesu modul runtime vytváří vztahy mezi nadřazenými a podřízenými daty pro rozsah dat a správu životního cyklu. Výchozí implementace <xref:System.Activities.Activity.CacheMetadata%2A> metody používá <xref:System.ComponentModel.TypeDescriptor> třídu instance pro `MySequence` aktivitu k přidání libovolné veřejné vlastnosti typu <xref:System.Activities.Activity> nebo <xref:System.Collections.IEnumerable> \<<xref:System.Activities.Activity>> jako podřízených objektů `MySequence` aktivity.

 Pokaždé, když aktivita zveřejňuje veřejnou kolekci podřízených aktivit, je pravděpodobný stav sdílení podřízených aktivit. Je osvědčeným postupem pro nadřazenou aktivitu, v tomto případě `MySequence` také k vystavení kolekce proměnných, pomocí kterých mohou podřízené aktivity dosáhnout. Podobně jako podřízené aktivity, <xref:System.Activities.Activity.CacheMetadata%2A> metoda přidává veřejné vlastnosti typu <xref:System.Activities.Variable> nebo <xref:System.Collections.IEnumerable> \<<xref:System.Activities.Variable>> jako proměnné přidružené k `MySequence` aktivitě.

 Kromě veřejných proměnných, které jsou manipulovány podřízenými prvky `MySequence` , `MySequence` musí také sledovat, kde se nachází v provádění jejích podřízených objektů. K tomuto účelu používá soukromou proměnnou `currentIndex` . Tato proměnná je registrována jako součást `MySequence` prostředí přidáním volání <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> metody v rámci `MySequence` <xref:System.Activities.Activity.CacheMetadata%2A> metody aktivity. <xref:System.Activities.Activity>Objekty přidané do `MySequence` `Activities` kolekce nemůžou přistupovat k proměnným přidaným tímto způsobem.

 Pokud `MySequence` je spuštěn modulem runtime, modul runtime volá svou <xref:System.Activities.NativeActivity.Execute%2A> metodu a předává <xref:System.Activities.NativeActivityContext> . <xref:System.Activities.NativeActivityContext>Je objekt proxy aktivity zpátky do modulu runtime pro přesměrování argumentů a proměnných a také plánování jiných <xref:System.Activities.Activity> objektů nebo `ActivityDelegates` . `MySequence`používá `InternalExecute` metodu k zapouzdření logiky plánování prvního podřízeného prvku a všech dalších podřízených objektů v rámci jediné metody. Spustí se pomocí přesměrování `currentIndex` . Pokud se rovná počtu v `Activities` kolekci, pak je sekvence dokončena, aktivita se vrátí bez plánování jakékoli práce a modul runtime je přesune do <xref:System.Activities.ActivityInstanceState.Closed> stavu. Pokud `currentIndex` je menší než počet aktivit, další podřízený objekt získá z `Activities` kolekce a `MySequence` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> , předání podřízeného objektu k naplánování a <xref:System.Activities.CompletionCallback> , který odkazuje na `InternalExecute` metodu. Nakonec se `currentIndex` zvýší a ovládací prvek se vrátí zpět do modulu runtime. Pokud je instance `MySequence` podřízeného <xref:System.Activities.Activity> objektu naplánovaná, modul runtime považuje za spuštěný stav.

 Po dokončení podřízené aktivity se <xref:System.Activities.CompletionCallback> spustí. Smyčka pokračuje od začátku. Podobně jako `Execute` , <xref:System.Activities.CompletionCallback> přebírá a <xref:System.Activities.NativeActivityContext> poskytuje implementátorovi přístup k modulu runtime.

 `MyWhile`se liší od `MySequence` v tom, že opakovaně plánuje jeden <xref:System.Activities.Activity> objekt a v tom, že používá <xref:System.Activities.Activity%601><bool \> s názvem `Condition` k určení, zda toto plánování má nastat. Podobně `MySequence` jako `MyWhile` používá `InternalExecute` Metoda k centralizaci své logiky plánování. Naplánuje `Condition` <xref:System.Activities.Activity><bool \> pomocí <xref:System.Activities.CompletionCallback%601> \<bool> pojmenovaného `OnEvaluationCompleted` . Po `Condition` dokončení provádění je jeho výsledek k dispozici <xref:System.Activities.CompletionCallback> v parametru silného typu s názvem `result` . IF `true` , `MyWhile` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> , předání v `Body` <xref:System.Activities.Activity> objektu a `InternalExecute` jako <xref:System.Activities.CompletionCallback> . Po `Body` dokončení `Condition` Naplánování v systému se znovu `InternalExecute` spustí smyčka. Když `Condition` vrátí `false` instance, `MyWhile` poskytne řízení zpět modulu runtime bez plánování `Body` a modul runtime ho přesune do <xref:System.Activities.ActivityInstanceState.Closed> stavu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete ukázkové řešení kompozitní. sln v aplikaci Visual Studio 2010.

2. Sestavte a spusťte řešení.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
