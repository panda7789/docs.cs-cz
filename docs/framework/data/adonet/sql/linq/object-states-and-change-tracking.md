---
title: "Stavy objektů a sledování změn"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f7eb1a8afe87caece18432c66a8d8a268ce9fbd2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="object-states-and-change-tracking"></a>Stavy objektů a sledování změn
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]objekty vždy účastnit některé *stavu*. Například když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří nový objekt, objekt je ve `Unchanged` stavu. Nový objekt, který sami vytvoříte nezná <xref:System.Data.Linq.DataContext> a je v `Untracked` stavu. Po úspěšné provedení <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, všechny objekty, které zná [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] v `Unchanged` stavu. (Jednu výjimku představuje ty, které byla úspěšně odstraněna z databáze, které jsou v `Deleted` stavu a nelze jej použít v tom, že <xref:System.Data.Linq.DataContext> instance.)  
  
## <a name="object-states"></a>Stavy objektů  
 Následující tabulka uvádí možné stavy pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty.  
  
|Stav|Popis|  
|-----------|-----------------|  
|`Untracked`|Objekt není sledován pomocí funkce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Příklady zahrnují následující:<br /><br /> -Není zasílat dotazy prostřednictvím aktuální objekt <xref:System.Data.Linq.DataContext> (například nově vytvořený objekt).<br />-Vytvořena prostřednictvím deserializace objektu<br />-Objekt zasílat dotazy prostřednictvím jiné <xref:System.Data.Linq.DataContext>.|  
|`Unchanged`|Objekt, načíst s použitím aktuální <xref:System.Data.Linq.DataContext> a není známý upraven, protože byla vytvořena.|  
|`PossiblyModified`|Objekt, který je *připojené* k <xref:System.Data.Linq.DataContext>. Další informace najdete v tématu [operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načítání dat ze](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Objekt není načíst s použitím aktuální <xref:System.Data.Linq.DataContext>. To způsobí, že databáze `INSERT` během <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Objekt ví, že byly změněny od byla načtena. To způsobí, že databáze `UPDATE` během <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Objekt označena pro odstranění, způsobuje databázi `DELETE` během <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Objekt, který byl odstraněn v databázi. Tento stav je poslední a nepovoluje Další přechody.|  
  
## <a name="inserting-objects"></a>Vkládání objektů  
 Můžete explicitně vyžádat `Inserts` pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternativně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lze odvodit `Inserts` podle hledání objektů, které jsou připojené k jednomu známé objektů, které se musí aktualizovat. Například, pokud přidáte `Untracked` do objektu <xref:System.Data.Linq.EntitySet%601> nebo nastavte <xref:System.Data.Linq.EntityRef%601> k `Untracked` objektu, provedete `Untracked` objekt dostupný prostřednictvím sledovaných objektů v grafu. Při zpracování <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prochází sledovaných objektů a zjišťuje dosažitelný trvalé objekty, které nejsou sledovat. Tyto objekty jsou kandidáty pro vložení do databáze.  
  
 Pro třídy v hierarchii dědičnosti <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) také nastaví hodnotu člena určený jako *diskriminátoru* tak, aby odpovídaly typ objektu `o`. V případě typ odpovídající výchozí hodnota diskriminátoru tato akce způsobí, že hodnota diskriminátoru ji přepsat výchozí hodnotu. Další informace najdete v tématu [dědičnosti podporu](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Přidat do objektu `Table` není v mezipaměti identity. Mezipaměti identity odráží pouze co je načtena z databáze. Po volání <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, přidané entity se nezobrazí v dotazech v databázi, dokud <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je úspěšně dokončen.  
  
## <a name="deleting-objects"></a>Odstraňování objektů  
 Označit objekt sledovaných `o` k odstranění voláním <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(e) na odpovídající <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zvažuje odebrání objektu ze <xref:System.Data.Linq.EntitySet%601> jako aktualizace operace a hodnotě odpovídající cizího klíče nastavena na hodnotu null. Cíl operace (`o`) není odstraněný z její tabulkou. Například `cust.Orders.DeleteOnSubmit(ord)` označuje aktualizaci kde vztah mezi `cust` a `ord` je porušeno nastavením cizí klíč `ord.CustomerID` na hodnotu null. Nedojde k odstranění řádku odpovídající `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]provádí následující zpracováním, když je odstraněn objekt (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) z jeho tabulky:  
  
-   Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána, `DELETE` operace pro tento objekt.  
  
-   Odebrání není rozšířen na související objekty bez ohledu na to, zda jsou načteny. Konkrétně souvisejících objektů, které nebyly načteny pro aktualizaci vlastnost vztahu.  
  
-   Po úspěšném spuštění <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, objekty jsou nastaveny na `Deleted` stavu. V důsledku toho nelze použít objekt nebo jeho `id` v tom, že <xref:System.Data.Linq.DataContext>. Vnitřní mezipaměti udržované <xref:System.Data.Linq.DataContext> instance nebude odstraněn objekty, které jsou načteny, nebo přidat jako nový, i když byly odstraněny objekty v databázi.  
  
 Můžete volat <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> pouze na objekt sledovanými <xref:System.Data.Linq.DataContext>. Pro `Untracked` objektu, musí volat <xref:System.Data.Linq.Table%601.Attach%2A> před voláním <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. Volání metody <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> na `Untracked` objekt vyvolá výjimku.  
  
> [!NOTE]
>  Odebírání objektů z tabulky informuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generovat odpovídající SQL `DELETE` příkaz v době <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Tato akce není odebrat objekt z mezipaměti nebo rozšířit odstranění související objekty.  
>   
>  Abyste získali zpět `id` odstraněného objektu, použijte nové <xref:System.Data.Linq.DataContext> instance. Pro čištění souvisejících objektů, můžete použít *kaskádové odstranění* funkci databáze, nebo s jiným ručně odstranit související objekty.  
>   
>  Souvisejících objektů, které nemusí být odstraněn v libovolném pořadí speciální (na rozdíl od v databázi).  
  
## <a name="updating-objects"></a>Aktualizace objektů  
 Můžete zjistit `Updates` pomocí sledování oznámení změny. Oznámení jsou k dispozici prostřednictvím <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> událost v nastavením vlastností. Když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je upozornění na změnu první do objektu, vytvoří kopii objektu a považuje za objekt kandidátem pro generování `Update` příkaz.  
  
 Pro objekty, které neimplementují <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] udržuje kopii hodnoty, které objekty měly při byly nejprve materializována. Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] porovná aktuální a původní hodnoty se rozhodnout, zda objekt byl změněn.  
  
 Vztahy aktualizace považuje odkaz z podřízených na nadřazené (to znamená, odkaz odpovídající cizí klíč) oprávnění. Odkaz v opačném směru (který je z nadřazené do podřízené) je volitelný. Třídy vztahu (<xref:System.Data.Linq.EntitySet%601> a <xref:System.Data.Linq.EntityRef%601>) zaručit, že obousměrného odkazy jsou konzistentní pro relace 1 n a 1: 1. Pokud model objektu nepoužívá <xref:System.Data.Linq.EntitySet%601> nebo <xref:System.Data.Linq.EntityRef%601>, a pokud se nachází reverzní odkaz, je vaší povinností zachování jejich konzistence s odkazem na dopředného při aktualizaci vztahu.  
  
 Pokud aktualizujete odkaz na požadované a odpovídající cizí klíč, musí se ujistěte, že souhlasí. <xref:System.InvalidOperationException> Je vyvolána výjimka, pokud dva nejsou synchronizované v době, kterou je možné volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. I když hodnota cizího klíče změny jsou dostatečné pro které mají vliv na aktualizace základní řádku, měli byste změnit odkaz na umožňující zachovat připojení objekt grafu a obousměrné konzistence relace.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Operace vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
