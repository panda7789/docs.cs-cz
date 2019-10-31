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
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117477"
---
# <a name="disablecommitthreadstack-element"></a>\<element > disableCommitThreadStack
Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|umožněn|Požadovaný atribut.<br /><br /> Určuje, zda je potvrzování zásobníku úplného vlákna při spuštění vlákna (výchozí chování) zakázáno.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0,8|Nepovolujte výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.|  
|první|Zakáže výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.|  
  
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
> Nespravované hostitele můžou použít příznak spuštění `STARTUP_DISABLE_COMMITTHREADSTACK` ve výčtu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) k dosažení stejného výsledku.  
  
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
