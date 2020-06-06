---
title: <Crst_DisableSpinWait> – element
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117640"
---
# <a name="crst_disablespinwait-element"></a>\<Crst_DisableSpinWait> – element

Určuje, jestli se má v případě, že se má v případě, že je to zamýšlí, zakázat číselník čekání  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**umožněn**|Určuje, jestli jsou zakázané oddíly, které čekají na kritické, pokud jsou zakázané.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Description|  
|-----------|-----------------|  
|1|Zakažte číselník čekání, pokud nelze získat kritickou sekci.|  
|0|Nepovolujte číselník čekání, pokud nelze získat kritickou sekci. Toto je výchozí hodnota.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o různých nastaveních konfigurace modulu runtime.|  
  
## <a name="example"></a>Příklad  

Následující příklad v případě, že je to zamýšlí, zakáže v částech kritické čekání.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
