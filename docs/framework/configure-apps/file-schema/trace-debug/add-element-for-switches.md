---
title: <add> – element pro <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 2edc890049d62913d693ad61d8d814d012c0f482
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697182"
---
# <a name="add-element-for-switches"></a>> element \<add pro \<switches >
Určuje úroveň, kde je nastaven přepínač trasování.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<switches >** ](switches-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**  
  
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
|**value**|Požadovaný atribut.<br /><br /> Určuje úroveň přepínače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`switches`|Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru. Pokud je přepínačem <xref:System.Diagnostics.BooleanSwitch>, můžete ho zapnout nebo vypnout. Pokud je přepínačem <xref:System.Diagnostics.TraceSwitch>, můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv pro výstup aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít > prvek **\<add** k nastavení sledovacího přepínačů `General` na úroveň <xref:System.Diagnostics.TraceLevel> a povolení logického přepínače `Data`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [Trasování a ladění schématu nastavení](index.md)
