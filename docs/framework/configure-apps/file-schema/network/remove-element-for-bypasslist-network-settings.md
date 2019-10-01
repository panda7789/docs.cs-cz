---
title: <remove> – element pro bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697895"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>@no__t – element > 0remove pro BypassList (nastavení sítě)

Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.

[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**  

## <a name="syntax"></a>Syntaxe

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|**Atribut**|**Popis**|
|-------------------|---------------------|
|`address`|Regulární výraz popisující IP adresu nebo název DNS.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|**Element**|**Popis**|
|-----------------|---------------------|
|[bypasslist](bypasslist-element-network-settings.md)|Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.|

## <a name="remarks"></a>Poznámky

Element `remove` odstraní regulární výrazy popisující IP adresy nebo názvy serverů DNS ze seznamu adres, které obcházejí proxy server. Adresy byly definovány dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.

Hodnota atributu `address` by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.

Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Konfigurační soubory

Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).

## <a name="example"></a>Příklad

Následující příklad odebere předchozí definici pro doménu adventure-works.com a pak do seznamu pro obejití přidá doménu contoso.com.

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
