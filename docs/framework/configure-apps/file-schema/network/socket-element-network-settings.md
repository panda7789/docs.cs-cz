---
title: "&lt;Socket&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fefb8e119d428d86501e1c8cdd5eec5ef0809cbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;Socket&gt; – Element (nastavení sítě)
Určuje, zda operace soketu používat porty dokončení.  
  
 \<Konfigurace >  
\<System.NET >  
\<Nastavení >  
\<Socket >  
  
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
|`alwaysUseCompletionPortsForAccept`|Označuje, zda soket měli vždycky používat dokončení porty pro volání metod přijmout. Výchozí hodnota je `false`.|  
|`alwaysUseCompletionPortsForConnect`|Označuje, zda soket měli vždycky používat dokončení porty pro volání metod připojit. Výchozí hodnota je `false`.|  
|`ipProtectionLevel`|Určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket. Výchozí hodnota závisí na verzi systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy se používají k určení výchozího chování týkající se použití dokončení portů pomocí třídy v <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Dokončení porty – se doporučují pro vysoký výkon serverových aplikací.  
  
 Výchozí hodnota `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy je **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Můžete použít k získání aktuální hodnota `alwaysUseCompletionPortsForAccept` atribut z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Můžete použít k získání aktuální hodnota `alwaysUseCompletionPortsForConnect` atribut z příslušných konfiguračních souborů.  
  
 `ipProtectionLevel` Atribut určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost umožňuje konfigurovat omezení soketu IPv6 pro zadaný rozsah oboru, například adresy se stejným propojit místní nebo lokality místní předponu. Tato možnost umožňuje aplikacím umístit omezení přístupu na IPv6 sockets. Takové omezení povolit aplikace spuštěna v privátní síti LAN jednoduše a robustní posílení samotné proti útokům na externí. Tato možnost rozšiřuje nebo zužuje oblast naslouchání soketu a povolení neomezený přístup z veřejné a soukromé uživatele v případě nutnosti nebo omezení přístupu jenom do stejné lokality, podle potřeby.  
  
 To `ipProtectionLevel` atribut nastavení má vliv počáteční příchozí provoz:  
  
-   Server TCP naslouchá pro příchozí spojení na soket.  
  
-   UDP aplikace, který přijímá paket na soketu.  
  
 Toto nastavení nemá vliv již navázáno připojení TCP (provoz je neomezený v obou směrech) a nemá vliv na aplikaci odesílání UDP paketů.  
  
 Možné hodnoty `ipProtectionLevel` nastavení atributu odpovídají s úrovněmi ochrany definované zadané v <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> výčtu následujícím způsobem:  
  
|**Hodnota atributu**|**Popis**|  
|-|-|  
|EdgeRestricted|Úroveň ochrany IP je hraniční omezený. Tato hodnota se použije aplikace navržené tak, aby provoz přes Internet. Toto nastavení neumožňuje traversal překlad adres (NAT) pomocí implementace Teredo systému Windows. Tyto aplikace mohou obejít brány firewall IPv4, takže aplikace musí být zesílené zabezpečení proti útokům na Internetu přesměrován na otevřen port. V systému Windows Server 2003 a Windows XP je výchozí hodnota pro úroveň ochrany IP na soket edge omezený.|  
|Omezený|Úroveň ochrany IP je omezen. Tato hodnota se použije intranetu aplikace, které neimplementují scénáře Internetu. Tyto aplikace nejsou obvykle testována nebo zesílené zabezpečení proti útokům na Internetu stylu. Toto nastavení omezí přijaté přenosy do link-local jenom.|  
|Bez omezení|Úroveň ochrany IP není omezeno. Tato hodnota se použije aplikace navržené tak, aby provoz přes Internet, včetně aplikací s využitím možnosti traversal IPv6 NAT do systému Windows (například Teredo). Tyto aplikace mohou obejít brány firewall IPv4, takže aplikace musí být zesílené zabezpečení proti útokům na Internetu přesměrován na otevřen port. Na Windows Server 2008 R2 a Windows Vista je výchozí hodnota pro úroveň ochrany IP na soket bez omezení.|  
|Tento parametr|Úroveň ochrany IP neurčená. V systému Windows 7 a Windows Server 2008 R2 je výchozí hodnota pro úroveň ochrany IP na soket neurčené.|  
  
 Výchozí hodnota `ipProtectionLevel` atribut je **nespecifikovaný**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost lze použít k získání aktuální hodnota `ipProtectionLevel` atribut z příslušných konfiguračních souborů.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že má být použita dokončení porty a že výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by měl neomezený.  
  
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
