---
title: '&lt;add&gt; – &lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 4552cc030a88841d4fb80c097ba089d1c6a0066c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a>&lt;add&gt; – &lt;protocolMapping&gt;
Představuje výchozí protokol mapování mezi přenosové schéma protokolu (např. http, net.tcp, net.pipe atd.) a vazbu Windows Communication Foundation (WCF). Při vytváření výchozí koncové body za běhu, WCF porovná nakonfigurované mapování a rozhodne, na které vazby pro konkrétní na základě adres.  
  
 \<system.serviceModel>  
\<protocolMapping >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Řetězec, který určuje typ vazby má být použit pro koncový bod během vytváření výchozí koncový bod.|  
|bindingConfiguration|Řetězec, který určuje název konfiguračního oddílu vazba bude odkazovat.|  
|scheme|Schéma přenosu protokolu má být použit pro výchozí koncový bod.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Představuje konfigurační oddíl pro definování výchozí protokol mapování mezi přenosu protokolu schémata (např. http, net.tcp, net.pipe atd.) a Windows Communication Foundation (WCF) vazby.|  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace ukazuje výchozí mapování protokolu v souboru machine.config. Můžete přepsat toto výchozí mapování na úrovni počítače úpravou souboru machine.config. Nebo pokud chcete pouze přepsání v rámci oboru aplikace, můžete přepsat v této části v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémat.  
  
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
