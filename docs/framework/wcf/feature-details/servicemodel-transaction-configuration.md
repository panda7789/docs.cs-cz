---
title: Konfigurace transakcí ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: e8c8c9ebff259ccd991768afb8cdf9925a66aad0
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141609"
---
# <a name="servicemodel-transaction-configuration"></a>Konfigurace transakcí ServiceModel
Windows Communication Foundation (WCF) poskytuje tři atributy pro konfiguraci transakcí pro službu: `transactionFlow`, `transactionProtocol`a `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurace transactionFlow  
 Většina předdefinovaných vazeb WCF obsahuje atributy `transactionFlow` a `transactionProtocol`, takže můžete nakonfigurovat vazbu tak, aby přijímala příchozí transakce pro konkrétní koncový bod pomocí konkrétního protokolu toku transakce. Kromě toho můžete použít prvek `transactionFlow` a jeho atribut `transactionProtocol` k sestavení vlastní vazby. Další informace o nastavení elementů konfigurace najdete v tématu [\<vázání >](../../configure-apps/file-schema/wcf/bindings.md) a [schématu konfigurace WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 Atribut `transactionFlow` určuje, zda je pro koncové body služby, které používají vazbu, povolen tok transakcí.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurace transactionProtocol  
 Atribut `transactionProtocol` určuje protokol transakce pro použití s koncovými body služby, které používají vazbu.  
  
 Následuje příklad konfiguračního oddílu, který konfiguruje zadanou vazbu na podporu toku transakce a také používá protokol WS-AtomicTransaction.  
  
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
  
## <a name="configuring-transactiontimeout"></a>Konfigurace vlastnost TransactionTimeout  
 Atribut `transactionTimeout` pro službu WCF můžete nakonfigurovat v elementu `behavior` konfiguračního souboru. Následující kód ukazuje, jak to provést.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 Atribut `transactionTimeout` určuje časové období, ve kterém musí být nová transakce vytvořená ve službě dokončena. Používá se jako časový limit <xref:System.Transactions.TransactionScope> pro jakoukoli operaci, která vytváří novou transakci, a pokud je <xref:System.ServiceModel.OperationBehaviorAttribute> použito, vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.  
  
 Časový limit určuje dobu od vytvoření transakce až do dokončení fáze 1 v protokolu dvoufázového potvrzení.  
  
 Pokud je tento atribut nastaven v rámci konfiguračního oddílu `service`, měli byste použít alespoň jednu metodu odpovídající služby s <xref:System.ServiceModel.OperationBehaviorAttribute>, ve které je vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavena na `true`.  
  
 Všimněte si, že použitá hodnota časového limitu je menší hodnota mezi nastavením konfigurace `transactionTimeout` a libovolnou vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.  
  
## <a name="see-also"></a>Viz také:

- [vazba \<](../../configure-apps/file-schema/wcf/bindings.md)
- [Konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
