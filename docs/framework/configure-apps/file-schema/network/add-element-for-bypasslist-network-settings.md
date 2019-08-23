---
title: <add> – element pro bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: da234402c6ec7e2c1f85e4bd674517b1147f0d18
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927480"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<Přidat > element pro BypassList (nastavení sítě)
Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.  
  
 \<> Konfigurace  
\<system.net>  
\<defaultProxy>  
\<BypassList >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|**address**|Regulární výraz popisující IP adresu nebo název DNS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.|  
  
## <a name="remarks"></a>Poznámky  
 `add` Element vloží regulární výrazy popisující IP adresy nebo názvy serverů DNS na seznam adres, které obcházejí proxy server.  
  
 Hodnota `address` atributu by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.  
  
 Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění. Regulární výraz "[a-z] +\\. contoso\\. com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com. Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] +\\. contoso\\. com $".  
  
 Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá dvě adresy do seznamu pro obejití. První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
