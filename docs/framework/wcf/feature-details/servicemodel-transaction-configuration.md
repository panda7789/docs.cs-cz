---
title: Konfigurace transakcí ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184455"
---
# <a name="servicemodel-transaction-configuration"></a>Konfigurace transakcí ServiceModel
Windows Communication Foundation (WCF) poskytuje tři atributy pro `transactionFlow`konfiguraci transakcí pro službu: , `transactionProtocol`a `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurace transakceFlow  
 Většina předdefinovaných vazeb, které `transactionFlow` WCF poskytuje, obsahuje atributy a, `transactionProtocol` takže můžete nakonfigurovat vazbu tak, aby přijímala příchozí transakce pro konkrétní koncový bod pomocí konkrétního protokolu toku transakcí. Kromě toho můžete použít `transactionFlow` prvek `transactionProtocol` a jeho atribut k vytvoření vlastní vazby. Další informace o nastavení konfiguračních prvků naleznete [ \<v tématu vazby>](../../configure-apps/file-schema/wcf/bindings.md) a [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 Atribut `transactionFlow` určuje, zda je povolen tok transakcí pro koncové body služby, které používají vazbu.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurace protokolu transactionProtocol  
 Atribut `transactionProtocol` určuje transakční protokol, který se má použít s koncovými body služby, které používají vazbu.  
  
 Následuje příklad konfigurační části, která konfiguruje zadanou vazbu pro podporu toku transakcí, stejně jako použití protokolu WS-AtomicTransaction.  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a>Konfigurace transakceTimeout  
 Atribut služby `transactionTimeout` WCF můžete nakonfigurovat `behavior` v prvku konfiguračního souboru. Následující kód ukazuje, jak to provést.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 Atribut `transactionTimeout` určuje časové období, ve kterém musí být dokončena nová transakce vytvořená ve službě. Používá se jako <xref:System.Transactions.TransactionScope> časový časový úsek pro všechny operace, která <xref:System.ServiceModel.OperationBehaviorAttribute> vytvoří novou <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> transakci, `true`a pokud je použita, vlastnost je nastavena na .  
  
 Časový limit určuje dobu od vytvoření transakce do dokončení fáze 1 v protokolu dvoufázového potvrzení.  
  
 Pokud je tento atribut `service` nastaven v části konfigurace, měli byste použít <xref:System.ServiceModel.OperationBehaviorAttribute>alespoň jednu metodu odpovídající služby s , ve kterém je <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnost nastavena na `true`.  
  
 Všimněte si, že použitá hodnota časového `transactionTimeout` času je <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> menší hodnota mezi tímto nastavením konfigurace a libovolnou vlastností.  
  
## <a name="see-also"></a>Viz také

- [\<závazné>](../../configure-apps/file-schema/wcf/bindings.md)
- [Konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
