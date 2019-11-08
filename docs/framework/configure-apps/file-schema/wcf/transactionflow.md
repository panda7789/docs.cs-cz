---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736314"
---
# <a name="transactionflow"></a>\<transactionFlow >
Určuje podporu toku transakce pro vlastní vazbu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|transactionProtocol|Určuje transakční protokol, který se má použít. Platné hodnoty jsou následující:<br /><br /> – OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Výchozí hodnota je OleTransactions.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek umožňuje povolit nebo zakázat tok příchozích transakcí v nastaveních vazby koncového bodu a také určit požadovaný formát protokolu pro příchozí transakce. Další informace o použití tohoto konfiguračního prvku naleznete v tématu [Konfigurace transakce ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) a [Povolení toku transakce](../../../wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
> Při použití protokolu `OleTransactions` ke flowování transakcí z koncového bodu do koncového bodu může být časový limit transakce ztracený, pokud se cílový koncový bod pokusí o přetečení pomocí libovolného jiného protokolu než `OleTransactions`. To může způsobit, že všechny uzly nižší úrovně po OleTransactions směrování do vypršení časového limitu budou pozdější, než se čekalo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Konfigurace transakcí ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [Povolení toku transakcí](../../../wcf/feature-details/enabling-transaction-flow.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
