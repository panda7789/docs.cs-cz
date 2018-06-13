---
title: '&lt;disablecommitthreadstack –&gt; – Element'
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
ms.openlocfilehash: 4d8724d16a25cdec040fa5b1f5472da06b11f669
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752660"
---
# <a name="ltdisablecommitthreadstackgt-element"></a>&lt;disablecommitthreadstack –&gt; – Element
Určuje, jestli je úplná vlákno zásobníku potvrzeny při spuštění vlákna.  
  
 \<Konfigurace >  
\<modul runtime >  
\<disablecommitthreadstack – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, zda je zakázána potvrzení zásobníku úplné vlákno při spuštění vlákna (výchozí nastavení).|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Nezakazujte výchozí chování modul common language runtime, který je při spuštění vlákna potvrzení zásobníku úplný přístup z více vláken.|  
|1|Zakážete výchozí chování modul CLR, což je potvrzení zásobníku úplné vlákno při spuštění vlákna.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový element v každém konfiguračním souboru, který používá modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikace.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování modul common language runtime je potvrzení zásobníku úplné vlákno při spuštění vlákna. Pokud velký počet vláken, je nutné vytvořit na serveru, která má omezenou paměti a většinu těchto vláken použije velmi málo místa zásobníku, server může fungovat lépe modul common language runtime nesměrují zásobníku úplné vlákno okamžitě po vlákno st arted.  
  
> [!NOTE]
>  Nespravované hostitelů můžete použít `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění v [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu k dosažení stejného výsledku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat výchozí chování modul CLR, což je potvrzení zásobníku úplné vlákno při spuštění přístup z více vláken.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
