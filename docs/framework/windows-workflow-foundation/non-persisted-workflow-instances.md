---
title: Netrvalé instance pracovních postupů
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 2f28e7b44f951151b47a6424670e5101960e91eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649343"
---
# <a name="non-persisted-workflow-instances"></a>Netrvalé instance pracovních postupů
Když pracovního postupu je vytvořena nová instance, která udržuje svůj stav v <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hostitel služby vytvoří záznam pro tuto službu v úložišti instancí. Následně, když instance pracovního postupu trvala poprvé, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> uloží aktuální stav instance. Pokud pracovní postup je hostovaný v aktivační službě procesů Windows, data nasazení služby se zapisují také do úložiště instancí při instance je trvale uložena poprvé.  
  
 Za předpokladu, instance pracovního postupu ještě nebyla trvale uložena, je v **netrvalé** stavu. V tomto stavu nelze obnovit instance pracovního postupu po provedení recyklace domény aplikace, selhání hostitele nebo selhání počítače.  
  
## <a name="the-non-persisted-state"></a>-Trvalý stav  
 Instance trvalý pracovních postupů, které ještě nebyla trvale uložena zůstanou ve stavu netrvalé v následujících případech:  
  
- Hostitel služby spadne, než se instance pracovního postupu je trvalý poprvé. Instance pracovního postupu zůstává v úložišti instancí a není obnoven. Pokud je korelační přijetí e-mailu, instance pracovního postupu aktivují znovu.  
  
- Instance pracovního postupu dojde k výjimce předtím, než je umístěný prvním. V závislosti na tom <xref:System.Activities.UnhandledExceptionAction> vrátila, dojde k následující scénáře:  
  
    - <xref:System.Activities.UnhandledExceptionAction> je nastavena na <xref:System.Activities.UnhandledExceptionAction.Abort>: Když dojde k výjimce, informace o nasazení služby se zapisují do úložiště instancí a instance pracovního postupu je uvolněn z paměti. Zůstane ve stavu netrvalé instance pracovního postupu a nelze znovu načíst.  
  
    - <xref:System.Activities.UnhandledExceptionAction> je nastavena na <xref:System.Activities.UnhandledExceptionAction.Cancel> nebo <xref:System.Activities.UnhandledExceptionAction.Terminate>: Když dojde k výjimce, informace o nasazení služby se zapisují do úložiště instancí a instance stav aktivity je nastavený na <xref:System.Activities.ActivityInstanceState.Closed>.  
  
 Chcete-li minimalizovat riziko vzniku pracovní postup uvolněn netrvalé instance, doporučujeme uchování pracovního postupu v rané fázi svého životního cyklu.  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a>Rozpoznání a odstranění netrvalé instance  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Neodebere všechny instance pracovního postupu netrvalé instance storu. Všechny vlastníky vypršela platnost zámku, které mají pracovní postup netrvalé instance k nim má přiřazené také nezpůsobí odebrání.  
  
 Doporučujeme vám, že správce pravidelně kontroluje úložiště instance k netrvalé instance. Za předpokladu, ví, že tento pracovní postup neobdrží korelovaných zpráv, mohou správci odebrat tyto instance ze v úložišti instancí. Například pokud instance v databázi na několik měsíců, a je známo, že pracovní postup má obvykle životnost několik dní, by se dá předpokládat, že bylo inicializované instance, který měl došlo k chybě.  
  
 Najít netrvalé instance v Store Instance pracovního postupu SQL můžete použít následující dotazy SQL:  
  
- Tento dotaz najde všechny instance, která ještě nebyla trvale uložena a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
- Tento dotaz najde všechny instance, která ještě nebyla trvale uložena, a, které nejsou načtené a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
- Tento dotaz najde všechny pozastavené instance, která ještě nebyla trvale uložena a vrátí ID, čas vytvoření (uložené v čase UTC), pozastavení a název výjimky pro ně.  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 Při odstraňování netrvalé instance, použijte pozornost. Obecně je bezpečně odebrat netrvalé instance vytvořené <xref:System.ServiceModel.Activities.WorkflowServiceHost> , které jsou pozastavené, nebo se nenačítají. Tyto konkrétní instance můžete odstranit z úložiště tak, že odstraníte je z `[System.Activities.DurableInstancing].[Instances]` s použitím následujícího příkazu SQL, nahraďte ID instance správný.  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  Nedoporučujeme odebrání všech netrvalé instance, protože to zahrnuje instance, které jste právě vytvořili a ještě nebyla trvale uložena.
