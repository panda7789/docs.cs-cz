---
title: Element <disableCachingBindingFailures>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c99eb6b77a969a1c5003743b0407821e2537b683
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289715"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures> Element
Určuje, zda chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<disableCachingBindingFailures>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Povoleno|Požadovaný atribut.<br /><br /> Určuje, zda chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Nezakazujte ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním. Toto je výchozí chování vazby od verze rozhraní .NET Framework verze 2.0.|  
|1|Zakáže ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním. Toto nastavení se vrátí k chování vazby rozhraní .NET Framework verze 1.1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework verze 2.0, je výchozí chování pro načtení sestavení do mezipaměti všechny vazby a načítání chyb. To znamená pokud se nezdaří pokus o načtení sestavení, následné žádosti k načtení stejné sestavení selhala okamžitě, bez jakékoli pokusy o nalezení sestavení. Tento prvek zakazuje výchozí chování pro vazbu, ke kterým dochází, protože sestavení nebyl nalezen v cestě k testování. Vyvolat tyto chyby <xref:System.IO.FileNotFoundException>.  
  
 Některé vazby a načítání selhání nevztahují na tento element a jsou vždy uloženy v mezipaměti. Tyto chyby dojít, protože sestavení nebyl nalezen, ale nelze jej načíst. Generují výjimku <xref:System.BadImageFormatException> nebo <xref:System.IO.FileLoadException>. Následující seznam obsahuje několik příkladů takových selhání.  
  
-   Při pokusu načíst soubor není platným sestavením, následné pokusy o načtení sestavení se nezdaří, i když chybný soubor nahradí správné sestavení.  
  
-   Při pokusu o načtení sestavení, které je uzamčen systému souborů, následné pokusy o načtení sestavení se nezdaří, i po sestavení je vydáno systémem souborů.  
  
-   Pokud je jeden nebo více verzí sestavení, které se pokoušíte načíst v cesta zjišťování, ale konkrétní verzi, které jste požádali, není mezi nimi, následné pokusy načíst tuto verzi se nezdaří, i v případě, že správná verze je přesunut do cesta zjišťování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat ukládání do mezipaměti selhání vazby sestavení, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
