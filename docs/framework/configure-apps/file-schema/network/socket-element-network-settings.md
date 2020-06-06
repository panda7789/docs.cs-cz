---
title: <socket> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089093"
---
# <a name="socket-element-network-settings"></a>\<socket> – element (nastavení sítě)
Určuje, jestli operace soketu používají porty dokončení.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Určuje, zda má soket vždy používat porty dokončení pro volání metody Accept. Výchozí hodnota je `false`.|  
|`alwaysUseCompletionPortsForConnect`|Určuje, zda má soket vždy používat porty dokončení pro volání metody připojení. Výchozí hodnota je `false`.|  
|`ipProtectionLevel`|Určuje výchozí hodnotu <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> , která se má použít pro soket. Výchozí hodnota závisí na verzi systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Objekt**|**Popis**|  
|-----------------|---------------------|  
|[zdroje dat](settings-element-network-settings.md)|Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.|  
  
## <a name="remarks"></a>Poznámky  
 `alwaysUseCompletionPortsForAccept`Atributy a `alwaysUseCompletionPortsForConnect` se používají k určení výchozího chování týkající se použití portů dokončení třídami v <xref:System.Net.Sockets?displayProperty=nameWithType> oboru názvů. Pro vysoce výkonné serverové aplikace se doporučují porty pro dokončení.  
  
 Výchozí hodnota `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` atributů a je **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForAccept` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForConnect` atributu z příslušných konfiguračních souborů.  
  
 `ipProtectionLevel`Atribut určuje výchozí hodnotu, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> která se má použít pro soket. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Vlastnost umožňuje konfiguraci omezení pro soket IPv6 do zadaného oboru, jako jsou adresy se stejným místní předponou nebo místní předponou webu. Tato možnost umožňuje aplikacím umístit omezení přístupu na sokety IPv6. Taková omezení umožňují aplikacím běžícím v privátní síti LAN jednoduše a robustní zabezpečení proti externím útokům. Tato možnost rozšiřuje nebo zužuje rozsah naslouchajícího soketu a umožňuje tak neomezený přístup k veřejným a soukromým uživatelům, pokud je to vhodné, nebo omezuje přístup jenom na stejnou lokalitu, jak je potřeba.  
  
 `ipProtectionLevel`Nastavení tohoto atributu má vliv jenom na počáteční příchozí provoz:  
  
- Server TCP naslouchá příchozím připojením na soketu.  
  
- Aplikace UDP, která přijímá paket na soketu.  
  
 Toto nastavení konfigurace neovlivňuje již zavedené připojení TCP (provoz není v obou směrech omezený) a nemá vliv na aplikaci, která odesílá pakety UDP.  
  
 Možné hodnoty pro `ipProtectionLevel` nastavení atributů odpovídají definovaným úrovním ochrany zadaným ve <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> výčtu následujícím způsobem:  
  
|**Hodnota atributu**|**Popis**|  
|-|-|  
|EdgeRestricted|Úroveň ochrany protokolu IP je omezena na hranici. Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet. Toto nastavení nepovoluje procházení síťových adres (NAT) pomocí implementace Windows Teredo. Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port. V systémech Windows Server 2003 a Windows XP je výchozí hodnota pro úroveň ochrany protokolu IP na soketu omezena na hranici.|  
|S omezeným přístupem|Úroveň ochrany protokolu IP je omezená. Tuto hodnotu budou používat intranetové aplikace, které neimplementují internetové scénáře. Tyto aplikace jsou obecně netestovány ani posíleny proti útokům pomocí internetového stylu. Toto nastavení omezí přijatý provoz jenom na místní připojení.|  
|Neomezené|Úroveň ochrany IP je neomezená. Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet, včetně aplikací využívajících možnosti přecházení IPv6 NAT integrované do Windows (například Teredo). Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port. V systémech Windows Server 2008 R2 a Windows Vista není výchozí hodnota pro úroveň ochrany IP adres na soketu omezená.|  
|Unspecified|Úroveň ochrany protokolu IP není určena. V systémech Windows 7 a Windows Server 2008 R2 není určena výchozí hodnota pro úroveň ochrany IP adres na soketu.|  
  
 Výchozí hodnota pro `ipProtectionLevel` atribut není **specifikována**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Vlastnost lze použít k získání aktuální hodnoty `ipProtectionLevel` atributu z příslušných konfiguračních souborů.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, zda mají být použity porty dokončení a že výchozí hodnota <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by měla být neomezená.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
