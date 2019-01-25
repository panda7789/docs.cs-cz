---
title: Stavy objektů a sledování změn
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: 89e9f44a6cd3579a5ef9cc2078609ca26e0d2ae5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683307"
---
# <a name="object-states-and-change-tracking"></a>Stavy objektů a sledování změn
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty vždy účastnit některé *stavu*. Například když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří nový objekt, je objekt v `Unchanged` stavu. Nový objekt, který sami vytvoříte není znám <xref:System.Data.Linq.DataContext> a je v `Untracked` stavu. Po úspěšné provedení <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, všechny objekty, které jsou známé [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] v `Unchanged` stavu. (Jednu výjimku představuje ty, které byla úspěšně odstraněna z databáze, které jsou ve `Deleted` stavu takže nepůjdou použít v tomto <xref:System.Data.Linq.DataContext> instance.)  
  
## <a name="object-states"></a>Stavy objektů  
 V následující tabulce jsou uvedeny možné stavy pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty.  
  
|Stav|Popis|  
|-----------|-----------------|  
|`Untracked`|Objekt není sledován pomocí funkce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Mezi příklady patří následující:<br /><br /> -Není zasílat dotazy prostřednictvím aktuální objekt <xref:System.Data.Linq.DataContext> (například nově vytvořený objekt).<br />-Vytvořených prostřednictvím deserializace objektu<br />-Zasílat dotazy prostřednictvím jiného objektu <xref:System.Data.Linq.DataContext>.|  
|`Unchanged`|Objekt, načíst pomocí aktuálního <xref:System.Data.Linq.DataContext> a není známo, že se změnily, protože byl vytvořen.|  
|`PossiblyModified`|Objekt, který *připojené* k <xref:System.Data.Linq.DataContext>. Další informace najdete v tématu [CUD operace v N-vrstvé aplikace (LINQ to SQL) a načítání dat](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Objekt nelze načíst pomocí aktuálního <xref:System.Data.Linq.DataContext>. To způsobí, že databáze `INSERT` během <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Objekt je známo, že byly změněny od načtení. To způsobí, že databáze `UPDATE` během <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Objekt označený k odstranění, způsobí databázi `DELETE` během <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Objekt, který byl odstraněn v databázi. Tento stav je finální a není povoleno pro další přechody.|  
  
## <a name="inserting-objects"></a>Vkládání objektů  
 Můžete explicitně vyžádat `Inserts` pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternativně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lze odvodit `Inserts` hledáním objekty, které jsou připojené k některé z známé objekty, které se musí aktualizovat. Například, pokud chcete přidat `Untracked` objektu <xref:System.Data.Linq.EntitySet%601> nebo nastavte <xref:System.Data.Linq.EntityRef%601> do `Untracked` objektu, provedete `Untracked` objekt dostupný prostřednictvím sledovaných objektů v grafu. Při zpracování <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projde sledované objekty a vyhledá všechny dostupné trvalé objekty, které nebudou pro účely. Tyto objekty jsou kandidáty pro vložení do databáze.  
  
 Pro třídy v hierarchii dědičnosti <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) nastaví hodnotu člen označený jako *diskriminátoru* tak, aby odpovídaly typu objektu `o`. V případě typ odpovídající výchozí hodnota diskriminátoru tato akce způsobí, že hodnota diskriminátoru přepsat výchozí hodnotu. Další informace najdete v tématu [podpora dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Přidat do objektu `Table` není v mezipaměti identit. Mezipaměti identit odráží, co je načíst pouze z databáze. Po volání <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, přidání entity se nezobrazí v dotazech databázi do <xref:System.Data.Linq.DataContext.SubmitChanges%2A> se úspěšně dokončila.  
  
## <a name="deleting-objects"></a>Odstranění objektů  
 Označit objekt sledované `o` k odstranění voláním <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) na příslušný <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bere v úvahu odebrání objektu z <xref:System.Data.Linq.EntitySet%601> jako aktualizace operace a hodnotě odpovídající cizího klíče nastavena na hodnotu null. Cíl operace (`o`) neodstranil z příslušné tabulky. Například `cust.Orders.DeleteOnSubmit(ord)` označuje aktualizaci kde vztah mezi `cust` a `ord` porušeno nastavením cizí klíč `ord.CustomerID` na hodnotu null. Nezpůsobí odstranění řádku odpovídající `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provádí následující zpracováním, když je objekt odstraněný (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) z jeho tabulky:  
  
-   Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je zavolána, `DELETE` operace pro tento objekt.  
  
-   Pokud chcete odebrání se nerozšíří do bez ohledu na to, zda jsou načteny související objekty. Konkrétně nejsou načteny související objekty pro aktualizaci vlastnost vztahu.  
  
-   Po úspěšném spuštění <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, objekty jsou nastaveny na `Deleted` stavu. V důsledku toho nelze použít objekt nebo jeho `id` v tom, že <xref:System.Data.Linq.DataContext>. Udržuje interní mezipaměť <xref:System.Data.Linq.DataContext> instance nebude odstraněn objekty, které jsou načteny, nebo přidat jako nový, i když se odstranily objekty v databázi.  
  
 Můžete volat <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> jenom u objektu sledován pomocí funkce <xref:System.Data.Linq.DataContext>. Pro `Untracked` objektu, je nutné volat <xref:System.Data.Linq.Table%601.Attach%2A> před voláním <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. Volání <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> na `Untracked` objektu vyvolá výjimku.  
  
> [!NOTE]
>  Odebrání objektu z tabulky říká [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ke generování odpovídající SQL `DELETE` příkaz v době <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Tato akce odebere objekt z mezipaměti ani šíření se odstraňování souvisejících objektů.  
>   
>  Získat zpět `id` odstraněného objektu použít novou <xref:System.Data.Linq.DataContext> instance. Pro čištění souvisejících objektů, můžete použít *kaskádové odstranění* funkce databáze, jinak ručně odstranit související objekty.  
>   
>  Související objekty není nutné odstranit v libovolném pořadí speciální (na rozdíl od v databázi).  
  
## <a name="updating-objects"></a>Aktualizace objektů  
 Můžete zjistit `Updates` pozorováním oznámení změn. Oznámení jsou k dispozici prostřednictvím <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> událost v nastavením vlastností. Když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oznámení o první změně na objekt, vytvoří kopii objektu a považuje za objekt kandidát pro generování `Update` příkaz.  
  
 Pro objekty, které neimplementují <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] neuchovává kopii hodnoty, které objekty měly při prvním vyhodnocena. Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] porovná aktuální a původní hodnoty se rozhodnout, zda byl změněn na objekt.  
  
 Aktualizace relace z podřízený odkaz na nadřazený prvek (tedy odkaz odpovídající cizí klíč) se považuje za oprávnění. Odkaz v opačném směru (to znamená z nadřazené do podřízené) je volitelný. Vztah tříd (<xref:System.Data.Linq.EntitySet%601> a <xref:System.Data.Linq.EntityRef%601>) zaručit, že jsou odkazy obousměrné konzistentní u vztahů jednoho k několika a 1: 1. Je-li objektový model nepoužívá <xref:System.Data.Linq.EntitySet%601> nebo <xref:System.Data.Linq.EntityRef%601>, a pokud je k dispozici zpětné reference, je vaší zodpovědností uchovávat konzistentní s dopředným odkazem při aktualizaci vztahu.  
  
 Při aktualizaci požadovaný odkaz a odpovídající cizí klíč, musí se ujistěte, že souhlasí. <xref:System.InvalidOperationException> Je vyvolána výjimka, pokud nejsou dva synchronizaci v době, kterou je možné volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. I když změny hodnoty cizího klíče jsou dostačující pro ovlivnění aktualizace základní řádky, měli byste změnit odkaz umožňující zachovat připojení objektu grafu a obousměrné konzistence relace.  
  
## <a name="see-also"></a>Viz také:
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Operace vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
