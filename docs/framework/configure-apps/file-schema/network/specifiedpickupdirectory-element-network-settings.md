---
title: "&lt;specifiedpickupdirectory –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0df8cb46943862e3de66faa5551f550cb232f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a>&lt;specifiedpickupdirectory –&gt; – Element (nastavení sítě)
Nakonfiguruje místní adresář pro přenos protokolu SMTP (Simple Mail) serveru.  
  
 \<Konfigurace >  
\<System.NET >  
\<mailSettings – >  
\<SMTP >  
\<specifiedpickupdirectory – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|Adresář, kde aplikace ukládání e-mailů pro pozdější zpracování serverem SMTP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<SMTP > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Nakonfiguruje možnosti odesílání e-mailu přenosu protokolu SMTP (Simple Mail).|  
  
## <a name="remarks"></a>Poznámky  
 `specifiedPickupDirectory` Atribut nastaví adresář, kde aplikace uložit e-mailových zpráv, které mají být zpracovány serverem SMTP.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje c:\maildrop jako předávací adresář pošty.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
