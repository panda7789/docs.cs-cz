---
title: Vlastní skládání využívající nativní aktivitu
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: d9caa6e950af8f800644793db84aa85cc8255914
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528683"
---
# <a name="custom-composite-using-native-activity"></a>Vlastní skládání využívající nativní aktivitu
Tato ukázka předvádí, jak psát <xref:System.Activities.NativeActivity> , která plánuje další <xref:System.Activities.Activity> objekty pro řízení toku provádění pracovního postupu. Tento příklad používá dva běžné toky ovládacího prvku, pořadí a současně přitom, aby ukazují, jak to provést.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Počínaje `MySequence`, je první věc, kterou si všimněte, že se odvozuje od <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> je <xref:System.Activities.Activity> objektu, který poskytuje plnou škálu modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> předán `Execute` metody.  
  
 `MySequence` poskytuje veřejné kolekci <xref:System.Activities.Activity> objekty, které se naplní autorem pracovního postupu. Předtím, než se spustí pracovní postup, volání modulu runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metoda u každé aktivity v pracovním postupu. Během tohoto procesu vytvoří modul runtime vztahů nadřazenosti a podřízenosti pro správu dat na rozsahu a životnosti. Výchozí implementace <xref:System.Activities.Activity.CacheMetadata%2A> metoda používá <xref:System.ComponentModel.TypeDescriptor> instance třídy pro `MySequence` aktivitu, chcete-li přidat všechny veřejné vlastnosti typu <xref:System.Activities.Activity> nebo <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> jako podřízené objekty `MySequence` aktivity.  
  
 Pokaždé, když se aktivita poskytuje kolekci veřejné podřízené aktivity, je pravděpodobné, že sdílení stavu těchto podřízených aktivit. V tomto případě je nejvhodnějším postupem pro Nadřazená aktivita `MySequence`můžete také zveřejnit kolekce proměnných, pomocí kterých podřízených aktivit se dá dosáhnout. Podřízené aktivity, jako jsou <xref:System.Activities.Activity.CacheMetadata%2A> metoda přidá veřejné vlastnosti typu <xref:System.Activities.Variable> nebo <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> jako proměnných spojených s `MySequence` aktivity.  
  
 Kromě veřejné proměnné, které manipulováno jako podřízených prvků `MySequence`, `MySequence` musíte mít také přehled o Pokud je při provádění své podřízené objekty. Používá soukromé proměnné `currentIndex`, jak toho dosáhnout. Tato proměnná je registrovaný jako součást `MySequence` prostředí tak, že přidáte volání <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> metody v rámci `MySequence` aktivity <xref:System.Activities.Activity.CacheMetadata%2A> metody. <xref:System.Activities.Activity> Objekty přidané do `MySequence` `Activities` kolekce nelze přistoupit k proměnným přidat tímto způsobem.  
  
 Když `MySequence` provádí modulem runtime, modul runtime zavolá jeho <xref:System.Activities.NativeActivity.Execute%2A> metodu <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> Je aktivity proxy server zpět do modulu runtime pro zrušení reference proměnné a argumenty, stejně jako ostatní plánování <xref:System.Activities.Activity> objektů, nebo `ActivityDelegates`. `MySequence` používá `InternalExecute` metoda k zapouzdření logiku plánování první podřízený objekt a všechny následné podřízené objekty v jedné metody. Začne tím, že přesměrování `currentIndex`. Pokud se rovná počtu v `Activities` kolekce a pak sekvence dokončí, kterou vrací aktivita bez plánování práce a modul runtime přesouvá ji do <xref:System.Activities.ActivityInstanceState.Closed> stavu. Pokud `currentIndex` je menší než počet aktivit, další podřízené získaných `Activities` kolekce a `MySequence` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>a předejte podřízené k naplánování a <xref:System.Activities.CompletionCallback> , která odkazuje na `InternalExecute` Metoda. Nakonec `currentIndex` je zvýšen a ovládací prvek se vrátil zpět do modulu runtime. Tak dlouho, dokud instance `MySequence` má podřízený element <xref:System.Activities.Activity> objekt naplánované, modul runtime bere v úvahu bude ve stavu zpracování.  
  
 Po dokončení podřízené aktivity <xref:System.Activities.CompletionCallback> provádí. Cyklus pokračuje v horní části. Stejně jako `Execute`, <xref:System.Activities.CompletionCallback> přebírá <xref:System.Activities.NativeActivityContext>, poskytne implementátora přístup k modulu runtime.  
  
 `MyWhile` se liší od `MySequence` v tom, že naplánuje jeden <xref:System.Activities.Activity> objektu opakovaně a, který se použije <xref:System.Activities.Activity%601>< bool\> s názvem `Condition` k určení, zda by dojít k plánování. Stejně jako `MySequence`, `MyWhile` používá `InternalExecute` metoda centralizovat svou logikou plánování. Naplánuje `Condition` <xref:System.Activities.Activity>< bool\> s <xref:System.Activities.CompletionCallback%601> \<bool > s názvem `OnEvaluationCompleted`. Při provádění `Condition` je dokončeno, výsledek bude k dispozici prostřednictvím tohoto <xref:System.Activities.CompletionCallback> v parametr silného typu s názvem `result`. Pokud `true`, `MyWhile` volání <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, předejte `Body` <xref:System.Activities.Activity> objektu a `InternalExecute` jako <xref:System.Activities.CompletionCallback>. Při provádění `Body` dokončení `Condition` získá znovu v naplánované `InternalExecute`, spouští se smyčka znovu. Když `Condition` vrátí `false`, instance `MyWhile` poskytuje řízení zpět do modulu runtime bez plánování `Body` a modul runtime přesouvá ji do <xref:System.Activities.ActivityInstanceState.Closed> stavu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete v ukázkovém řešení Composite.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`