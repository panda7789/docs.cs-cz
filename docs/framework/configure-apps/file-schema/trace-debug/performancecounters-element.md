---
title: Element <performanceCounters>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697158"
---
# <a name="performancecounters-element"></a>Element \<performanceCounters>

Určuje velikost globální paměti sdílené čítači výkonu.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a>Syntaxe

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|filemappingsize|Požadovaný atribut.<br /><br /> Určuje velikost globální paměti sdílené čítači výkonu (v bajtech). Výchozí hodnota je 524288.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`system.diagnostics`|Určuje kořenový element konfiguračního oddílu ASP.NET.|

## <a name="remarks"></a>Poznámky

Čítače výkonu k publikování údajů o výkonu používají soubor mapované paměti nebo sdílenou paměť.  Velikost sdílené paměti určuje, kolik instancí lze najednou použít.  Existují dva typy sdílené paměti: globální sdílená paměť a samostatná sdílená paměť.  Globální sdílená paměť je používána všemi kategoriemi čítače výkonu nainstalovanými s verzemi .NET Framework 1,0 nebo 1,1.  Kategorie čítače výkonu nainstalované s .NET Framework verze 2,0 používají samostatnou sdílenou paměť, přičemž každá kategorie čítače výkonu má vlastní paměť.

Velikost globální sdílené paměti lze nastavit pouze pomocí konfiguračního souboru.  Výchozí velikost je 524 288 byes, maximální velikost je 33 554 432 bajtů a minimální velikost je 32 768 bajtů.  Vzhledem k tomu, že globální sdílená paměť je sdílena všemi procesy a kategorie, první tvůrce určuje velikost.  Pokud definujete velikost v konfiguračním souboru aplikace, bude tato velikost použita pouze v případě, že je vaše aplikace první aplikací, která způsobuje, že jsou čítače výkonu provedeny.  Proto je správné umístění pro určení `filemappingsize` hodnoty soubor Machine. config.  Paměť v globální sdílené paměti nemůže být uvolněna jednotlivými čítači výkonu, takže je nakonec vyčerpána globální sdílená paměť, pokud je vytvořen velký počet instancí čítače výkonu s různými názvy.

V případě velikosti samostatné sdílené paměti je nejprve odkazována hodnota DWORD FileMappingSize v HKEY_LOCAL_MACHINE klíči registru \\ *\<category name>* , za kterou následuje hodnota zadaná pro globální sdílenou paměť v konfiguračním souboru. Pokud hodnota FileMappingSize neexistuje, je velikost samostatné sdílené paměti nastavena na jednu čtvrtou (1/4) globální nastavení konfiguračního souboru.

## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
