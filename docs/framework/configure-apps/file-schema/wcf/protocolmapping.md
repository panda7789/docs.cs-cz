---
title: '&lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: c50ca451052c9ad9d7ab6a0cb5387e644196191e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525003"
---
# <a name="ltprotocolmappinggt"></a>&lt;protocolMapping&gt;
Představuje konfigurační oddíl pro definování sady výchozích mapování protokolů mezi schématy přenosových protokolů (např. http, net.tcp, net.pipe atd.) a vazbami WCF. Při vytváření výchozí koncové body za běhu, Windows Communication Foundation (WCF) zabývá nakonfigurované mapování a určuje, na které vazby pro konkrétní základě adresu.  
  
[**\<system.serviceModel >**](system-servicemodel.md)  
&nbsp;&nbsp;**\<protocolMapping >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<protocolMapping>
   <add binding="String" bindingConfiguration="String" scheme="http/net.msmq/net.pipe/net.tcp"/>
</protocolMapping>  
```

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtry>](filters-of-routing.md)|Obsahuje výchozí mapování protokolů mezi schématem přenosového protokolu (např. http, net.tcp, net.pipe atd.) a vazeb WCF.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Kořenový element všechny elementy konfigurace WCF.|  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace ukazuje výchozí mapování protokolů v souboru machine.config. Můžete přepsat toto výchozí mapování na úrovni počítače tak, že upravíte soubor machine.config. Nebo pokud chcete pouze přepsat v rámci oboru aplikace, můžete ignorovat tento oddíl v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémata.  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
