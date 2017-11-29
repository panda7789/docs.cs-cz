---
title: "&lt;HttpWebRequest –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0a4490870cb12ff221f75b043f01baad9b5c7c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;HttpWebRequest –&gt; – Element (nastavení sítě)
Přizpůsobí parametry webové žádosti.  
  
 \<Konfigurace >  
\<System.NET >  
\<Nastavení >  
\<httpWebRequest >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Určuje v kilobajtech maximální délka hlavičky odpovědi. Výchozí hodnota je 64. Hodnota -1 označuje, že žádné omezení velikosti bude vynucená pro hlavičky odpovědi.|  
|`maximumErrorResponseLength`|Maximální délka chybnou odpověď, určuje v kilobajtech. Výchozí hodnota je 64. Hodnota -1 označuje, že žádné omezení velikosti bude vynucená pro odpovědi na chybu.|  
|`maximumUnauthorizedUploadLength`|Určuje maximální délku nahrávaný v reakci na neoprávněné chybový kód, v bajtech. Výchozí hodnota je -1. Hodnota -1 označuje, že žádné omezení velikosti bude vynucená pro odesílání.|  
|`useUnsafeHeaderParsing`|Určuje, zda je povolena analýza unsafe záhlaví. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení rozhraní .NET Framework výhradně vynucuje dokumentu RFC 2616 k analýze identifikátoru URI. Některé odezvy serveru může obsahovat řídicí znaky v zakázané pole, které způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda k vyvolání <xref:System.Net.WebException>. Pokud **useUnsafeHeaderParsing** je nastaven na **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nezpůsobí výjimku, v takovém případě; ale, bude vaše aplikace bude zranitelný vůči několika formulářů analýza útoky identifikátoru URI. Nejlepším řešením je změna serveru tak, aby odpověď neobsahuje řídicí znaky.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit větší než délka normální maximální záhlaví.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
