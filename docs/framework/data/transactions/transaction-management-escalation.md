---
title: Eskalace správy transakcí
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: d2f027f8a94ee8f0cd23d0f0909ecc9137873bc2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205841"
---
# <a name="transaction-management-escalation"></a>Eskalace správy transakcí
Windows je hostitelem sadu služeb a moduly, které společně tvoří transakcí správce. Transakce řízení eskalace popisuje proces migrace transakcí z jednoho z komponenty správce transakcí.  
  
 <xref:System.Transactions>zahrnuje komponentu správce transakcí, která koordinuje transakci zahrnující maximálně jeden trvalý prostředek nebo více těkavých prostředků. Vzhledem k tomu, že správce transakcí se používá pouze volání uvnitř aplikační domény, bude vrácen nejlepší výkon. Vývojáři nemusí přímo spolupracovat se správcem transakcí. Místo toho je poskytována běžné infrastruktury, který definuje rozhraní, běžné chování a pomocné třídy <xref:System.Transactions> oboru názvů.  
  
 Pokud chcete transakci uvést do objektu v jiné doméně aplikace (včetně hranic mezi procesy a počítači) na stejném počítači, <xref:System.Transactions> infrastruktura automaticky předává transakci, která má být spravována společností Microsoft. DTC (Distributed Transaction Coordinator) (MSDTC). Eskalace také dochází v případě zařazení jiného správce prostředků trvalý. Když eskalován, transakce zůstane spravovaných ve stavu zvýšenými až do jeho dokončení.  
  
 Mezi <xref:System.Transactions> transakce a transakce MSDTC, je zprostředkovatel druh transakce, které jsou k dispozici prostřednictvím možné jedné fáze zařazení (PSPE). PSPE je jiný důležité mechanismus v <xref:System.Transactions> pro optimalizaci výkonu. Umožňuje vzdálený trvalý prostředek umístěný v různých aplikační domény, procesu nebo počítače se účastnit programu <xref:System.Transactions> transakce, aniž by ji chcete-li být rozšířena na transakci MSDTC. Další informace o PSPE najdete v tématu [zařazení prostředků jako účastníků v transakci](enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Jak zahájit eskalaci  
 Eskalace transakce snižuje výkon, protože příkaz MSDTC nachází v samostatném procesu a escalating transakcí MSDTC výsledků u odesílaných v rámci procesu. Chcete-li zvýšit výkon, měli byste zpozdit nebo vyhnout eskalaci MSDTC; Proto potřebujete znát, jak a kdy je možné zahájit eskalaci.  
  
 Dokud <xref:System.Transactions> infrastruktury zpracovává těkavých materiály a maximálně jeden trvalý prostředek, který podporuje jednofázové oznámení, transakce zůstává ve vlastnictví <xref:System.Transactions> infrastruktury. Správce transakcí využije pouze na tyto prostředky, že živé ve stejné doméně aplikace a pro které protokolování (zápis výsledek transakce na disk) není povinný. Eskalaci, která způsobí, že <xref:System.Transactions> infrastruktury přenos vlastnictví transakce do MSDTC se stane, když:  
  
- Nejméně jeden trvalý prostředek, který nepodporuje jednofázové oznámení je uveden v transakci.  
  
- Nejméně dva trvalý prostředky, které podporují jednofázové oznámení jsou v transakci zapsán. Například zařazení jednoho spojení s SQL Server 2005 nezpůsobí povýšení transakce. Kdykoli ale otevřete druhé připojení k databázi SQL Server 2005, která způsobila zařazení databáze, <xref:System.Transactions> infrastruktura zjistí, že se jedná o druhý trvalý prostředek v transakci, a předává ho do transakce MSDTC.  
  
- Požadavek na "zařazování" různé aplikační domény nebo jiný proces transakce je vyvolána. Můžete například serializace objektu transakce v rámci hranice domény aplikace. Objekt transakce je zařazené hodnotou, což znamená, že jakýkoliv pokus o ji předejte hranice domény aplikace (i ve stejném procesu) má za následek serializace objektu transakce. Objekty transakce můžete předat tím, že zavoláte na vzdálené metody, která přebírá <xref:System.Transactions.Transaction> jako parametr nebo vám může pokusu o přístup k vzdálené transakční obsluhovaná komponenty. Toto serializuje objekt transakce a má za následek eskalaci jako při serializován transakcí v rámci domény aplikace. Že distribuovaná a místní správce transakcí již není dostatečné.  
  
 V následující tabulce jsou uvedeny všechny výjimky, které mohou být vyvolány během eskalace.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Pokus o eskalovat transakce se rovná úroveň izolace <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|Správce transakcí je nefunkční.|  
|<xref:System.Transactions.TransactionException>|Eskalace nezdaří a aplikace je přerušeno.|
