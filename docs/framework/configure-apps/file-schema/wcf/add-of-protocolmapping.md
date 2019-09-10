---
title: <add> z <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850375"
---
# <a name="add-of-protocolmapping"></a>\<Přidat > \<> ProtocolMapping
Představuje výchozí mapování protokolů mezi schématem transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a vazbou Windows Communication Foundation (WCF). Při vytváření výchozích koncových bodů za běhu vyhledá WCF nakonfigurované mapování a rozhodne, které vazby použít pro konkrétní adresu založenou na.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protocolMapping >** ](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Řetězec, který určuje typ vazby, která se má použít pro koncový bod při vytváření výchozího koncového bodu.|  
|bindingConfiguration|Řetězec, který určuje název konfiguračního oddílu vazby, na který se má odkazovat.|  
|scheme|Schéma přenosového protokolu, které se má použít pro výchozí koncový bod.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|Představuje konfigurační oddíl pro definování výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a Windows Communication Foundation (WCF) vazby.|  
  
## <a name="example"></a>Příklad  
 Následující konfigurační příklad ukazuje výchozí mapování protokolu v souboru Machine. config. Toto výchozí mapování na úrovni počítače můžete přepsat úpravou souboru Machine. config. Nebo pokud byste ho chtěli přepsat v rámci rozsahu aplikace, můžete tuto část přepsat v konfiguračním souboru aplikace a změnit mapování pro jednotlivá schémata protokolů.  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
