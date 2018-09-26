---
title: '&lt;Odebrat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f885416629ae58949cc688f4e6fbd41e77e872aa
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071715"
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
 [\<namedcaches – > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
