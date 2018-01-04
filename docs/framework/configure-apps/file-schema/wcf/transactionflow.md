---
title: '&lt;transactionFlow&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3720294ac937c6aa7ce99ab687efa76b2e860abb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactionflowgt"></a>&lt;transactionFlow&gt;
Určuje podpora toku transakcí pro vlastní připojení.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<transactionFlow >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|TransactionProtocol|Určuje protokol transakce, který se má použít. Platné hodnoty patří:<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> Výchozí hodnota je OleTransactions.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element můžete povolit nebo zakázat příchozí tok transakcí v nastavení vazby koncového bodu, a také k určení formátu požadovaný protokol pro příchozí transakce. Další informace o použití tohoto elementu konfigurace najdete v tématu [konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) a [povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
>  Při použití `OleTransactions` protokolu směrování transakcí z koncového bodu endpoint, časový limit transakcí může dojít ke ztrátě, pokud do cílového koncového bodu se pokusí znovu s použitím libovolný protokol pro jiné než toku `OleTransactions`. Všechny uzly nižší úrovni. to může způsobit po směrování OleTransactions časový limit později, než se očekávalo.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [Povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
