---
title: "Konfigurace transakcí ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54b07eff0b54816fe2d359a27f75b07ecb9f355a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="servicemodel-transaction-configuration"></a>Konfigurace transakcí ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]obsahuje tři atributy pro konfiguraci transakce pro službu: `transactionFlow`, `transactionProtocol`, a `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurace transactionFlow  
 Většina z předdefinovaných vazeb [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje obsahovat `transactionFlow` a `transactionProtocol` atributy, takže můžete nakonfigurovat vazby tak, aby přijímal příchozí transakce pro koncový bod konkrétní použití protokolu toku konkrétní transakce. Kromě toho můžete použít `transactionFlow` elementu a jeho `transactionProtocol` atribut vytvářet vlastní vlastní vazby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nastavení konfigurační prvky, najdete v části [ \<vazby >](../../../../docs/framework/misc/binding.md) a [konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` Atribut určuje, zda toku transakcí je povoleno pro koncové body služby, které používají vazby.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurace transactionProtocol  
 `transactionProtocol` Určuje atribut, protokol transakcí pro použití s koncové body služby, které používají vazby.  
  
 Následuje příklad konfiguračního oddílu, který konfiguruje protokol WS-AtomicTransaction Zadaná vazba pro podporu toku transakcí, jakož i použití.  
  
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
 Můžete nakonfigurovat `transactionTimeout` atribut pro vaše [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v `behavior` element konfiguračního souboru. Následující kód ukazuje, jak to provést.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` Atribut určuje časové období, ve kterém musí dokončit v službě vytvořit novou transakci. Je používán jako <xref:System.Transactions.TransactionScope> časový limit pro žádnou operaci, která vytvoří novou transakci, a pokud <xref:System.ServiceModel.OperationBehaviorAttribute> se použije, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.  
  
 Časový limit určuje dobu od okamžiku vytvoření transakce pro dokončení fáze 1 dvoufázového protokolu.  
  
 Pokud tento atribut nastavený v rámci `service` konfigurační oddíl, byste měli použít alespoň jednu metodu odpovídající služby s <xref:System.ServiceModel.OperationBehaviorAttribute>, ve kterém <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.  
  
 Upozorňujeme, že dojde k vypršení platnosti použít nejmenší hodnotu mezi touto `transactionTimeout` nastavení konfigurace a všechny <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [\<Vazba >](../../../../docs/framework/misc/binding.md)  
 [Konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
