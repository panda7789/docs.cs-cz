---
title: "&lt;transport&gt; – &lt;msmqIntegrationBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27b2ade7c9033ca82d3249ef18f1004e30c30025
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a>&lt;transport&gt; – &lt;msmqIntegrationBinding&gt;
Definuje nastavení zabezpečení pro transport integrace služby Řízení front zpráv.  
  
 \<systém. ServiceModel >  
\<vazby >  
msmqIntegrationBinding  
\<Vazba >  
\<zabezpečení >  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Určuje, jak ověřit zprávu přenos MSMQ. Pokud je nastavena v `None`, hodnota `msmqProtectionLevel` musí být také nastaven `None`.<br /><br /> Platné hodnoty patří:<br /><br /> -None: Bez ověřování.<br />-Třídy WindowsDomain: Ověřovací mechanismus používá služby Active Directory k získání certifikátu X.509 SID přidružené ke zprávě. Používá se potom zkontrolujte, že seznamu ACL fronty, aby uživatel má oprávnění k zápisu do fronty.<br />-Certifikát: Kanál získá certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je třídy WindowsDomain. Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus, který se má použít pro šifrování zpráv v drátové síti při přenosu zpráv mezi správci fronty zpráv. Platné hodnoty patří:<br /><br /> -RC4Stream<br />-AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Určuje, jak jsou zprávy zabezpečená na úrovni přenosu služby MSMQ. Šifrování zajistíte integritu zpráva při EncryptAndSign zajišťuje zpráva integrity a nepopiratelnosti; To znamená zpráva skutečně pochází z odesílatele a odesílatele je, kdo říká, že se.<br /><br /> -Platné hodnoty patří:<br />-None: Žádná ochrana.<br />-Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.<br /><br /> Výchozí hodnota je přihlášení. Tento atribut je typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|-Určuje algoritmus, který se má použít v oblasti výpočetních daný výtah jako součást podpisy. Platné hodnoty patří:<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definuje nastavení zabezpečení pro vazby služby MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element zapouzdří nastavení zabezpečení pro transport integrace služby Řízení front zpráv. Nastavení jsou stejné pro integraci služby Řízení front zpráv a ve frontě přenosů. Umožňuje nastavit režim ověřování, algoritmus šifrování, algoritmus Secure Hash Algorithm a úroveň ochrany.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
