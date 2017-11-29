---
title: "&lt;bypasslist –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d349f14535de806e0b130ef64b58333e63f1b86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltbypasslistgt-element-network-settings"></a>&lt;bypasslist –&gt; – Element (nastavení sítě)
Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.  
  
 \<Konfigurace >  
\<System.NET >  
\<defaultProxy – >  
\<bypasslist – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Přidat](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|Přidá IP adresy nebo názvu DNS na seznam obcházení proxy.|  
|[Vymazat](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|Vymaže seznam obcházení.|  
|[odebrat](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|Odebere seznam obcházení proxy adresy IP nebo název DNS.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy –](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).|  
  
## <a name="remarks"></a>Poznámky  
 Seznam obcházení obsahuje regulární výrazy, které popisují identifikátory URI, <xref:System.Net.WebRequest> instance přístup přímo místo z prostřednictvím proxy serveru.  
  
 Buďte opatrní při zadávání regulární výraz pro tento element. Regulární výraz "[-z] +\\.contoso\\.com" odpovídá všechny hostitele v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com. Vyhledat pouze na hostiteli v doméně contoso.com, použijte element anchor ("$"): "[-z] +\\.contoso\\.com$".  
  
 Další informace o regulárních výrazech najdete v tématu. [Regulární výrazy rozhraní .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá dvě adresy do seznamu jednorázové přihlášení. První obchází proxy server pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery začít jejichž IP adresy s 192.168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
