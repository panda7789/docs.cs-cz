---
title: "&lt;transport&gt; – &lt;netMsmqBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 611d6730695c2e353782d11cb74d391107c02c35
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a>&lt;transport&gt; – &lt;netMsmqBinding&gt;
Definuje nastavení zabezpečení přenosu.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netMsmqBinding>  
\<Vazba >  
\<zabezpečení >  
\<transport>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|msmqAuthenticationMode|Určuje, jak ověřit zprávu přenos MSMQ. Platné hodnoty patří:<br /><br /> -None: Bez ověřování.<br />-Třídy WindowsDomain: Ověřovací mechanismus používá služby Active Directory pro načtení certifikátu X.509 pro identifikátor zabezpečení spojený se zprávou. Používá se potom zkontrolujte, že seznamu ACL fronty, aby uživatel má oprávnění k zápisu pro frontu.<br />-Certifikát: Kanál načte příslušný certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je `WindowsDomain`.<br /><br /> Pokud tento atribut je nastaven na `None`, `msmqProtectionLevel` musí být také nastaven `None`. Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Určuje algoritmus, který se má použít pro šifrování zpráv v drátové síti při přenosu zpráv mezi správci fronty zpráv. Platné hodnoty patří:<br /><br /> -RC4Stream<br />-AES<br />-Výchozí hodnota je `RC4Stream`. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Určuje, že zprávy způsob, jak jsou zabezpečené na úrovni přenosu služby MSMQ. Šifrování zajistí, že zajišťuje zpráva integrity, při přihlašování a šifrování zpráv integrity a nepopiratelnosti. To znamená zpráva skutečně pochází od odesílatele a odesílatele je, kdo říká, že se. Platné hodnoty patří:<br /><br /> -None: Žádná ochrana.<br />-Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.<br />-Výchozí hodnota je `Sign`.|  
|msmqSecureHashAlgorithm|Určuje algoritmus hash, který se má použít pro výpočty hodnota hash. Platné hodnoty patří:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Výchozí hodnota je `SHA1`. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení přenosu pro přenosy ve frontě.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
