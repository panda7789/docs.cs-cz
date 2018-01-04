---
title: "&lt;disablecachingbindingfailures –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd86bc2f58bc216f741c32a51925d3f4f8ef47df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disablecachingbindingfailures –&gt; – Element
Určuje, jestli chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen ve zjišťování.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<disablecachingbindingfailures – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, jestli chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen ve zjišťování.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Nezakazujte ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen pomocí zjišťování. Toto je výchozí chování vazby od verze rozhraní .NET Framework verze 2.0.|  
|1|Zakážete ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen pomocí zjišťování. Toto nastavení se vrátí do chování vazby rozhraní .NET Framework verze 1.1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework verze 2.0, je výchozí chování pro načtení sestavení do mezipaměti všechny vazby a načítání selhání. To znamená pokud se nezdaří pokus o načtení sestavení, další žádost o načtení do stejného sestavení nezdaří okamžitě, bez jakékoli pokus o vyhledání sestavení. Tento element zakáže výchozí chování pro vazby, ke kterým dochází, protože sestavení nebyl nalezen v cestě k testování. Throw – selhání <xref:System.IO.FileNotFoundException>.  
  
 Některé vazby a načítání selhání nemá vliv tohoto elementu a vždy v mezipaměti. Selhání dojít, protože sestavení nebyl nalezen, ale nebylo možné načíst. Vyvolají <xref:System.BadImageFormatException> nebo <xref:System.IO.FileLoadException>. Následující seznam obsahuje některé příklady takových selhání.  
  
-   Když se pokusí načíst soubor není platným sestavením, následných pokusů o načtení sestavení selže i v případě chybného souboru se nahradí správná sestavení.  
  
-   Při pokusu o načtení sestavení, které je uzamčený systému souborů následné pokusy o načtení sestavení selže i po vydání sestavení pomocí systému souborů.  
  
-   Pokud je jeden nebo více verzí sestavení, které se pokoušíte načíst v cestě k testování, ale není mezi nimi konkrétní verzi, kterou jste požádali, následné pokusy o spouštění této verze selže i v případě správnou verzi přesunete do testování cestu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat ukládání do mezipaměti selhání vazby sestavení, ke kterým dochází, protože sestavení nebyl nalezen pomocí zjišťování.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
