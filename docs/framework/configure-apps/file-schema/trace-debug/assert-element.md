---
title: Element <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088938"
---
# <a name="assert-element"></a>Element \<assert>
Určuje, zda se má při volání metody zobrazit okno se zprávou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> . určuje také název souboru, do kterého budou zapsány zprávy.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`assertuienabled`|Nepovinný atribut.<br /><br /> Určuje, zda se má zobrazit okno se zprávou, když je metoda **Debug. Assert** vyhodnocena jako **false**.|  
|`logfilename`|Nepovinný atribut.<br /><br /> Určuje název souboru, do kterého se má zpráva zapsat, pokud je hodnota **Debug. Assert** vyhodnocena jako **false**.|  
  
## <a name="assertuienabled-attribute"></a>AssertUiEnabled – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`true`|Zobrazí okno se zprávou. Toto nastavení je výchozí.|  
|`false`|Nezobrazuje okno se zprávou.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Oba atributy v **\<assert>** elementu jsou volitelné. Okna se zprávou můžete zakázat bez určení souboru, do kterého se mají zprávy zapisovat, nebo můžete zadat soubor, do kterého se mají zapisovat zprávy, a nechat okna zpráv zapnutá.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat zobrazování oken zpráv při volání metody **Debug. Assert** a zapsat zprávy do `c:\log.txt` .  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Debug>
- [Trasování a ladění schématu nastavení](index.md)
