---
title: Element <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115401"
---
# <a name="thread_useallcpugroups-element"></a>Element \<Thread_UseAllCpuGroups>

Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a>Syntaxe

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.|

## <a name="enabled-attribute"></a>Atribut enabled

|Hodnota|Description|
|-----------|-----------------|
|`false`|Modul runtime nedistribuuje spravovaná vlákna napříč více skupinami PROCESORů. Toto nastavení je výchozí.|
|`true`|Modul runtime distribuuje spravovaná vlákna napříč více skupinami PROCESORů, pokud má počítač více skupin PROCESORů a [\<GCCpuGroup>](gccpugroup-element.md) element je povolen.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Pokud má počítač více skupin PROCESORů, povolení tohoto elementu způsobí, že modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů. Chcete-li použít tuto funkci, je nutné povolit také [\<GCCpuGroup>](gccpugroup-element.md) element, který rozšiřuje uvolňování paměti do všech skupin CPU a při vytváření a vyrovnávání haldy bere v úvahu všechny jádra. Povolení [\<GCCpuGroup>](gccpugroup-element.md) elementu vyžaduje povolení [\<gcServer>](gcserver-element.md) prvku. Pokud tyto prvky nejsou povoleny, povolení `<Thread_UseAllCpuGroups>` prvku nemá žádný vliv.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak povolit podporu více skupin PROCESORů.

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<GCCpuGroup>Objekt](gccpugroup-element.md)
