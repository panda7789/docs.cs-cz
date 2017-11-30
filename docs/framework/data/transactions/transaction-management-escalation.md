---
title: "Transakce správy eskalaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ac45390d78f4fbce15c8910fcdcc95713c5898a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-management-escalation"></a>Transakce správy eskalaci
Windows je hostitelem sadu služeb a moduly, které společně tvoří transakcí správce. Transakce řízení eskalace popisuje proces migrace transakcí z jednoho z komponenty správce transakcí.  
  
 <xref:System.Transactions>obsahuje součást Správce transakce, která souřadnice transakce zahrnující maximálně jeden prostředek trvalý nebo více těkavých zdrojů. Vzhledem k tomu, že správce transakcí se používá pouze volání uvnitř aplikační domény, bude vrácen nejlepší výkon. Vývojáři nemusí přímo spolupracovat se správcem transakcí. Místo toho je poskytována běžné infrastruktury, který definuje rozhraní, běžné chování a pomocné třídy <xref:System.Transactions> oboru názvů.  
  
 Pokud chcete zadat transakce na objekt v jiné doméně aplikace (včetně napříč hranicemi procesů a počítače) na stejném počítači, <xref:System.Transactions> infrastruktury automaticky eskaluje transakce má být spravováno aplikací společnosti Microsoft Koordinátor distribuovaných transakcí (MSDTC). Eskalace také dochází v případě zařazení jiného správce prostředků trvalý. Když eskalován, transakce zůstane spravovaných ve stavu zvýšenými až do jeho dokončení.  
  
 Mezi <xref:System.Transactions> transakce a transakce MSDTC, je zprostředkovatel druh transakce, které jsou k dispozici prostřednictvím možné jedné fáze zařazení (PSPE). PSPE je jiný důležité mechanismus v <xref:System.Transactions> pro optimalizaci výkonu. Umožňuje vzdálený trvalý prostředek umístěný v různých aplikační domény, procesu nebo počítače se účastnit programu <xref:System.Transactions> transakce, aniž by ji chcete-li být rozšířena na transakci MSDTC. Další informace o PSPE najdete v tématu [uvedení prostředky jako účastníky v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Jak zahájit eskalaci  
 Eskalace transakce snižuje výkon, protože příkaz MSDTC nachází v samostatném procesu a escalating transakcí MSDTC výsledků u odesílaných v rámci procesu. Pokud chcete zvýšit výkon, by měla zpoždění nebo vyhnout eskalace ke službě; Proto je třeba vědět, jak a kdy se zahájí eskalace.  
  
 Dokud <xref:System.Transactions> infrastruktury zpracovává těkavých materiály a maximálně jeden trvalý prostředek, který podporuje jednofázové oznámení, transakce zůstává ve vlastnictví <xref:System.Transactions> infrastruktury. Správce transakcí využije pouze na tyto prostředky, že živé ve stejné doméně aplikace a pro které protokolování (zápis výsledek transakce na disk) není povinný. Eskalaci, která způsobí, že <xref:System.Transactions> infrastruktury přenos vlastnictví transakce do MSDTC se stane, když:  
  
-   Nejméně jeden trvalý prostředek, který nepodporuje jednofázové oznámení je uveden v transakci.  
  
-   Nejméně dva trvalý prostředky, které podporují jednofázové oznámení jsou v transakci zapsán. Můžete například uvedení jednoho připojení s [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] nezpůsobí transakce má být povýšen. Však kdykoli otevřít druhé připojení k [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] databázi k zařazení, které způsobuje, že databáze <xref:System.Transactions> infrastruktury zjistí, že je druhý trvalý prostředek v transakci a eskaluje ho MSDTC transakce.  
  
-   Požadavek na "zařazování" různé aplikační domény nebo jiný proces transakce je vyvolána. Můžete například serializace objektu transakce v rámci hranice domény aplikace. Objekt transakce je zařazené hodnotou, což znamená, že jakýkoliv pokus o ji předejte hranice domény aplikace (i ve stejném procesu) má za následek serializace objektu transakce. Objekty transakce můžete předat tím, že zavoláte na vzdálené metody, která přebírá <xref:System.Transactions.Transaction> jako parametr nebo vám může pokusu o přístup k vzdálené transakční obsluhovaná komponenty. Toto serializuje objekt transakce a má za následek eskalaci jako při serializován transakcí v rámci domény aplikace. Že distribuovaná a místní správce transakcí již není dostatečné.  
  
 V následující tabulce jsou uvedeny všechny výjimky, které mohou být vyvolány během eskalace.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Pokus o eskalovat transakce se rovná úroveň izolace <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|Správce transakcí je nefunkční.|  
|<xref:System.Transactions.TransactionException>|Eskalace nezdaří a aplikace je přerušeno.|
