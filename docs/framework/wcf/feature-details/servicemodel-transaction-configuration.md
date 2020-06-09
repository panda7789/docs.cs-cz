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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="69c8a-102">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="69c8a-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="69c8a-103">Windows Communication Foundation (WCF) poskytuje tři atributy pro konfiguraci transakcí pro službu: `transactionFlow` , a `transactionProtocol` `transactionTimeout` .</span><span class="sxs-lookup"><span data-stu-id="69c8a-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="69c8a-104">Konfigurace transactionFlow</span><span class="sxs-lookup"><span data-stu-id="69c8a-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="69c8a-105">Většina předdefinovaných vazeb WCF poskytuje `transactionFlow` `transactionProtocol` atributy a, takže můžete nakonfigurovat vazbu tak, aby přijímala příchozí transakce pro konkrétní koncový bod pomocí konkrétního protokolu toku transakce.</span><span class="sxs-lookup"><span data-stu-id="69c8a-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="69c8a-106">Kromě toho můžete použít `transactionFlow` prvek a jeho `transactionProtocol` atribut k sestavení vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="69c8a-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="69c8a-107">Další informace o nastavení elementů konfigurace naleznete v tématu [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) a [schématu konfigurace WCF](../../configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="69c8a-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="69c8a-108">`transactionFlow`Atribut určuje, zda je povolen tok transakce pro koncové body služby, které používají vazbu.</span><span class="sxs-lookup"><span data-stu-id="69c8a-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="69c8a-109">Konfigurace transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="69c8a-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="69c8a-110">`transactionProtocol`Atribut určuje protokol transakce pro použití s koncovými body služby, které používají vazbu.</span><span class="sxs-lookup"><span data-stu-id="69c8a-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="69c8a-111">Následuje příklad konfiguračního oddílu, který konfiguruje zadanou vazbu na podporu toku transakce a také používá protokol WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="69c8a-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="69c8a-112">Konfigurace vlastnost TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="69c8a-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="69c8a-113">Můžete nakonfigurovat `transactionTimeout` atribut pro službu WCF v `behavior` elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="69c8a-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="69c8a-114">Následující kód ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="69c8a-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="69c8a-115">`transactionTimeout`Atribut určuje časové období, ve kterém musí být dokončena nová transakce vytvořená ve službě.</span><span class="sxs-lookup"><span data-stu-id="69c8a-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="69c8a-116">Používá se jako <xref:System.Transactions.TransactionScope> časový limit pro jakoukoli operaci, která vytváří novou transakci, a pokud <xref:System.ServiceModel.OperationBehaviorAttribute> je použita, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnost je nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="69c8a-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="69c8a-117">Časový limit určuje dobu od vytvoření transakce až do dokončení fáze 1 v protokolu dvoufázového potvrzení.</span><span class="sxs-lookup"><span data-stu-id="69c8a-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="69c8a-118">Pokud je tento atribut nastaven v rámci `service` konfiguračního oddílu, měli byste použít alespoň jednu metodu odpovídající služby s <xref:System.ServiceModel.OperationBehaviorAttribute> , ve které <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je vlastnost nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="69c8a-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="69c8a-119">Všimněte si, že použitá hodnota časového limitu je menší hodnota mezi `transactionTimeout` nastavením konfigurace a libovolnou <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="69c8a-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c8a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="69c8a-120">See also</span></span>

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="69c8a-121">Konfigurační schéma služby WCF</span><span class="sxs-lookup"><span data-stu-id="69c8a-121">WCF Configuration Schema</span></span>](../../configure-apps/file-schema/wcf/index.md)
