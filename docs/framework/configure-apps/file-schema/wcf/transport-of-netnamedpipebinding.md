---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 9bcaae68051be2976b97989657efe53cf7a2718a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263447"
---
# <a name="transport-of-netnamedpipebinding"></a>\<transport> of \<netNamedPipeBinding>
Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netNamedPipeBinding>  
\<Vytvoření vazby >  
\<security>  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Třída protectionLevel|Definuje úroveň ochrany pojmenovaného kanálu. Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů. Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu. Platné hodnoty patří:<br /><br /> -Žádný: Žádná ochrana.<br />– Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.<br /><br /> Výchozí hodnota je EncryptAndSign.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Definuje nastavení zabezpečení pro vazbu.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
