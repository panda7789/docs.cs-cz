---
title: Element <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb4d0ed5b33170c40aacb32bebbf1b59ca659be4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252619"
---
# <a name="etwenable-element"></a>\<etwEnable – element >
Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<etwEnabled >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Požadovaný atribut.<br /><br /> Určuje, zda má být povoleno trasování událostí pro Windows.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|true|Povolte trasování událostí pro Windows. Toto je výchozí nastavení pro verze Windows počínaje operačními systémy Windows Vista a Windows Server 2008.|  
|false|Zakažte trasování událostí pro Windows. Toto je výchozí nastavení pro dřívější verze systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje systémem Windows Vista je ETW ve výchozím nastavení povolená. Tento prvek použijte k zakázání ETW pro aplikaci. V dřívějších verzích Windows použijte tento prvek k povolení ETW pro aplikaci.  
  
> [!NOTE]
> ETW lze povolit nebo zakázat globálně na serveru pomocí nastavení registru. Viz [řízení protokolování .NET Framework](../../../performance/controlling-logging.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit trasování ETW pro aplikaci.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Řízení přihlašování rozhraní .NET Framework](../../../performance/controlling-logging.md)
