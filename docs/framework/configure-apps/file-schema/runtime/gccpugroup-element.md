---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56b23b6d5fca6d0527d509c9b6a6fc6dd82336
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920785"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup – element >

Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.

\<> Konfigurace \
\<běhové > \
\<GCCpuGroup>

## <a name="syntax"></a>Syntaxe

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.|

## <a name="enabled-attribute"></a>Atribut enabled

|Value|Popis|
|-----------|-----------------|
|`false`|Uvolňování paměti nepodporuje více skupin PROCESORů. Toto nastavení je výchozí.|
|`true`|Uvolňování paměti podporuje více skupin PROCESORů, pokud je povoleno shromažďování paměti serveru.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Pokud je v počítači více skupin procesorů a uvolňování paměti serveru (viz [ \<gcServer >](gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU a při vytváření a zabere všechny jádra do účtu. vyvážení hald.

> [!NOTE]
> Tento prvek se vztahuje pouze na vlákna uvolňování paměti. Chcete-li povolit modulu runtime pro distribuci uživatelských vláken napříč všemi skupinami procesorů, je [ \<](thread-useallcpugroups-element.md) nutné povolit také > element Thread_UseAllCpuGroups.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin PROCESORů.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Zakázání souběžného uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Uvolnění paměti pracovní stanice a serveru](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
