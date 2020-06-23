---
title: Uvedení prostředků jako účastníků v transakci
description: Zařazení prostředků jako účastníků v transakci .NET. Každý prostředek v transakci je spravován správcem prostředků, který je koordinován správcem transakcí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: c3c777593750b3a4f05ae97ed6e26e19f58e4d72
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141872"
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Uvedení prostředků jako účastníků v transakci

Každý zdroj účasti na transakci spravuje správce prostředků, jejichž akce jsou koordinovaný správcem transakcí. Koordinace se provádí prostřednictvím oznámením na účastníky, kteří mají uveden v transakci prostřednictvím Správce transakcí.

Toto téma popisuje, jak prostředek (nebo více zdrojů) může být uveden v transakci, jakož i různé typy zařazení. [Potvrzení transakce v části s jednou fází a ve více fázích](committing-a-transaction-in-single-phase-and-multi-phase.md) popisuje, jak je možné koordinovat transakci mezi zařazenými prostředky.

## <a name="enlisting-resources-in-a-transaction"></a>Uvedení prostředků v transakci

Chcete-li, aby zdroj k účasti v transakci musí zařadit do transakce. <xref:System.Transactions.Transaction>Třída definuje sadu metod, jejichž názvy začínají na **zařazení** , které tuto funkci poskytují. Různé metody **zařazení** odpovídají různým typům zařazení, které může mít správce prostředků. Konkrétně používají <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody pro těkavých materiály a <xref:System.Transactions.Transaction.EnlistDurable%2A> metody pro trvalý zdroje. Životnost (nebo naopak nestálosti) materiálu manager odkazuje na tom, zda správce prostředků podporuje obnovení po selhání. Pokud správce prostředků podporuje obnovení po selhání, přenese data do trvalého úložiště během fáze 1 (připravit) tak, pokud správce prostředků nebude fungovat, můžete zařadit do transakce při obnovení, znovu a správné činnostem podle oznámení obdržená z správce TM. Obecně platí správci těkavých prostředků spravovat těkavých prostředků, jako jsou například struktury dat v paměti (například v paměti zpracováván jako transakce hashtable) a správci trvalý prostředků spravovat prostředky, které mají více trvalé záložní úložiště (například databáze jehož záložní úložiště je disku).

Pro jednoduchost, jakmile se rozhodnete, zda se má použít <xref:System.Transactions.Transaction.EnlistDurable%2A> nebo <xref:System.Transactions.Transaction.EnlistVolatile%2A> metoda založená na podporu své prostředků životnost, by měl zařazení materiálu k účasti na dvě fáze potvrzení (2PC) implementací <xref:System.Transactions.IEnlistmentNotification> rozhraní pro váš správce prostředků. Další informace o 2PC naleznete v tématu [potvrzení transakce v jedné fázi a několika fázích](committing-a-transaction-in-single-phase-and-multi-phase.md).

Jeden účastník může zařazení pro více než jedním z těchto protokolů voláním <xref:System.Transactions.Transaction.EnlistDurable%2A> a <xref:System.Transactions.Transaction.EnlistVolatile%2A> více než jednou.

### <a name="durable-enlistment"></a>Trvalý zařazení

<xref:System.Transactions.Transaction.EnlistDurable%2A> Metody se používají k zařazení správce prostředků pro účast v transakci jako trvalý prostředek.  Očekává se, že je-li správce prostředků trvalý uprostřed transakcí, lze provádět obnovení poté, co načtením zpět do režimu online podle reenlisting (pomocí <xref:System.Transactions.TransactionManager.Reenlist%2A> metoda) ve všech transakcích, v nichž byl účastník a nebyla dokončena, fáze 2 a volat <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> po dokončení zpracování obnovení. Další informace o obnovení najdete v tématu [provádění obnovení](performing-recovery.md).

<xref:System.Transactions.Transaction.EnlistDurable%2A> Provést všechny metody <xref:System.Guid> objektu jako svůj první parametr. <xref:System.Guid> Slouží správcem transakcí, které pokud chcete přidružit trvalý zařazení správce prostředků konkrétní. Jako takové, je nezbytné, že správce prostředků konzistentně používá stejný <xref:System.Guid> k identifikaci i přes správci různých prostředků při restartování, v opačném případě obnovení může selhat.

