---
title: Element <gcServer>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 98ecc7069df20a92492e9a6276a0d88331ccc0bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116660"
---
# <a name="gcserver-element"></a>\<element > gcServer
Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<gcServer >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime spouští uvolňování paměti serveru.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nespustí shromažďování paměti serveru. Toto nastavení je výchozí.|  
|`true`|Spustí shromažďování paměti serveru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, které je k dispozici ve všech systémech a uvolňování paměti serveru, které je k dispozici v systémech s více procesory. Pomocí elementu `<gcServer>` lze řídit typ uvolňování paměti, který modul CLR provede. Pomocí vlastnosti <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> určete, zda je povoleno uvolňování paměti serveru.  
  
 V případě počítačů s jedním procesorem by měla být výchozí kolekce uvolnění paměti pracovní stanice nejrychlejší možností. Pro počítače se dvěma procesory lze použít buď pracovní stanici, nebo server. Uvolňování paměti serveru by mělo být nejrychlejší možností pro více než dva procesory.  
  
 Tento element lze použít pouze v konfiguračním souboru aplikace; ignoruje se, pokud je v konfiguračním souboru počítače.  
  
> [!NOTE]
> V .NET Framework 4 a starších verzích není souběžné uvolňování paměti k dispozici, když je povoleno uvolňování paměti serveru. Počínaje .NET Framework 4,5 je shromažďování paměti serveru souběžné. Chcete-li použít nesouběžné uvolňování paměti serveru, nastavte prvek `<gcServer>` na hodnotu `true` a [\<prvek > gcConcurrent](gcconcurrent-element.md) na `false`.  
  
## <a name="example"></a>Příklad  
 Následující příklad povoluje uvolňování paměti serveru.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Zakázání souběžného uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
