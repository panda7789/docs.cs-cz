---
title: Optimalizace pomocí jednofázového potvrzení a možné zařazení jednofázového oznámení
description: Optimalizujte výkon pomocí jediné fáze potvrzení a oznámení s jednou fází. Přečtěte si o infrastruktuře System. Transactions v .NET.
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: 89ce82e673340c93254983c078f78a2501129383
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141975"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Optimalizace pomocí jednofázového potvrzení a možné zařazení jednofázového oznámení

Toto téma popisuje mechanismy poskytované <xref:System.Transactions> infrastruktury za účelem optimalizace výkonu.

## <a name="promotable-single-phase-enlistment"></a>Zařazení možné jedna fáze

<xref:System.Transactions> Infrastruktury administrates transakcí v rámci jedné aplikační domény, který zahrnuje maximálně jeden prostředek trvalý nebo více těkavých zdrojů. Vzhledem k tomu <xref:System.Transactions> infrastruktura používá volání pouze uvnitř aplikační domény, bude vrácen nejlepší propustnost a výkonu.

Nicméně, pokud transakce je k dispozici na jiný objekt v jiné doméně aplikace (včetně přes hranice procesu a strojově), ve stejném počítači, nebo pokud jste byli k zařazení jiného správce prostředků trvalý, <xref:System.Transactions> infrastruktury automaticky eskaluje transakce jej lze spravovat pomocí příkaz MSDTC. Spravuje MSDTC transakcí není jako jedna spravuje performance-wise <xref:System.Transactions> infrastruktury.

Za účelem optimalizace výkonu, <xref:System.Transactions> možné jedné fáze zařazení (PSPE) umožňující na jeden vzdálený trvalý prostředek umístěný v různých aplikační domény, procesu nebo počítač, abyste se mohli účastnit v poskytuje infrastrukturu <xref:System.Transactions> transakce, aniž by ji chcete-li být rozšířena na transakci MSDTC. Tento správce prostředků (SV) můžete hostovat a "vlastní" transakce, který lze později být rozšířena na distribuovaných transakcí (nebo transakce MSDTC) v případě potřeby. Tím omezíte možnost pomocí příkaz MSDTC.

Tento konkrétní zdroj správce obvykle má svou vlastní interní bez distribuované transakce a musí podporovat převod těchto transakcí na distribuované transakce za běhu. SQL Server 2005 je například správce prostředků. V takovém případě <xref:System.Transactions> infrastruktury přebírá roli pasivní Správa právě sledováním transakci pro potřebu eskalace. Pro podporu interakce mezi <xref:System.Transactions> manager infrastruktury a prostředků, druhém musí implementovat rozhraní <xref:System.Transactions.IPromotableSinglePhaseNotification>.

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Metoda se používá k zařazení jednoho trvalého prostředek, který lze později eskalován. Tato metoda zajišťuje, že zařazení může být eskalován podle potřeby. Pokud zařazení úspěšná, správce prostředků vytvoří jeho vnitřní transakci a přidruží ji k <xref:System.Transactions> transakce. Pokud se nezdaří zařazení PSPE, by měl správce prostředků místo toho zařazení pomocí <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Selhání při zařazení v PSPE může dojít, když transakce je již distribuovaných transakcí, nebo když PSPE zařazení již provedl jiný správce prostředků

Jakmile je zapsán, volá klienty potvrzení nebo přerušení <xref:System.Transactions> transakce jsou převedeny na volání na správce prostředků vyvoláním <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> v případě metody nebo <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> v uvedeném pořadí.

Pokud <xref:System.Transactions> transakce nikdy vyžaduje eskalace, když je transakce potvrzeny, obdrží správce prostředků <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> oznámení. Poté jej lze potvrďte interní transakce, která byla původně vytvořena.

Pokud <xref:System.Transactions> transakce musí být eskalován (například pro podporu více RMs), <xref:System.Transactions> oznámí správci prostředků voláním <xref:System.Transactions.ITransactionPromoter.Promote%2A> metodu na <xref:System.Transactions.ITransactionPromoter> rozhraní, ze kterého <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní je odvozena. Správce prostředků potom převede transakce interně z místní transakce (která nevyžaduje protokolování) transakce objekt, který je schopen účasti na transakci DTC a přidruží ji k práci prováděné. Při transakci je vyzván k potvrzení, správce transakcí stále odešle <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> oznámení, aby správce zdrojů, který potvrdí distribuovaných transakcí, který je vytvořen při eskalace.

