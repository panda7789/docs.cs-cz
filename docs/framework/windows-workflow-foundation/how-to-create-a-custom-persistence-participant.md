---
title: "Postupy: vytvoření vlastního účastník"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e76c08586d45e09359b74d9c8cacdccef6f1ad13
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Postupy: vytvoření vlastního účastník
Následující postup obsahuje kroky k vytvoření účastník trvalost. Najdete v článku [účastní trvalost](http://go.microsoft.com/fwlink/?LinkID=177735) ukázka a [rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) téma pro ukázkové implementace trvalost účastníky.  
  
1.  Vytvořte třídu odvozování z <xref:System.Activities.Persistence.PersistenceParticipant> nebo <xref:System.Activities.Persistence.PersistenceIOParticipant> třídy. Třída PersistenceIOParticipant nabízí stejné body rozšiřitelnosti jako třída PersistenceParticipant kromě toho mohou podílet vstupně-výstupní operace. Postupujte podle jednoho nebo více z následujících kroků.  
  
2.  Implementace <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metoda. **CollectValues** metoda má dva slovník parametrů, jeden pro ukládání hodnot pro čtení a zápis a dalších ten pro ukládání jen pro zápis hodnoty (používá se později v dotazech). Tato metoda by měla naplnění těchto slovníků s daty, která je specifická pro účastníka trvalost. Každý slovník obsahuje název hodnoty jako klíč a hodnotu sám sebe jako <xref:System.Runtime.DurableInstancing.InstanceValue> objektu.  
  
     Hodnoty ve slovníku readWriteValues spojených jako **InstanceValue** objekty. Hodnoty ve slovníku jen pro zápis spojených jako **InstanceValue** objekty sadou InstanceValueOptions.Optional a InstanceValueOption.WriteOnly. Každý **InstanceValue** poskytované **CollectValues** implementace napříč všichni účastníci trvalost musí mít jedinečný název.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implementace <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metoda. **MapValues** metoda přebírá dva parametry, které jsou podobné parametry, **CollectValues** metoda obdrží. Všechny hodnoty shromažďované **CollectValues** fáze se předaly tyto parametry slovníku. S novými hodnotami přidal **MapValues** fáze jsou přidány do jen pro zápis hodnoty.  Slovník jen pro zápis slouží k poskytování dat do externího zdroje není přímo přidružené hodnoty instance. Každá hodnota poskytované implementace **MapValues** metoda napříč všichni účastníci trvalost musí mít jedinečný název.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Metoda poskytuje funkce, <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> nemá, v, aby bylo povoleno pro závislost na jinou hodnotu poskytovanou infrastrukturou jiné trvalost člena, který nebyl zpracován podle <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> ještě.  
  
4.  Implementace **PublishValues** metoda. **PublishValues** metoda přijímá slovník obsahující všechny hodnoty načíst z úložiště trvalosti.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implementace **BeginOnSave** metoda Pokud účastník je účastníkem trvalost vstupně-výstupní operace. Tato metoda je volána v průběhu operace uložit. V této metodě je třeba provést adjunct vstupně-výstupní operace pro uchování (ukládání) instancí pracovních postupů.  Pokud hostitel používá transakce pro příkaz odpovídající trvalost, stejné transakci je součástí Transaction.Current.  Kromě toho může PersistenceIOParticipants inzerovat transakční konzistence požadavek, ve kterém případ hostitele vytvoří transakci pro trvalost díl, pokud by jinak je možné použít.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implementace **BeginOnLoad** metoda Pokud účastník je účastníkem trvalost vstupně-výstupní operace. Tato metoda je volána v průběhu operace načtení. V této metodě je třeba provést adjunct vstupně-výstupní operace pro načítání instance pracovního postupu. Pokud hostitel používá transakce pro příkaz odpovídající trvalost, stejné transakci je součástí Transaction.Current. Kromě toho může trvalost vstupně-výstupní operace účastníky inzerovat transakční konzistence požadavek, ve kterém případ hostitele vytvoří transakci pro trvalost díl, pokud by jinak je možné použít.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
