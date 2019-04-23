---
title: Konfigurace transakcí ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: d5bb81c618e3b27df32763948dbe56c9b37995e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188972"
---
# <a name="servicemodel-transaction-configuration"></a>Konfigurace transakcí ServiceModel
Windows Communication Foundation (WCF) obsahuje tři atributy pro konfiguraci transakce pro službu: `transactionFlow`, `transactionProtocol`, a `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurace transactionFlow  
 Většina předdefinovaných vazeb WCF poskytuje, obsahují `transactionFlow` a `transactionProtocol` atributy, tak, abyste mohli nakonfigurovat vazbu tak, aby přijímal příchozí transakce pro určitý koncový bod pomocí protokolu toku určené transakce. Kromě toho můžete použít `transactionFlow` elementu a jeho `transactionProtocol` atributu k sestavení vlastních vlastní vazby. Další informace o nastavení konfigurační prvky, naleznete v tématu [ \<vazby >](../../../../docs/framework/misc/binding.md) a [konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` Atribut určuje, zda je povolen tok transakce pro koncové body služby, které tuto vazbu využíval.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurace transactionProtocol  
 `transactionProtocol` Atribut určuje protokol transakce má použít s koncovými body služby, které tuto vazbu využíval.  
  
 Následuje příklad konfiguračního oddílu, který konfiguruje určenou vazbu pro podporu toku transakcí, stejně jako k využívání WS-AtomicTransaction protokolu.  
  
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
  
## <a name="configuring-transactiontimeout"></a>Konfigurace vlastností transactionTimeout  
 Můžete nakonfigurovat `transactionTimeout` atribut pro vaši službu WCF v `behavior` element konfiguračního souboru. Následující kód ukazuje, jak to provést.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` Atribut určuje časové období, ve kterém musí být vytvořené ve službě nové transakce dokončena. Se používá jako <xref:System.Transactions.TransactionScope> časový limit pro jakoukoli operaci, která zavádí novou transakci, a pokud <xref:System.ServiceModel.OperationBehaviorAttribute> se použije <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.  
  
 Časový limit určuje doba od vytvoření transakce pro dokončení fáze 1 v protokol dvoufázového potvrzení.  
  
 Pokud tento atribut je nastaven v rámci `service` konfiguračního oddílu, byste měli použít alespoň jednu metodu s odpovídající služby <xref:System.ServiceModel.OperationBehaviorAttribute>, ve kterém <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.  
  
 Mějte na paměti, že hodnota časového limitu je nejmenší hodnotu mezi touto `transactionTimeout` nastavení konfigurace a všechny <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [\<Vytvoření vazby >](../../../../docs/framework/misc/binding.md)
- [Konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
