---
title: '&lt;httpWebRequest&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 586b3e7219c72b6cd00653d6d0be3a74f6359709
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048980"
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt; – Element (nastavení sítě)
Přizpůsobí parametrů webové žádosti.  
  
 \<Konfigurace >  
\<system.net>  
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
|`maximumResponseHeadersLength`|Určuje v kilobajtech maximální délka hlavičky odpovědi. Výchozí hodnota je 64. Hodnota -1 znamená, že žádné omezení velikosti se nevyžaduje v hlavičkách odpovědi.|  
|`maximumErrorResponseLength`|Určuje maximální délku reakce na chybu, v kilobajtech. Výchozí hodnota je 64. Hodnota -1 znamená, že žádné omezení velikosti se nevyžaduje v odpovědi na chybu.|  
|`maximumUnauthorizedUploadLength`|Určuje maximální délku nahrání v reakci na neautorizovaný chybový kód, v bajtech. Výchozí hodnota je -1. Hodnota -1 znamená, že žádné omezení velikosti bude vynucená pro nahrávání.|  
|`useUnsafeHeaderParsing`|Určuje, zda je povolena analýza nebezpečné záhlaví. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení rozhraní .NET Framework přísně dokumentu RFC 2616 k analýze identifikátoru URI. Některé odpovědi serveru může obsahovat řídicí znaky zakázaných polí, které způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda k vyvolání <xref:System.Net.WebException>. Pokud **useUnsafeHeaderParsing** je nastavena na **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nezpůsobí výjimku v tomto případě; nicméně, vaše aplikace bude zranitelný vůči několik tvarů útoky parsování identifikátorů URI. Nejlepším řešením je změnit server tak, aby odpovědi neobsahuje řídicí znaky.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit větší než normální záhlaví maximální délku.  
  
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
