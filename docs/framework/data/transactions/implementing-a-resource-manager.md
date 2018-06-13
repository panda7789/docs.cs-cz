---
title: Implementace Resource Manager
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: f3e29dae095fbe56181cf7b67787c1044efa07ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363260"
---
# <a name="implementing-a-resource-manager"></a>Implementace Resource Manager
Každý prostředek, který používá v transakci spravuje správce prostředků, jejichž akce jsou koordinovaný správcem transakcí. Správci prostředků pracují ve spolupráci se správcem transakcí k poskytování aplikací s zárukou atomicitu a izolaci. Microsoft SQL Server, fronty zpráv trvalý, tabulky hodnot hash v paměti jsou všechny příklady správci prostředků.  
  
 Správce prostředků spravuje trvalé nebo přechodné data. Životnost (nebo naopak nestálosti) materiálu manager odkazuje na tom, zda správce prostředků podporuje obnovení po selhání. Pokud správce prostředků podporuje obnovení po selhání, přenese data do trvalého úložiště během fáze 1 (připravit) tak, pokud správce prostředků nebude fungovat, můžete zařadit do transakce při obnovení, znovu a správné činnostem podle oznámení obdržená z správce transakcí. Obecně platí správci těkavých prostředků spravovat těkavých prostředků, jako jsou například struktury dat v paměti (například v paměti zpracováván jako transakce hashtable) a správci trvalý prostředků spravovat prostředky, které mají více trvalé záložní úložiště (například databáze jehož záložní úložiště je disku).  
  
 Chcete-li, aby zdroj k účasti v transakci musí zařadit do transakce. <xref:System.Transactions.Transaction> Třída definuje sadu metod, jejichž názvy začínají řetězcem **Enlist** , zadejte tuto funkci. Různými **Enlist** metody odpovídají na různé typy zařazení, který mohl být správce prostředků. Konkrétně používají <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody pro těkavých materiály a <xref:System.Transactions.Transaction.EnlistDurable%2A> metody pro trvalý zdroje. Pro jednoduchost, jakmile se rozhodnete, zda se má použít <xref:System.Transactions.Transaction.EnlistDurable%2A> nebo <xref:System.Transactions.Transaction.EnlistVolatile%2A> metoda založená na podporu své prostředků životnost, by měl zařazení materiálu k účasti na dvě fáze potvrzení (2PC) implementací <xref:System.Transactions.IEnlistmentNotification> rozhraní pro váš správce prostředků. Další informace o 2PC najdete v tématu [potvrzení transakce v několika fázi a jednofázové](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 Pomocí zapsání správce prostředků zajišťuje, že ji zpětná volání získá ze Správce transakcí při potvrzení nebo přerušení transakce. Existuje jedna instance <xref:System.Transactions.IEnlistmentNotification> za zařazení. Obvykle je jeden zařazení na transakci, ale můžete zvolit správce prostředků k zařazení vícekrát v rámci jedné transakce.  
  
 Po zařazení správce prostředků reaguje na požadavky transakci. Správce prostředků trvalý ukládá dostatek informací, aby mohla vrátit zpět nebo znovu provést transakci práci na prostředky, že spravuje. Existuje mnoho způsobů, jak provést; uchování verzí dat nebo udržování protokolu změn jsou dvě společné techniky.  
  
 Když aplikace potvrdí transakce, správce transakcí spustí protokol dvoufázového potvrzení. Správce transakcí žádá nejprve každého správce prostředků zařazených, pokud je připraven k potvrzení transakce. Správce prostředků musí přípravu k potvrzení akce – ji připravíte sám o potvrzení nebo přerušení transakce.  
  
 Během fáze Příprava správce prostředků trvalý zaznamenává stará a nová data v úložišti stabilní tak, aby správce prostředků můžete obnovit jej i v případě selhání systému. Pokud správce prostředků můžete připravit, informuje správce transakcí jeho hlasovat na tom, zda se potvrzení nebo přerušení transakce. Pokud některý správce prostředků hlásí selhání při přípravě, správce transakcí odešle příkaz vrátit zpět do každého správce prostředků a určuje selhání potvrzení do aplikace.  
  
 Jakmile připraven, musí správce prostředků čekat potvrzení nebo zrušení zpětného volání z správce transakcí ve fázi 2. Obvykle celý protokol prepare a potvrzení dokončí za zlomek sekundy. Pokud dochází k selhání systému nebo komunikace, nemusí přijetí oznámení potvrzení nebo přerušení pro minut nebo hodin. Během této doby je správce prostředků za výsledek transakce. Nemůže určit, zda byla transakce potvrzena nebo bylo přerušeno. Správce prostředků v době vyskytne transakcí, zachová data změněná udržováním transakce zamknuta, a tím izolace tyto změny od všech ostatních transakcí.  
  
 Pokud se nezdaří správce prostředků, jsou všechny její provedení transakcí bylo přerušeno kromě těch, které jsou připravených nebo potvrzených před selhání. Po restartování správce prostředků trvalý rekonstruuje potvrzeny stav prostředků, které spravuje načtením Příprava informací, zapsán ve fázi prepare a potvrzení nebo přerušení tyto transakce odpovídajícím způsobem.  
  
 V souhrnu protokol dvoufázového potvrzení a správci prostředků spojují k provádění transakcí, atomické a trvalý.  
  
 <xref:System.Transactions.Transaction> Třída rovněž poskytuje <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu k zařazení možné zařazení pro jedné fáze (PSPE). To umožňuje trvalý prostředku manager (SV) pro hostování a "vlastní" transakce, který lze později eskalován jej lze spravovat pomocí příkaz MSDTC v případě potřeby. Další informace najdete v tématu [optimalizace pomocí jednoho potvrdit fáze a možné zvýšit jeden oznámení fáze](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 V následujících tématech jsou uvedeny kroky obvykle následuje správce prostředků.  
  
 [Uvedení prostředků jako účastníků v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
  
 Popisuje, jak lze prostředek trvalé nebo přechodné zařazení v transakci.  
  
 [Potvrzení transakce v jedné fázi a více fázích](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Popisuje, jak správce prostředků reaguje na potvrzení oznámení a připravit potvrzení.  
  
 [Provedení obnovení](../../../../docs/framework/data/transactions/performing-recovery.md)  
  
 Popisuje, jak obnoví správce trvalý prostředků z selhání.  
  
 [Úrovně důvěryhodnosti zabezpečení v přístupu k prostředkům](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)  
  
 Popisuje, jak tři úrovně důvěryhodnosti pro System.Transactions omezit přístup k studijních materiálech, které <xref:System.Transactions> zveřejňuje.  
  
 [Optimalizace pomocí jednofázového potvrzení a možné zařazení jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
  
 Popisuje postupy pro optimalizaci implementace správce prostředků k dispozici.
