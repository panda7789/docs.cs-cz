---
title: Element <disableCommitThreadStack>
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
ms.openlocfilehash: 2fa32d64f3ce440981c5f26d731051a118ed9254
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252672"
---
# <a name="disablecommitthreadstack-element"></a>\<disableCommitThreadStack – element >
Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Požadovaný atribut.<br /><br /> Určuje, zda je potvrzování zásobníku úplného vlákna při spuštění vlákna (výchozí chování) zakázáno.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|0|Nepovolujte výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.|  
|1|Zakáže výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozím chováním modulu CLR (Common Language Runtime) je zápis úplného zásobníku vlákna při spuštění vlákna. Pokud je třeba vytvořit velký počet vláken na serveru, který má omezené množství paměti, a většina těchto vláken bude používat velmi málo prostoru zásobníku, server může být lepší, pokud modul CLR (Common Language Runtime) nepotvrdí plný zásobník vláken okamžitě, když je vlákno St. arted.  
  
> [!NOTE]
> Nespravované hostitele můžou použít `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění ve výčtu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) k dosažení stejného výsledku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat výchozí chování modulu CLR (Common Language Runtime), který slouží k potvrzení zásobníku úplného vlákna při spuštění vlákna.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
