---
title: '&lt;disableCommitThreadStack&gt; Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b02a5365aa2dc2292b0917820782405ba35ad92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534066"
---
# <a name="ltdisablecommitthreadstackgt-element"></a>&lt;disableCommitThreadStack&gt; Element
Určuje, zda je zásobníku úplného vlákna potvrzeny při spuštění vlákna.  
  
 \<Konfigurace >  
\<modul runtime >  
\<disableCommitThreadStack>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Povoleno|Požadovaný atribut.<br /><br /> Určuje, zda je zakázaný potvrzení zásobníku úplného vlákna při spuštění vlákna (výchozí chování).|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Nezakazujte výchozí chování modulu common language runtime, který je pro potvrzení zásobníku úplného vlákna při spuštění vlákna.|  
|1|Zakážete výchozí chování modulu common language runtime, který je pro potvrzení zásobníku úplného vlákna při spuštění vlákna.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový element v každém konfiguračním souboru, který používá modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikací.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování modulu common language runtime je potvrzení změn zásobníku úplného vlákna při spuštění vlákna. Pokud velký počet vláken musí být vytvořen na serveru, který má omezené paměti a většina tato vlákna budou používat velmi málo místa zásobníku, server může být lepší provedeno, zda modul common language runtime nesměrují zásobníku úplného vlákna ihned po vlákno st uštění.  
  
> [!NOTE]
>  Můžete použít nespravovaným hostitelům `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění v [startup_flags –](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčet k dosažení stejného výsledku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat výchozí chování modulu common language runtime, což je potvrzení změn zásobníku úplného vlákna při spuštění vlákna.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
