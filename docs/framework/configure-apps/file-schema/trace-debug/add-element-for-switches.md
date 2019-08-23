---
title: <add> – element pro <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 8fcd5cbe63a323a7509f5ff8c615364295c244d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920546"
---
# <a name="add-element-for-switches"></a>\<Přidat > element pro \<přepínače >
Určuje úroveň, kde je nastaven přepínač trasování.  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<přepne >  
\<add>  
  
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
|**name**|Požadovaný atribut.<br /><br /> Určuje název přepínače. Hodnota tohoto atributu odpovídá parametru *DisplayName* , který je předán konstruktoru Switch.|  
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
 Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru. Pokud je <xref:System.Diagnostics.BooleanSwitch>přepínač, můžete ho zapnout nebo vypnout. Pokud je <xref:System.Diagnostics.TraceSwitch>přepínač, můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv výstupem aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak <xref:System.Diagnostics.TraceLevel> použít `Data` `General`  **\<element add >** pro nastavení přepínače trasování na úroveň a povolení logického sledovacího přepínače.  
  
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
