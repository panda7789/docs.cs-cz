---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116834"
---
# <a name="gccpugroup-element"></a>\<element > GCCpuGroup

Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**  

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

|Hodnota|Popis|
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

Pokud je v počítači více skupin PROCESORů a uvolňování paměti serveru (viz [\<gcServer >](gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU a při vytváření a zabere všechny jádra do účtu. vyvážení hald.

> [!NOTE]
> Tento prvek se vztahuje pouze na vlákna uvolňování paměti. Chcete-li modulu runtime povolit distribuci uživatelských vláken napříč všemi skupinami CPU, je nutné povolit také [\<prvek > Thread_UseAllCpuGroups](thread-useallcpugroups-element.md) .

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
