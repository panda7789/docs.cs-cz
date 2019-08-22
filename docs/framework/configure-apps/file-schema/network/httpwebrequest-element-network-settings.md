---
title: <httpWebRequest> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: de5672e5c6762b1e0742e717a3d499a4f93ee8ec
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659345"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest – element > (nastavení sítě)
Přizpůsobuje parametry webového požadavku.  
  
 \<> Konfigurace  
\<system.net>  
\<Nastavení >  
\<httpWebRequest>  
  
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
|`maximumResponseHeadersLength`|Určuje maximální délku hlavičky odpovědi v kilobajtech. Výchozí hodnota je 64. Hodnota-1 označuje, že do hlaviček odpovědi nebude uloženo žádné omezení velikosti.|  
|`maximumErrorResponseLength`|Určuje maximální délku chybové odpovědi v kilobajtech. Výchozí hodnota je 64. Hodnota-1 označuje, že při chybové odpovědi nebude uloženo žádné omezení velikosti.|  
|`maximumUnauthorizedUploadLength`|Určuje maximální délku nahrávání jako odpověď na neautorizovaný kód chyby (v bajtech). Výchozí hodnota je-1. Hodnota-1 označuje, že při nahrávání nebude uloženo žádné omezení velikosti.|  
|`useUnsafeHeaderParsing`|Určuje, zda je povoleno nebezpečná analýza hlaviček. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[možnost](settings-element-network-settings.md)|Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení .NET Framework striktně vynutila specifikaci RFC 2616 pro analýzu identifikátorů URI. Některé odpovědi serveru mohou obsahovat řídicí znaky v zakázaných polích, což způsobí, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> že metoda <xref:System.Net.WebException>vyvolá výjimku. Pokud je **useUnsafeHeaderParsing** nastavené na **hodnotu true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> v tomto případě se v tomto případě nevyvolává. vaše aplikace ale bude zranitelná vůči několika formám útoků s analýzou identifikátoru URI. Nejlepším řešením je změnit server tak, aby odpověď neobsahovala řídicí znaky.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat větší než normální maximální délka hlavičky.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [Schéma nastavení sítě](index.md)
