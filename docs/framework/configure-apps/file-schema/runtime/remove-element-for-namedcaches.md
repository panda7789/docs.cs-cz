---
title: '&lt;Odebrat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d31caf88e1376025484ed6d65d5277c015e70b5e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613736"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a>&lt;Odebrat&gt; – Element pro &lt;namedCaches&gt;
Odebere položku pojmenovanou mezipaměť z `namedCaches` kolekce pro mezipaměť.  
  
 \<system.runtime.caching>  
\<memoryCache >  
\<namedcaches – >  
\<Odebrat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
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
 `remove` Odebere element `namedCache` položku z kolekce s názvem mezipaměti pro mezipaměť.  
  
## <a name="see-also"></a>Viz také  
- [\<namedcaches – > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
