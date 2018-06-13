---
title: Vlastní složené pomocí nativní aktivity
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 78d00a13bdc018946fa20635a47677b1508c1ed1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519207"
---
# <a name="custom-composite-using-native-activity"></a>Vlastní složené pomocí nativní aktivity
Tento příklad ukazuje, jak k zápisu <xref:System.Activities.NativeActivity> , jiné plány <xref:System.Activities.Activity> objekty, které se řídí tok spuštění pracovního postupu. Tato ukázka používá dvě běžné řízení toky, pořadí a při, aby ukazují, jak to udělat.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Počínaje `MySequence`, je nejprve si všimněte si, že je odvozena z <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> je <xref:System.Activities.Activity> objekt, který zveřejňuje úplného spektra modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> předaný `Execute` metoda.  
  
 `MySequence` poskytuje veřejné kolekci <xref:System.Activities.Activity> objekty, které získá naplněny autorem pracovního postupu. Před provedením pracovní postup volá modulu runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metoda na každou aktivitu v pracovním postupu. Během tohoto procesu vytvoří modul runtime vztahů nadřazenosti a podřízenosti pro správu dat na rozsahu a doby platnosti. Výchozí implementaci <xref:System.Activities.Activity.CacheMetadata%2A> metoda používá <xref:System.ComponentModel.TypeDescriptor> instance třídy pro `MySequence` aktivitu přidat všechny veřejné vlastnosti typu <xref:System.Activities.Activity> nebo <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> jako podřízené objekty `MySequence` aktivity.  
  
 Vždy, když aktivita poskytuje veřejné kolekci podřízené aktivity, je pravděpodobné, že tyto aktivity podřízené sdílet stavu. V takovém případě je nejvhodnějším postupem pro nadřazené aktivity `MySequence`, také vystavit kolekci proměnných, pomocí kterých podřízené aktivity se dá dosáhnout. Podřízené aktivity, jako <xref:System.Activities.Activity.CacheMetadata%2A> metoda přidá veřejné vlastnosti typu <xref:System.Activities.Variable> nebo <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> jako proměnné přidružené `MySequence` aktivity.  
  
 Kromě toho veřejné proměnné, které jsou manipulovat podřízené objekty daného `MySequence`, `MySequence` musí také udržovat zaznamenávat, kde je při provádění jeho podřízených položek. Používá soukromé proměnné `currentIndex`, toho chcete dosáhnout. Tato proměnná je zaregistrován v rámci `MySequence` prostředí tak, že přidáte volání <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> metoda v rámci `MySequence` aktivity <xref:System.Activities.Activity.CacheMetadata%2A> metoda. <xref:System.Activities.Activity> Objektů přidaných do `MySequence` `Activities` kolekce nemůže získat přístup k proměnné přidány tímto způsobem.  
  
 Když `MySequence` je provedený modulu runtime volání modulu runtime jeho <xref:System.Activities.NativeActivity.Execute%2A> předávání v případě metody <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> Je aktivity proxy zpět do modulu runtime pro vyhodnocení argumentů a proměnných a také další plánování <xref:System.Activities.Activity> objekty, nebo `ActivityDelegates`. `MySequence` používá `InternalExecute` metoda má být zapouzdřena logiku plánování první podřízený objekt a všechny následné podřízené objekty v jedné metody. Začne tím vyhodnocení `currentIndex`. Pokud se rovná počtu v `Activities` dokončení kolekce a potom toto pořadí aktivita vrátí bez plánování veškerou práci, a modul runtime, přesune ho do <xref:System.Activities.ActivityInstanceState.Closed> stavu. Pokud `currentIndex` je menší než počet aktivit, další podřízené se získávají z `Activities` kolekce a `MySequence` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, předejte v podřízeném k naplánování a <xref:System.Activities.CompletionCallback> který odkazuje na `InternalExecute` Metoda. Nakonec `currentIndex` se zvýší a ovládací prvek, je vhodné zpět do modulu runtime. Stejně dlouho jako instanci `MySequence` má podřízenou <xref:System.Activities.Activity> objekt naplánované, modul runtime považuje ve stavu zpracování.  
  
 Po dokončení podřízené aktivity <xref:System.Activities.CompletionCallback> se spustí. Smyčky pokračuje shora. Jako `Execute`, <xref:System.Activities.CompletionCallback> trvá <xref:System.Activities.NativeActivityContext>, udělíte přístup implementátor modulu runtime.  
  
 `MyWhile` se liší od `MySequence` v tom, že naplánuje jedné <xref:System.Activities.Activity> objektu opakovaně a v tom, že používá <xref:System.Activities.Activity%601>< bool\> s názvem `Condition` k určení, zda tento plánování provedeno. Jako `MySequence`, `MyWhile` používá `InternalExecute` metoda a centralizovat plánování logiky pravidla. Naplánuje `Condition` <xref:System.Activities.Activity>< bool\> s <xref:System.Activities.CompletionCallback%601> \<bool > s názvem `OnEvaluationCompleted`. Při provádění `Condition` je dokončena, její výsledek bude k dispozici prostřednictvím to <xref:System.Activities.CompletionCallback> parametr silného typu s názvem `result`. Pokud `true`, `MyWhile` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>a předejte `Body` <xref:System.Activities.Activity> objektu a `InternalExecute` jako <xref:System.Activities.CompletionCallback>. Při provádění `Body` dokončení `Condition` získá znovu v naplánované `InternalExecute`, spouštění smyčky přes znovu. Při `Condition` vrátí `false`, instanci `MyWhile` nabízí kontrolu zpět do runtime bez plánování `Body` a modul runtime přesouvá ji do <xref:System.Activities.ActivityInstanceState.Closed> stavu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete Composite.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`