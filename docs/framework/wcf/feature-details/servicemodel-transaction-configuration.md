---
title: Konfigurace transakcí ServiceModel
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 96cf83be06949160cf3efa73344e4a7680d24e09
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="13a5c-102">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="13a5c-102">ServiceModel Transaction Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="13a5c-103"> obsahuje tři atributy pro konfiguraci transakce pro službu: `transactionFlow`, `transactionProtocol`, a `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="13a5c-103"> provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="13a5c-104">Konfigurace transactionFlow</span><span class="sxs-lookup"><span data-stu-id="13a5c-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="13a5c-105">Většina z předdefinovaných vazeb [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje obsahovat `transactionFlow` a `transactionProtocol` atributy, takže můžete nakonfigurovat vazby tak, aby přijímal příchozí transakce pro koncový bod konkrétní použití protokolu toku konkrétní transakce.</span><span class="sxs-lookup"><span data-stu-id="13a5c-105">Most of the predefined bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="13a5c-106">Kromě toho můžete použít `transactionFlow` elementu a jeho `transactionProtocol` atribut vytvářet vlastní vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="13a5c-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="13a5c-107">Další informace o nastavení konfigurační prvky najdete v tématu [ \<vazby >](../../../../docs/framework/misc/binding.md) a [konfigurační schéma služby WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="13a5c-107">For more information about setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="13a5c-108">`transactionFlow` Atribut určuje, zda toku transakcí je povoleno pro koncové body služby, které používají vazby.</span><span class="sxs-lookup"><span data-stu-id="13a5c-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="13a5c-109">Konfigurace transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="13a5c-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="13a5c-110">`transactionProtocol` Určuje atribut, protokol transakcí pro použití s koncové body služby, které používají vazby.</span><span class="sxs-lookup"><span data-stu-id="13a5c-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="13a5c-111">Následuje příklad konfiguračního oddílu, který konfiguruje protokol WS-AtomicTransaction Zadaná vazba pro podporu toku transakcí, jakož i použití.</span><span class="sxs-lookup"><span data-stu-id="13a5c-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="13a5c-112">Konfigurace vlastností transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="13a5c-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="13a5c-113">Můžete nakonfigurovat `transactionTimeout` atribut pro vaše [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v `behavior` element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="13a5c-113">You can configure the `transactionTimeout` attribute for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="13a5c-114">Následující kód ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="13a5c-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="13a5c-115">`transactionTimeout` Atribut určuje časové období, ve kterém musí dokončit v službě vytvořit novou transakci.</span><span class="sxs-lookup"><span data-stu-id="13a5c-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="13a5c-116">Je používán jako <xref:System.Transactions.TransactionScope> časový limit pro žádnou operaci, která vytvoří novou transakci, a pokud <xref:System.ServiceModel.OperationBehaviorAttribute> se použije, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="13a5c-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="13a5c-117">Časový limit určuje dobu od okamžiku vytvoření transakce pro dokončení fáze 1 dvoufázového protokolu.</span><span class="sxs-lookup"><span data-stu-id="13a5c-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="13a5c-118">Pokud tento atribut nastavený v rámci `service` konfigurační oddíl, byste měli použít alespoň jednu metodu odpovídající služby s <xref:System.ServiceModel.OperationBehaviorAttribute>, ve kterém <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="13a5c-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="13a5c-119">Upozorňujeme, že dojde k vypršení platnosti použít nejmenší hodnotu mezi touto `transactionTimeout` nastavení konfigurace a všechny <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="13a5c-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a5c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="13a5c-120">See Also</span></span>  
 [<span data-ttu-id="13a5c-121">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="13a5c-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="13a5c-122">Konfigurační schéma služby WCF</span><span class="sxs-lookup"><span data-stu-id="13a5c-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
