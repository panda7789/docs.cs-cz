---
title: Element <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba411114bfb853e06c83adb42713d43f1452d9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135067"
---
# <a name="etwenable-element"></a>\<etwenable – > – Element
Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro common language runtime události.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<etwEnabled>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Povoleno|Požadovaný atribut.<br /><br /> Určuje, zda by měly být povolené trasování událostí pro Windows.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|true|Povolte trasování událostí pro Windows. Toto je výchozí verze Windows od verze operačních systémů Windows Vista a Windows Server 2008.|  
|false|Zakážete trasování událostí pro Windows. Toto je výchozí hodnota u starších verzí systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze Windows Vista, je ve výchozím nastavení povolené trasování událostí pro Windows. Tento element slouží k zakázání trasování událostí pro Windows pro aplikaci. V dřívějších verzích Windows použijte tento prvek povolit trasování událostí pro Windows pro aplikaci.  
  
> [!NOTE]
>  Trasování událostí pro Windows můžete povolit nebo zakázat globálně na serveru s použitím nastavení registru. Zobrazit [řízení přihlašování rozhraní .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit trasování událostí pro Windows pro aplikaci.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Řízení přihlašování rozhraní .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