> [!NOTE]
> Trasování **TransactionCommitted** (které jsou generovány při vyvolání potvrzení pro eskalaci transakce) obsahují ID aktivity transakce DTC.

Další informace o eskalaci správy najdete v tématu [Eskalace správy transakcí](transaction-management-escalation.md).

## <a name="transaction-management-escalation-scenario"></a>Eskalace scénář pro správu transakce

Následující scénář ukazuje eskalaci distribuovaných transakcí pomocí <xref:System.Data> oboru názvů jako proxy "server" pro správce prostředků. Tento scénář předpokládá, že již existuje jedna <xref:System.Data> připojení k databázi, CN1, jejich zapojení do transakce a aplikace chce zahrnovat další <xref:System.Data> připojení, CN2. Transakce musí být rozšířena na DTC, jako dvoufázového úplná distribuované transakce.

V tomto případě

1. Volání CN1 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu za účelem zařadit do transakce. Potom transakce je stále místní a neexistují žádné další možné zařazení transakce, takže se <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> volání úspěšné.

2. Při volání CN2 druhé připojení <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, volání selže, protože je potřebný další možné zařazení. Z tohoto důvodu musí CN2 získat transakci DTC, chcete-li předat SQL. Chcete-li to provést, používá jednu z metody poskytované <xref:System.Transactions.TransactionInterop> třídy a vytvořit formát transakce, která mohou být zadány SQL.

3. <xref:System.Transactions>volá <xref:System.Transactions.ITransactionPromoter.Promote%2A> metodu na <xref:System.Transactions.ITransactionPromoter> rozhraní implementované CN1.

4. V tomto okamžiku CN1 eskaluje transakce, pomocí některé mechanismus, které jsou specifické pro SQL 2005 a <xref:System.Data>.

5. Návratová hodnota z <xref:System.Transactions.ITransactionPromoter.Promote%2A> je metoda bajtové pole, který obsahuje token šíření hodnoty pro transakci. <xref:System.Transactions>pomocí tohoto tokenu šíření vytvoří transakci DTC, kterou může začlenit do místní transakce.

6. V tomto okamžiku CN2 můžete použít data byla přijata z jedné z metod ve volání <xref:System.Transactions.TransactionInterop> mají být předány transakce SQL.

7. Nyní jak jsou uveden v transakci DTC distribuované.

## <a name="single-phase-commit-optimization"></a>Optimalizace potvrzení jedna fáze

Protokol potvrzení jedné fáze je efektivnější za běhu jako všechny aktualizace jsou provedeno bez explicitního koordinace. Chcete-li využít výhod této optimalizace, měli byste implementovat pomocí Správce prostředků <xref:System.Transactions.ISinglePhaseNotification> rozhraní pro daný prostředek a zařadit do transakce pomocí <xref:System.Transactions.Transaction.EnlistDurable%2A> nebo <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody. Konkrétně by parametr *EnlistmentOptions* měl <xref:System.Transactions.EnlistmentOptions.None> být roven tomu, aby bylo zajištěno provedení jediné fáze potvrzení.

Vzhledem k tomu <xref:System.Transactions.ISinglePhaseNotification> rozhraní je odvozena z <xref:System.Transactions.IEnlistmentNotification> rozhraní, není-li váš správce prostředků nárok na jediné fázi potvrzení, pak může i nadále přijímat dvě fáze potvrzení oznámení. Pokud váš správce prostředků přijme <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> oznámení ze Správce TM, by měl akci k provedení práce, které jsou nezbytné k potvrzení a odpovídajícím způsobem informovat správce transakcí, pokud má být potvrzena nebo vrácena zpět voláním transakce <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>, nebo <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> metodu na <xref:System.Transactions.SinglePhaseEnlistment> parametru. Odpověď <xref:System.Transactions.Enlistment.Done%2A> na zařazení v této fázi zahrnuje sémantiku jen pro čtení. Proto by neměl Odpovědět <xref:System.Transactions.Enlistment.Done%2A> spolu s některou z ostatních metod.

Pokud je k dispozici pouze jedno nestálé zařazení a žádné trvalé zařazení, nestálá zařazení obdrží oznámení SPC. Pokud existují nějaké nestálé zařazení a jenom jedno trvalé zařazení, nestálá zařazení získají 2PC. Po dokončení, trvalý zařazení obdrží certifikát SPC.

## <a name="see-also"></a>Viz také

- [Uvedení prostředků jako účastníků v transakci](enlisting-resources-as-participants-in-a-transaction.md)
- [Potvrzení transakce v jedné fázi a více fázích](committing-a-transaction-in-single-phase-and-multi-phase.md)
