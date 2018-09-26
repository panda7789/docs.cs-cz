---
title: '&lt;soket&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: fb057ab75c31edd7bbdaf5d5115cda2802d3b057
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203992"
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;soket&gt; – Element (nastavení sítě)
Určuje, zda operace soketu používat porty dokončení.  
  
 \<Konfigurace >  
\<system.net>  
\<Nastavení >  
\<soket >  
  
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
|`alwaysUseCompletionPortsForAccept`|Označuje, zda soketu měli vždy používat porty dokončení pro volání metody přijmout. Výchozí hodnota je `false`.|  
|`alwaysUseCompletionPortsForConnect`|Označuje, zda soketu by měla vždy používat porty dokončení pro volání metody připojení. Výchozí hodnota je `false`.|  
|`ipProtectionLevel`|Určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket. Výchozí hodnota závisí na verzi Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy se používají k určení výchozí chování týkající se použití portů dokončení třídy v <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Dokončení porty se doporučuje pro aplikace s vysokým výkonem serveru.  
  
 Výchozí hodnota `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy je **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForAccept` atribut z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForConnect` atribut z příslušných konfiguračních souborů.  
  
 `ipProtectionLevel` Atribut specifikuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost umožňuje konfiguraci toho, omezení pro soket IPv6 do zadaného oboru, například adresy se stejným propojit místní nebo lokality místní předponu. Tato možnost umožňuje aplikacím umístit omezení přístupu pro sokety IPv6. Taková omezení povolit aplikaci spuštěnou v privátní síti LAN jednoduše a robustně Posilte zabezpečení samotného externí útoky. Tato možnost rozšiřuje nebo rozsahu oboru naslouchání soketu, takže neomezený přístup z veřejné a soukromé uživatele v případě potřeby nebo omezení přístupu jenom ke stejné lokalitě, podle potřeby.  
  
 To `ipProtectionLevel` atribut nastavení má vliv počáteční příchozí provoz:  
  
-   Server TCP naslouchání pro příchozí spojení na soket.  
  
-   Aplikace UDP příjem paketů pro soket.  
  
 Toto nastavení nemá vliv na už navázané připojení TCP (v obou směrech je neomezený přenos) a nemá vliv na aplikace odešle pakety UDP.  
  
 Možné hodnoty parametru `ipProtectionLevel` nastavení atributu nekorespondují s definovanou úrovní podle <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> výčet následujícím způsobem:  
  
|**Hodnota atributu**|**Popis**|  
|-|-|  
|EdgeRestricted|Úroveň ochrany IP je edge s omezením pomocí specifikátoru. Tato hodnota se použije u aplikací, které jsou navržené tak, aby provoz přes Internet. Toto nastavení není povoleno procházení překladu adres (NAT) pomocí implementace Windows Teredo. Tyto aplikace mohou obejít brány firewall protokolu IPv4, takže aplikace musí být posílené už před útoky z Internetu zaslaných je otevřený port. V systému Windows Server 2003 a Windows XP je výchozí hodnotu pro úroveň ochrany IP na soketu edge s omezením pomocí specifikátoru.|  
|s omezením pomocí specifikátoru|Úroveň ochrany IP je omezen. Tato hodnota se použije ve intranetové aplikace, které neimplementují scénáře Internetu. Tyto aplikace nejsou obecně testovat nebo posílené už před útoky na Internetu – vizuální styl. Toto nastavení omezí přijaté přenosy do link-local pouze.|  
|Neomezená|Úroveň ochrany IP neomezený. Tato hodnota se použije aplikace, které jsou navržené tak, aby provoz přes Internet, jako jsou třeba aplikace s využitím integrované možnosti procházení překladu adres IPv6 do Windows (například Teredo). Tyto aplikace mohou obejít brány firewall protokolu IPv4, takže aplikace musí být posílené už před útoky z Internetu zaslaných je otevřený port. V systému Windows Server 2008 R2 a Windows Vista je výchozí hodnotu pro úroveň ochrany IP na soketu neomezený.|  
|Tento parametr zadán|Úroveň ochrany IP není zadána. Ve Windows 7 a Windows Server 2008 R2 neurčená výchozí hodnotu pro úroveň ochrany IP pro soket.|  
  
 Výchozí hodnota `ipProtectionLevel` atribut je **nespecifikovaný**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost lze použít k získání aktuální hodnoty `ipProtectionLevel` atribut z příslušných konfiguračních souborů.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat, že má být použita portů dokončení a že výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by měl neomezená.  
  
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
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
