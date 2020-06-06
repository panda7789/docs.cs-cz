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
ms.openlocfilehash: 23633cb282b8e59b4df4bcc2cd38717d805a207e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117501"
---
# <a name="disablecachingbindingfailures-element"></a>Element \<disableCachingBindingFailures>
Určuje, jestli se má zakázat ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Požadovaný atribut.<br /><br /> Určuje, jestli se má zakázat ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Description|  
|-----------|-----------------|  
|0|Nepovolujte ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování. Toto je výchozí chování vazby počínaje .NET Framework verze 2,0.|  
|1|Zakáže ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování. Toto nastavení se vrátí k chování vazby .NET Framework verze 1,1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 .NET Framework počínaje verzí 2,0 je výchozím chováním při načítání sestavení ukládání do mezipaměti všech vazeb a selhání načítání. To znamená, že pokud se pokus o načtení sestavení nezdaří, následné požadavky na načtení stejného sestavení okamžitě selžou bez nutnosti najít sestavení. Tento prvek zakáže toto výchozí chování pro chyby vazby, ke kterým dojde, protože sestavení nebylo nalezeno v cestě zjišťování. Tyto chyby vyvolávají vyvolání <xref:System.IO.FileNotFoundException> .  
  
 Některá vazba a selhání načítání nejsou ovlivněny tímto elementem a jsou vždy ukládány do mezipaměti. K těmto selháním dochází, protože bylo nalezeno sestavení, ale nebylo možné ho načíst. Vyvolávají <xref:System.BadImageFormatException> nebo <xref:System.IO.FileLoadException> . Následující seznam obsahuje některé příklady takových selhání.  
  
- Pokud se pokusíte načíst soubor není platným sestavením, následné pokusy o načtení sestavení selžou i v případě, že je chybný soubor nahrazen správným sestavením.  
  
- Pokud se pokusíte načíst sestavení, které je uzamčeno systémem souborů, následné pokusy o načtení sestavení selžou i poté, co je sestavení uvolněno systémem souborů.  
  
- Pokud je jedna nebo více verzí sestavení, které se pokoušíte načíst, v cestě zjišťování, ale konkrétní verze, kterou požadujete, není mimo ně, následné pokusy o načtení této verze selžou, i když je správná verze přesunuta do cesty pro zjišťování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat ukládání neúspěšných vazeb sestavení do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md)
