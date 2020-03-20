---
title: Element <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153227"
---
# <a name="switches-element"></a>\<přepínače> Element
Obsahuje přepínače trasování a úroveň, kde jsou přepínače trasování nastaveny.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<přepínače>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add-element-for-switches.md)|Určuje úroveň, na které je nastaven přepínač trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`System.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Úroveň trasovacího přepínače můžete změnit jeho vložením do konfiguračního souboru. Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch>, můžete jej zapínat a vypínat. Pokud je přepínač <xref:System.Diagnostics.TraceSwitch>, můžete mu přiřadit různé úrovně a určit typy trasovacích nebo ladicích zpráv, které aplikace vypíše.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí ** \<prvku switch>** nastavit <xref:System.Diagnostics.TraceLevel> přepínač `General` trasování `Data` na úroveň a povolit přepínač trasování logické.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [Trasování a ladění schématu nastavení](index.md)
