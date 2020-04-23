---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102889"
---
# <a name="gccpugroup-element"></a>\<Prvek> skupiny GCCpuGroup

Určuje, zda uvolňování paměti podporuje více skupin procesoru.

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>GCCpuGroup**

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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda uvolňování paměti podporuje více skupin procesoru.|

## <a name="enabled-attribute"></a>Atribut enabled

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Uvolňování paměti nepodporuje více skupin procesoru. Toto nastavení je výchozí.|
|`true`|Uvolňování paměti podporuje více skupin procesoru, pokud je povoleno uvolňování paměti serveru.|

### <a name="child-elements"></a>Podřízené elementy

Žádné.

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Pokud má počítač více skupin procesoru a je povoleno uvolňování paměti serveru (viz [ \<gcServer>](gcserver-element.md) element), povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru a bere v úvahu všechna jádra při vytváření a vyvažování hromady.

> [!NOTE]
> Tento prvek platí pouze pro vlákna uvolňování paměti. Chcete-li povolit runtime distribuovat vlákna uživatelů ve všech skupinách procesoru, musíte také povolit [ \<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) prvek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesoru.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma nastavení běhu](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Zakázat souběžné uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Uvolňování paměti pracovní stanice a serveru](../../../../standard/garbage-collection/workstation-server-gc.md)
