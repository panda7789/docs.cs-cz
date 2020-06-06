---
title: <add> – element pro <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088959"
---
# <a name="add-element-for-switches"></a>\<add> – element pro \<switches>
Určuje úroveň, kde je nastaven přepínač trasování.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Jméno**|Požadovaný atribut.<br /><br /> Určuje název přepínače. Hodnota tohoto atributu odpovídá parametru *DisplayName* , který je předán konstruktoru Switch.|  
|**osa**|Požadovaný atribut.<br /><br /> Určuje úroveň přepínače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`switches`|Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru. Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch> , můžete ho zapnout nebo vypnout. Pokud je přepínač <xref:System.Diagnostics.TraceSwitch> , můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv výstupem aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít **\<add>** prvek pro nastavení `General` přepínače trasování na <xref:System.Diagnostics.TraceLevel> úroveň a povolení `Data` logického sledovacího přepínače.  
  
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
