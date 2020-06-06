---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102889"
---
# <a name="gccpugroup-element"></a>Element \<GCCpuGroup>

Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

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

|Hodnota|Description|
|-----------|-----------------|
|`false`|Uvolňování paměti nepodporuje více skupin PROCESORů. Toto nastavení je výchozí.|
|`true`|Uvolňování paměti podporuje více skupin PROCESORů, pokud je povoleno shromažďování paměti serveru.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Pokud je v počítači více skupin PROCESORů a uvolňování paměti serveru (viz [\<gcServer>](gcserver-element.md) element), povolením tohoto elementu dojde k rozšíření uvolňování paměti napříč všemi skupinami procesorů a při vytváření a vyrovnávání hald budou brát v úvahu všechny jádra.

> [!NOTE]
> Tento prvek se vztahuje pouze na vlákna uvolňování paměti. Chcete-li povolit modulu runtime pro distribuci uživatelských vláken napříč všemi skupinami CPU, je nutné povolit také [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.

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

## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Zakázat souběžné uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Uvolnění paměti pracovní stanice a serveru](../../../../standard/garbage-collection/workstation-server-gc.md)
