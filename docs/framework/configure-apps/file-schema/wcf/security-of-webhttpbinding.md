---
title: '&lt;security&gt; – &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 52146fa08ec63ef63fa996cdc09f9185b9f42e02
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646912"
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a>&lt;security&gt; – &lt;webHttpBinding&gt;
Určuje koncový bod nakonfigurovaný s požadavky na zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<webHttpBinding>  
\<Vytvoření vazby >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Určuje, zda zabezpečení transportní vrstvy nebo žádné zabezpečení používá koncový bod. Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázaná.|  
|Přenos|Zabezpečení je k dispozici pomocí protokolu HTTPS. Služba je potřeba nakonfigurovat s využitím certifikátů SSL. Zprávu je zcela zabezpečené pomocí protokolu HTTPS a služba je ověřený pomocí klienta pomocí certifikátu SSL služby. Ověření klienta je řízen pomocí `ClientCredentialType` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).|  
|TransportCredentialOnly|Tento režim neposkytuje integrity a důvěrnosti zpráv. Poskytuje ověření klienta založené na protokolu HTTP. Tento režim je třeba používat opatrně. Byste měli použít ve prostředích, kde zabezpečení přenosu se neposkytujeme jiným způsobem (jako je protokol IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<přenos >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Prvek vazby, který se používá ke konfiguraci koncových bodů pro Windows Communication Foundation (WCF) Web services tuto odpověď na požadavky HTTP namísto zpráv SOAP.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Výběr typu přihlašovacích údajů](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)  
 [Programovací model webových služeb HTTP WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
