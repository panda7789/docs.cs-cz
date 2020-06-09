---
title: Konfigurace transakcí ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 1d04a7bb756cccb33b436c1f57decc0249764828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600332"
---
# <a name="servicemodel-transaction-configuration"></a>Konfigurace transakcí ServiceModel
Windows Communication Foundation (WCF) poskytuje tři atributy pro konfiguraci transakcí pro službu: `transactionFlow` , a `transactionProtocol` `transactionTimeout` .  
  
## <a name="configuring-transactionflow"></a>Konfigurace transactionFlow  
 Většina předdefinovaných vazeb WCF poskytuje `transactionFlow` `transactionProtocol` atributy a, takže můžete nakonfigurovat vazbu tak, aby přijímala příchozí transakce pro konkrétní koncový bod pomocí konkrétního protokolu toku transakce. Kromě toho můžete použít `transactionFlow` prvek a jeho `transactionProtocol` atribut k sestavení vlastní vazby. Další informace o nastavení elementů konfigurace naleznete v tématu [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) a [schématu konfigurace WCF](../../configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow`Atribut určuje, zda je povolen tok transakce pro koncové body služby, které používají vazbu.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurace transactionProtocol  
 `transactionProtocol`Atribut určuje protokol transakce pro použití s koncovými body služby, které používají vazbu.  
  
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
 Můžete nakonfigurovat `transactionTimeout` atribut pro službu WCF v `behavior` elementu konfiguračního souboru. Následující kód ukazuje, jak to provést.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout`Atribut určuje časové období, ve kterém musí být dokončena nová transakce vytvořená ve službě. Používá se jako <xref:System.Transactions.TransactionScope> časový limit pro jakoukoli operaci, která vytváří novou transakci, a pokud <xref:System.ServiceModel.OperationBehaviorAttribute> je použita, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnost je nastavena na `true` .  
  
 Časový limit určuje dobu od vytvoření transakce až do dokončení fáze 1 v protokolu dvoufázového potvrzení.  
  
 Pokud je tento atribut nastaven v rámci `service` konfiguračního oddílu, měli byste použít alespoň jednu metodu odpovídající služby s <xref:System.ServiceModel.OperationBehaviorAttribute> , ve které <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je vlastnost nastavena na `true` .  
  
 Všimněte si, že použitá hodnota časového limitu je menší hodnota mezi `transactionTimeout` nastavením konfigurace a libovolnou <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastností.  
  
## <a name="see-also"></a>Viz také

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [Konfigurační schéma služby WCF](../../configure-apps/file-schema/wcf/index.md)
