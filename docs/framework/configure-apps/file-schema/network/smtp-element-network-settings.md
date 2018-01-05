---
title: "&lt;SMTP&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 598fe3dc2a49187e923cd689f863d0a3327e735f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;SMTP&gt; – Element (nastavení sítě)
Nakonfiguruje formát doručení, metodu doručení a z adresy pro odesílání e-mailů.  
  
 \<Konfigurace >  
\<System.NET >  
\<mailSettings – >  
\<SMTP >  
  
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
