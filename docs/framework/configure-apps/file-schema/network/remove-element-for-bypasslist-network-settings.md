---
title: <remove> – element pro element bypasslist (nastavení sítě)
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
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354255"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>\<Odebrat > – Element pro bypasslist (nastavení sítě)

Odebere ze seznamu obcházení proxy IP adresu nebo název DNS.

\<Konfigurace > \
\<system.net>\
\<defaultProxy>\
\<bypasslist – > \
\<remove>

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
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.|

## <a name="remarks"></a>Poznámky

`remove` Element odebere regulární výrazy popisující IP adres nebo názvů DNS serverů v seznamu adres, které obcházejí proxy server. Adresy byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii configuration.

Hodnota `address` atribut musí být regulární výraz, který popisuje sadu IP adres nebo názvů hostitele.

Další informace o formátování regulárních výrazů naleznete v tématu. [Regulárních výrazech .NET Frameworku](../../../../../docs/standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Konfigurační soubory

Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).

## <a name="example"></a>Příklad

Následující příklad odebere všechny předchozí definice pro doménu společnosti adventure works.com a pak přidá do seznamu obcházení doménu contoso.com.

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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
