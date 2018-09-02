---
title: 'Postupy: vytvoření vlastního účastníka trvalosti'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 8daf4924db48c79486e85660357e3b28a2583836
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422074"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Postupy: vytvoření vlastního účastníka trvalosti
Následující postup obsahuje kroky k vytvoření trvalého účastníka. Najdete v článku [účastní trvalost](https://go.microsoft.com/fwlink/?LinkID=177735) ukázky a [Store rozšíření](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tématu pro ukázková implementace účastníci trvalosti.  
  
1.  Vytvořte třídu odvozenou z <xref:System.Activities.Persistence.PersistenceParticipant> nebo <xref:System.Activities.Persistence.PersistenceIOParticipant> třídy. Třída PersistenceIOParticipant nabízí stejné body rozšiřitelnosti jako třída PersistenceParticipant navíc nebudou moct zúčastnit vstupně-výstupních operací. Postupujte podle jednoho nebo více z následujících kroků.  
  
2.  Implementace <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metody. **CollectValues** metoda má dva slovník parametrů, jeden pro uložení hodnot pro čtení a zápis a druhé pro ukládání jen pro zápis hodnoty (později v dotazech použít). V této metodě měli byste vyvolat tyto adresáře s daty, která je specifická pro trvalého účastníka. Každý slovník obsahuje název hodnoty z klíče a samotná hodnota jako <xref:System.Runtime.DurableInstancing.InstanceValue> objektu.  
  
     Hodnoty ve slovníku readWriteValues jsou dodávány jako **InstanceValue** objekty. Hodnoty ve slovníku jen pro zápis, které jsou dodávány jako **InstanceValue** objekty s nastavenou InstanceValueOptions.Optional a InstanceValueOption.WriteOnly. Každý **InstanceValue** poskytované **CollectValues** implementace napříč všichni účastníci trvalosti musí mít jedinečný název.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implementace <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metody. **MapValues** metoda přebírá dva parametry, které jsou podobně jako parametry, které **CollectValues** metoda obdrží. Všechny hodnoty shromážděné při **CollectValues** fáze se předaly tyto parametry slovníku. Přidá nové hodnoty **MapValues** fázi jsou přidány do hodnoty jen pro zápis.  Slovník jen pro zápis se používá k předání dat do externího zdroje není přímo přidružené hodnoty instance. Každou hodnotu poskytovanou infrastrukturou implementace **MapValues** metoda napříč všichni účastníci trvalosti musí mít jedinečný název.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Metoda poskytuje funkce, která <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> tak není, v tom, že umožňuje pro závislost na jiná hodnota poskytnutá jiným účastníkem trvalého, která nebyla zpracována <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> ještě.  
  
4.  Implementace **PublishValues** metody. **PublishValues** metoda obdrží slovník obsahující všechny hodnoty načíst z trvalého úložiště.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implementace **BeginOnSave** metodu, pokud je účastník účastníka trvalosti vstupně-výstupních operací. Tato metoda je volána při operaci uložit. V této metodě měli byste provést adjunct vstupně-výstupních operací na uchování (instance pracovního postupu ukládání).  Pokud hostitel používá transakce pro příkaz odpovídající trvalost, stejné transakce je k dispozici v Transaction.Current.  Kromě toho může PersistenceIOParticipants inzerovat transakční konzistence požadavek, ve kterém případ hostitele vytvoří transakce pro danou epizodu trvalost, pokud by v opačném případě je možné použít.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implementace **BeginOnLoad** metodu, pokud je účastník účastníka trvalosti vstupně-výstupních operací. Tato metoda je volána při operaci načítání. V této metodě měli byste provést adjunct vstupně-výstupních operací na načtení instance pracovního postupu. Pokud hostitel používá transakce pro příkaz odpovídající trvalost, stejné transakce je k dispozici v Transaction.Current. Kromě toho mohou účastníci trvalosti vstupně-výstupních operací inzerovat transakční konzistence požadavek, ve kterém případ hostitele vytvoří transakce pro danou epizodu trvalost, pokud by v opačném případě je možné použít.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
