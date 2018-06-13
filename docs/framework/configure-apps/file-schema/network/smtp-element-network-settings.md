---
title: '&lt;SMTP&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 56912e09d24fc83e93a91cc42b1d96dcc68210f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741890"
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;SMTP&gt; – Element (nastavení sítě)
Nakonfiguruje formát doručení, metodu doručení a z adresy pro odesílání e-mailů.  
  
 \<Konfigurace >  
\<system.net>  
\<mailSettings – >  
\<smtp>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`deliveryFormat`|Určuje formát doručení pro odchozí e-mailů. Přípustné hodnoty jsou SevenBit a mezinárodní.|  
|`deliveryMethod`|Určuje metodu doručení e-mailů. Přípustné hodnoty jsou sítě, pickupDirectoryFromIis a specifiedpickupdirectory –.|  
|`from`|Určuje z adresy pro odchozí e-mailů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|Nakonfiguruje místní adresář pro přenos protokolu SMTP (Simple Mail) serveru.|  
|`network`|Nakonfiguruje možnosti sítě pro externí server SMTP.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[\<mailSettings – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Nakonfiguruje možnosti odesílání e-mailu.|  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
