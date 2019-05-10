---
title: element < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754671"
---
# <a name="crstdisablespinwait-element"></a>\<Crst_DisableSpinWait > – element

Určuje, zda chcete zakázat typu číselník – časový limit na kritický oddíl, když ve sporných.  
  
 \<Konfigurace >  
\<modul runtime >  
\<Crst_DisableSpinWait>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Povoleno**|Určuje, zda číselník – časový limit na kritické oddíly, když jsou jejich ve sporných zakázána.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|1|Zakážete typu číselník čekání, když kritický oddíl nelze získat.|  
|0|Nezakazujte čekání typu číselník při kritický oddíl nelze získat. Jedná se o výchozí hodnotu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o různých nastavení konfigurace modulu runtime.|  
  
## <a name="example"></a>Příklad  

Následující příklad zakazuje typu číselník čekání v kritických oddílů, když ve sporných.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
