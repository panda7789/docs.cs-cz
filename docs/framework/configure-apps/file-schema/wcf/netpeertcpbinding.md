---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 1b2e5030c55f8568bc418b507878ddbf202b39fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750879"
---
# <a name="ltnetpeertcpbindinggt"></a>&lt;netPeerTcpBinding&gt;
Definuje vazbu pro sdílené kanál konkrétní TCP zasílání zpráv.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netPeerTcpBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|ListenIPAddress|Řetězec, který určuje IP adresu, na kterém bude uzlu sdílené naslouchat zpráv TCP. Výchozí hodnota je `null`.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|port|Celé číslo, které určuje, na které tato vazba zpracuje rovnocenné zprávy TCP port síťového rozhraní. Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>. Výchozí hodnota je 0.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<překladač >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Určuje sdílené překladač použité v této vazbě přeložit sdílené OK ID sítě na koncový bod IP adresy uzlů v rámci sdílené OK.|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|Definuje nastavení zabezpečení pro zprávu. Tento element je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tato vazba poskytuje podporu pro vytváření aplikací peer-to-peer nebo více stran použití sdílené přenosu přes protokol TCP. Každý uzel sdílené může být hostitelem více typů komunikačních kanálů sdílené, které jsou definované s tímto typem vazby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití NetPeerTcpBinding vazby, který poskytuje více stran komunikaci pomocí rovnocenného kanálu. Podrobné scénář použití tuto vazbu, najdete v části [Net sdílené TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [NET sdílené TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
