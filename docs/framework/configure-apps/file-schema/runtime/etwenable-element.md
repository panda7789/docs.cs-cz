---
title: Element <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117397"
---
# <a name="etwenable-element"></a>Element \<etwEnable>
Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
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
  
|Hodnota|Description|  
|-----------|-----------------|  
|true|Povolte trasování událostí pro Windows. Toto je výchozí nastavení pro verze Windows počínaje operačními systémy Windows Vista a Windows Server 2008.|  
|false (nepravda)|Zakažte trasování událostí pro Windows. Toto je výchozí nastavení pro dřívější verze systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
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
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Řízení přihlašování rozhraní .NET Framework](../../../performance/controlling-logging.md)
