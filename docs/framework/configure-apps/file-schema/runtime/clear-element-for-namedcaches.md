---
title: '&lt;Vymazat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ea860c185d68a24c31ec24de4a087b9b98fe791f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727804"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a>&lt;Vymazat&gt; – Element pro &lt;namedCaches&gt;
Vymaže všechny `namedCache` položky `namedCaches` kolekce pro mezipaměť.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 `None`  
  
### <a name="child-elements"></a>Podřízené elementy  
 `None`  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.|  
  
## <a name="remarks"></a>Poznámky  
 `clear` Element vymaže všechny `namedCache` položky v kolekci s názvem mezipaměti pro mezipaměť. Můžete použít `clear` prvek před použitím `add` prvek, který chcete přidat novou položku pojmenovanou mezipaměť, aby bylo možné je potřeba mít jistotu, neexistují žádné jiné s názvem mezipaměti v kolekci.  
  
## <a name="see-also"></a>Viz také:
- [\<namedcaches – > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
