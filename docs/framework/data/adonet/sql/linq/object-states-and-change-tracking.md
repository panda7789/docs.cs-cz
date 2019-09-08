---
title: Stavy objektů a sledování změn
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: a9df200f4d2e5f64bf5883c7bc513ba7129dcaad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781272"
---
# <a name="object-states-and-change-tracking"></a>Stavy objektů a sledování změn

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]objekty se vždycky účastní v některých *stavech*. Například při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytváření nového objektu je objekt ve `Unchanged` stavu. Nový objekt, který sami vytvoříte, není známý pro <xref:System.Data.Linq.DataContext> a je ve `Untracked` stavu. Po úspěšném provedení <xref:System.Data.Linq.DataContext.SubmitChanges%2A>se všechny objekty, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jsou v `Unchanged` tomto stavu, ví. (Jediná výjimka je reprezentovaná prvky, které byly úspěšně odstraněny z databáze, které jsou ve `Deleted` stavu a nepoužitelné v této <xref:System.Data.Linq.DataContext> instanci.)

## <a name="object-states"></a>Stavy objektů

V následující tabulce jsou uvedené možné stavy pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty.

|Stav|Popis|
|-----------|-----------------|
|`Untracked`|Objekt, který není sledován [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástrojem. Mezi příklady patří následující:<br /><br /> – Objekt, na který se nedotazuje <xref:System.Data.Linq.DataContext> pomocí aktuálního (například nově vytvořeného objektu).<br />-Objekt vytvořený prostřednictvím deserializace<br />– Objekt, na který se dotazoval <xref:System.Data.Linq.DataContext>, je jiný.|
|`Unchanged`|Objekt načtený pomocí aktuálního <xref:System.Data.Linq.DataContext> a neznámého objektu byl od vytvoření změněn.|
|`PossiblyModified`|Objekt, který je *připojen* k <xref:System.Data.Linq.DataContext>. Další informace najdete v tématu [načtení dat a operace CUD v N-vrstvých aplikacích (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).|
|`ToBeInserted`|Objekt, který nebyl načten pomocí aktuálního <xref:System.Data.Linq.DataContext>. Tím dojde k vytvoření `INSERT` databáze <xref:System.Data.Linq.DataContext.SubmitChanges%2A>během.|
|`ToBeUpdated`|Objekt, který měl být od načtení změněn. Tím dojde k vytvoření `UPDATE` databáze <xref:System.Data.Linq.DataContext.SubmitChanges%2A>během.|
|`ToBeDeleted`|Objekt označený k odstranění, který způsobuje databázi `DELETE` během. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>|
|`Deleted`|Objekt, který byl odstraněn v databázi. Tento stav je finální a neumožňuje další přechody.|

## <a name="inserting-objects"></a>Vkládání objektů

Můžete explicitně požádat `Inserts` o použití <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. `Inserts` Alternativně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lze odvodit pomocí hledání objektů připojených k jednomu ze známých objektů, které je třeba aktualizovat. Například `Untracked` Pokud přidáte `Untracked` objekt <xref:System.Data.Linq.EntitySet%601> do <xref:System.Data.Linq.EntityRef%601> objektu`Untracked` nebo nastavíte objekt, provedete ho pomocí sledovaných objektů v grafu. Při zpracování <xref:System.Data.Linq.DataContext.SubmitChanges%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projde sledované objekty a zjistí všechny dostupné trvalé trvalé objekty, které nejsou sledovány. Tyto objekty jsou kandidáty na vložení do databáze.

Pro <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>třídy v hierarchii dědičnosti (`o`) také nastaví hodnotu člena určenou jako *diskriminátor* tak, aby odpovídala typu objektu `o`. V případě typu, který odpovídá výchozí hodnotě diskriminátoru, tato akce způsobí přepsání hodnoty diskriminátoru výchozí hodnotou. Další informace najdete v tématu [Podpora dědičnosti](inheritance-support.md).

> [!IMPORTANT]
> Objekt přidaný do `Table` není v mezipaměti identit. Mezipaměť identity odráží pouze to, co je načteno z databáze. Po volání <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>se přidaná entita nezobrazí v dotazech na databázi, dokud <xref:System.Data.Linq.DataContext.SubmitChanges%2A> není úspěšně dokončena.

## <a name="deleting-objects"></a>Odstraňování objektů

Sledovaný objekt `o` můžete označit k odstranění voláním <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) na příslušné <xref:System.Data.Linq.Table%601>straně. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]považuje odebrání objektu <xref:System.Data.Linq.EntitySet%601> za operaci aktualizace a odpovídající hodnota cizího klíče je nastavena na hodnotu null. Cíl operace (`o`) není ze své tabulky odstraněn. Například `cust.Orders.DeleteOnSubmit(ord)` označuje aktualizaci, kde je relace mezi `cust` a `ord` vážně narušena nastavením cizího klíče `ord.CustomerID` na hodnotu null. Nezpůsobí odstranění řádku odpovídajícího `ord`.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]provádí následující zpracování, když je objekt odstraněn (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) z tabulky:

