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
ms.openlocfilehash: aa455945b839ada4100138d5bdf9fc239376e5cb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663975"
---
# <a name="socket-element-network-settings"></a>\<Socket > – element (nastavení sítě)
Určuje, jestli operace soketu používají porty dokončení.  
  
 \<> Konfigurace  
\<system.net>  
\<Nastavení >  
\<> soketu  
  
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
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[možnost](settings-element-network-settings.md)|Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Atributy `alwaysUseCompletionPortsForAccept` <xref:System.Net.Sockets?displayProperty=nameWithType>a `alwaysUseCompletionPortsForConnect` se používají k určení výchozího chování týkající se použití portů dokončení třídami v oboru názvů. Pro vysoce výkonné serverové aplikace se doporučují porty pro dokončení.  
  
 Výchozí hodnota `alwaysUseCompletionPortsForAccept` atributů a `alwaysUseCompletionPortsForConnect` je **false**.  
  
 Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForAccept` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForConnect` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>  
  
 Atribut určuje výchozí hodnotu <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> , která se má použít pro soket. `ipProtectionLevel` <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost umožňuje konfiguraci omezení pro soket IPv6 do zadaného oboru, jako jsou adresy se stejným místní předponou nebo místní předponou webu. Tato možnost umožňuje aplikacím umístit omezení přístupu na sokety IPv6. Taková omezení umožňují aplikacím běžícím v privátní síti LAN jednoduše a robustní zabezpečení proti externím útokům. Tato možnost rozšiřuje nebo zužuje rozsah naslouchajícího soketu a umožňuje tak neomezený přístup k veřejným a soukromým uživatelům, pokud je to vhodné, nebo omezuje přístup jenom na stejnou lokalitu, jak je potřeba.  
  
 Nastavení `ipProtectionLevel` tohoto atributu má vliv jenom na počáteční příchozí provoz:  
  
- Server TCP naslouchá příchozím připojením na soketu.  
  
- Aplikace UDP, která přijímá paket na soketu.  
  
 Toto nastavení konfigurace neovlivňuje již zavedené připojení TCP (provoz není v obou směrech omezený) a nemá vliv na aplikaci, která odesílá pakety UDP.  
  
 Možné hodnoty pro `ipProtectionLevel` nastavení atributů odpovídají definovaným úrovním ochrany zadaným <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ve výčtu následujícím způsobem:  
  
|**Hodnota atributu**|**Popis**|  
|-|-|  
|EdgeRestricted|Úroveň ochrany protokolu IP je omezena na hranici. Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet. Toto nastavení nepovoluje procházení síťových adres (NAT) pomocí implementace Windows Teredo. Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port. V systémech Windows Server 2003 a Windows XP je výchozí hodnota pro úroveň ochrany protokolu IP na soketu omezena na hranici.|  
|S omezeným přístupem|Úroveň ochrany protokolu IP je omezená. Tuto hodnotu budou používat intranetové aplikace, které neimplementují internetové scénáře. Tyto aplikace jsou obecně netestovány ani posíleny proti útokům pomocí internetového stylu. Toto nastavení omezí přijatý provoz jenom na místní připojení.|  
|Neomezený|Úroveň ochrany IP je neomezená. Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet, včetně aplikací využívajících možnosti přecházení IPv6 NAT integrované do Windows (například Teredo). Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port. V systémech Windows Server 2008 R2 a Windows Vista není výchozí hodnota pro úroveň ochrany IP adres na soketu omezená.|  
|Neurčené|Úroveň ochrany protokolu IP není určena. V systémech Windows 7 a Windows Server 2008 R2 není určena výchozí hodnota pro úroveň ochrany IP adres na soketu.|  
  
 Výchozí hodnota pro `ipProtectionLevel` atribut není specifikována.  
  
 Vlastnost lze použít k získání aktuální hodnoty `ipProtectionLevel` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