Druhý parametr <xref:System.Transactions.Transaction.EnlistDurable%2A> metoda je odkaz na objekt, který implementuje správce prostředků k odběru oznámení transakce. Přetížení, které využíváte informuje správce transakcí, zda váš správce prostředků podporuje optimalizaci jedné fáze potvrzení (SPC). Ve většině případů, měli byste implementovat <xref:System.Transactions.IEnlistmentNotification> rozhraní k účasti na dvoufázový potvrzení (2PC). Nicméně pokud chcete k optimalizaci procesu potvrzení, můžete zvážit implementaci <xref:System.Transactions.ISinglePhaseNotification> rozhraní pro certifikát SPC. Další informace o SPC najdete v tématu [potvrzující transakce v jedné fázi a ve vícenásobné](committing-a-transaction-in-single-phase-and-multi-phase.md) fázi a [optimalizaci pomocí oznámení jedné fáze potvrzení a jediné fáze s jedním fází](optimization-spc-and-promotable-spn.md).

Třetí parametr je <xref:System.Transactions.EnlistmentOptions> výčtu, jehož hodnota může být buď <xref:System.Transactions.EnlistmentOptions.None> nebo <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Pokud hodnota je nastavena <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>, zařazení může zahrnovat správci dalších prostředků při přijetí oznámení připravit z správce transakcí. Nicméně je třeba upozornit na to, že tento typ zařazení není nárok optimalizace jedné fáze potvrzení.

### <a name="volatile-enlistment"></a>Nestálá zařazení

Správa těkavých prostředků, jako je například mezipaměť by měl zařazení pomocí účastníci <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody. Tyto objekty nemusí být možné získat výsledku transakce nebo obnovit stav všech transakcí, které se účastní v po selhání systému.

Jak je uvedeno dříve, správce prostředků by Nestálá zařazení, pokud spravuje v paměti, těkavých zdroj. Jednou z výhod pomocí <xref:System.Transactions.Transaction.EnlistVolatile%2A> je nevede nepotřebné eskalace transakce. Další informace o eskalaci transakce naleznete v tématu [Eskalace správy transakcí](transaction-management-escalation.md) . Zařazení nestálosti předpokládá rozdíl ve způsobu zpracování zařazení správcem transakcí a také to, co se očekává v Resource Manageru správcem transakcí. Toto je vzhledem k tomu, že správce prostředků těkavých neprovádí obnovení. <xref:System.Transactions.Transaction.EnlistVolatile%2A> Metody nepřebírají <xref:System.Guid> parametr, vzhledem k tomu, že správce prostředků těkavých neprovádí obnovení a by volat <xref:System.Transactions.TransactionManager.Reenlist%2A> metodu, kterou je <xref:System.Guid>.

Stejně jako u trvalý zařazení označuje podle toho, která přetížení metody, které použijete k zařazení do správce transakcí zda váš správce prostředků podporuje optimalizaci jedné fáze potvrzení. Vzhledem k tomu, že správce prostředků těkavých nelze provést obnovení, žádné informace o obnovení pro těkavých zařazení během fáze Prepare není zapsán. Proto volání <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> metodu vede <xref:System.InvalidOperationException>.

Následující příklad ukazuje, jak takový objekt jako účastník v transakci pomocí zařazení do seznamu <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody.

[!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
[!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]

### <a name="optimizing-performance"></a>Optimalizace výkonu

<xref:System.Transactions.Transaction> Třída rovněž poskytuje <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu k zařazení možné zařazení pro jedné fáze (PSPE). To umožňuje trvalý prostředku manager (SV) pro hostování a "vlastní" transakce, který lze později eskalován jej lze spravovat pomocí příkaz MSDTC v případě potřeby. Další informace o této části najdete v tématu [optimalizace pomocí potvrzení jedné fáze a jediné fáze s jedním fází](optimization-spc-and-promotable-spn.md).

## <a name="see-also"></a>Viz také

- [Optimalizace pomocí jednofázového potvrzení a možné zařazení jednofázového oznámení](optimization-spc-and-promotable-spn.md)
- [Potvrzení transakce v jedné fázi a více fázích](committing-a-transaction-in-single-phase-and-multi-phase.md)