- Při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volání`DELETE` funkce je provedena operace pro tento objekt.

- Odebrání není rozšířeno na související objekty bez ohledu na to, zda jsou načteny. Konkrétně nejsou načteny související objekty pro aktualizaci vlastnosti Relationship.

- Po úspěšném provedení <xref:System.Data.Linq.DataContext.SubmitChanges%2A>se objekty nastaví `Deleted` do stavu. V důsledku toho nemůžete použít objekt nebo jeho `id` v. <xref:System.Data.Linq.DataContext> Interní mezipaměť udržované <xref:System.Data.Linq.DataContext> instancí neeliminuje objekty, které jsou načteny nebo přidány jako nové, i po odstranění objektů v databázi.

Můžete zavolat <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> pouze na objekt, který je <xref:System.Data.Linq.DataContext>sledován. V případě <xref:System.Data.Linq.Table%601.Attach%2A> <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>objektu je nutné volat před voláním. `Untracked` Volání <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>objektuvyvolávýjimku `Untracked` .

> [!NOTE]
> Při odebrání objektu z tabulky [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se vygeneruje odpovídající <xref:System.Data.Linq.DataContext.SubmitChanges%2A>příkaz SQL `DELETE` v čase. Tato akce neodebere objekt z mezipaměti ani nerozšíří odstranění do souvisejících objektů.
>
> Chcete-li uvolnit `id` odstraněný objekt, použijte novou <xref:System.Data.Linq.DataContext> instanci. Pro vyčištění souvisejících objektů můžete použít funkci *kaskádového odstranění* databáze nebo odstranit související objekty ručně.
>
> Související objekty není nutné odstraňovat v žádném speciálním pořadí (na rozdíl od databáze).

## <a name="updating-objects"></a>Aktualizace objektů

Můžete zjistit `Updates` pozorováním oznámení změn. Oznámení jsou k dispozici <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> prostřednictvím události v rámci setter vlastností. Když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je upozorněn na první změnu objektu, vytvoří kopii objektu a vezme objekt jako kandidát pro `Update` vygenerování příkazu.

U objektů, které <xref:System.ComponentModel.INotifyPropertyChanging>neimplementují [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , uchovává kopii hodnot, které měly objekty v době, kdy byly vyhodnoceny jako první. Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>porovná [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aktuální a původní hodnoty a určí, zda byl objekt změněn.

Pro aktualizace vztahů je odkaz z podřízeného objektu na nadřazený (tj. odkaz odpovídající cizímu klíči) považován za autoritu. Odkaz v opačném směru (tj. z nadřazené položky na podřízený) je volitelný. Třídy vztahů (<xref:System.Data.Linq.EntitySet%601> a <xref:System.Data.Linq.EntityRef%601>) zaručují, že obousměrné odkazy jsou konzistentní pro relace 1: n a 1:1. Pokud objektový model nepoužívá <xref:System.Data.Linq.EntitySet%601> nebo <xref:System.Data.Linq.EntityRef%601>a je-li k dispozici zpětný odkaz, je vaše zodpovědnost za to, že při aktualizaci vztahu zůstane v souladu s dopředným odkazem.

Pokud aktualizujete požadovaný odkaz i odpovídající cizí klíč, musíte se ujistit, že souhlasí. Výjimka je vyvolána, pokud tyto dvě nejsou synchronizovány v době volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. <xref:System.InvalidOperationException> I když jsou změny hodnoty cizího klíče dostačující pro ovlivnění aktualizace podkladového řádku, měli byste změnit odkaz na zachování připojení grafu objektů a obousměrné konzistence vztahů.

## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
- [Operace vložení, aktualizace a odstranění](insert-update-and-delete-operations.md)
