---
title: "Instance pracovního postupu netrvalé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a7dd9e0ccc29c81426064110eda3e00d2f27b99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="non-persisted-workflow-instances"></a>Instance pracovního postupu netrvalé
Novou instanci pracovního postupu vytvoření která je uchována jeho stav v <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hostitel služby vytvoří záznam pro tuto službu v úložišti instance. Když je následně k instanci pracovního postupu trvalé poprvé, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> uloží aktuální stav instance. Pokud je pracovní postup je hostovaná v aktivační službě procesů systému Windows, data nasazení služby se zapisují také do instance úložiště při první instance.  
  
 Tak dlouho, dokud k instanci pracovního postupu nebyla byla jako trvalé, je v **netrvalé** stavu. V tomto stavu, nelze obnovit instance pracovního postupu po provedení recyklace domény aplikace, selhání hostitele nebo počítače se nezdařilo.  
  
## <a name="the-non-persisted-state"></a>Netrvalého stavu  
 Instance pracovního postupu trvanlivý nezůstanou zůstanou v netrvalého stavu v následujících případech:  
  
-   Hostitel služby spadne, než se k instanci pracovního postupu je trvalá pro první. Instance pracovního postupu zůstává v úložišti instance a není obnoven. Pokud je korelační zpráva doručena, instance pracovního postupu zase aktivní.  
  
-   Instance pracovního postupu dojde k výjimce předtím, než je nastavené jako trvalé poprvé. V závislosti na tom <xref:System.Activities.UnhandledExceptionAction> vrátí, dojde k následující scénáře:  
  
    -   <xref:System.Activities.UnhandledExceptionAction>je nastavena na <xref:System.Activities.UnhandledExceptionAction.Abort>: když dojde k výjimce, informace o nasazení služby je zapsán do instance úložiště a k instanci pracovního postupu je uvolněn z paměti. Instance pracovního postupu zůstane v netrvalého stavu a nelze znovu načíst.  
  
    -   <xref:System.Activities.UnhandledExceptionAction>je nastavena na <xref:System.Activities.UnhandledExceptionAction.Cancel> nebo <xref:System.Activities.UnhandledExceptionAction.Terminate>: když dojde k výjimce, informace o nasazení služby je zapsán do úložiště instance a stav instance aktivity je nastavený na <xref:System.Activities.ActivityInstanceState.Closed>.  
  
 Chcete-li minimalizovat riziko zjištění instance pracovního postupu odpojen netrvalý, doporučujeme setrvání pracovního postupu již v rané fázi v jeho životním cyklu.  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a>Detekce a odebrání netrvalé instancí  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Neodebere všechny instance pracovního postupu netrvalé z obchodu instance. Také neodstraňuje žádné vypršela platnost zámku vlastníky, která mají instance pracovního postupu netrvalé s nimi spojených.  
  
 Doporučujeme, aby správce pravidelně zjišťuje, zda úložiště instance k netrvalé instancí. Tak dlouho, dokud věděli, že tento pracovní postup korelační zprávy nezobrazí, mohou správci odebrat tyto instance z obchodu instance. Například pokud instance byla v databázi několik měsíců a se ví, že pracovní postup má obvykle životnost několik dní, je bezpečné předpokládá, že bylo inicializovaného instanci, která měla došlo k chybě.  
  
 Najít netrvalé instancí v úložišti Instance pracovního postupu SQL můžete použít následující dotazy SQL:  
  
-   Tento dotaz najde všechny instance, které ještě jako trvalé a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   Tento dotaz najde všechny instance, která nezůstanou a které nejsou načíst a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   Tento dotaz najde všechny pozastavené instancí, které ještě jako trvalé a vrátí ID, čas vytvoření (uložené v čase UTC), Důvod pozastavení a název výjimky pro ně.  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 Použijte pozor při odstraňování netrvalé instancí. Obecně je bezpečné odebrání netrvalé instance vytvořené <xref:System.ServiceModel.Activities.WorkflowServiceHost> , jsou pozastavené, nebo se nenačítají. Tyto určité instance můžete odstranit z úložiště odstraněním je z `[System.Activities.DurableInstancing].[Instances]` zobrazení pomocí následujícího příkazu SQL, nahraďte ID správné instance.  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  Odebrání všech instancí netrvalý, protože to zahrnuje instance, které jste právě vytvořili a ještě nezůstanou nedoporučujeme.
