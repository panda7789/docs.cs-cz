---
title: Element <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663426"
---
# <a name="thread_useallcpugroups-element"></a>\<Thread_UseAllCpuGroups – element >

Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.

\<> Konfigurace \
\<běhové > \
\<Thread_UseAllCpuGroups >

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

|Value|Popis|
|-----------|-----------------|
|`false`|Modul runtime nedistribuuje spravovaná vlákna napříč více skupinami PROCESORů. Toto nastavení je výchozí.|
|`true`|Modul runtime distribuuje spravovaná vlákna napříč více skupinami procesorů, pokud má počítač více skupin procesorů a [ \<](gccpugroup-element.md) je povolený element GCCpuGroup >.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Pokud má počítač více skupin PROCESORů, povolení tohoto elementu způsobí, že modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů. Chcete-li použít tuto funkci, je nutné povolit [ \<také prvek GCCpuGroup >](gccpugroup-element.md) , který rozšiřuje uvolňování paměti do všech skupin CPU a při vytváření a vyrovnávání haldy bere v úvahu všechny jádra. Povolení prvku [GCCpuGroup > vyžaduje povolení prvku > gcServer. \<](gccpugroup-element.md) [ \<](gcserver-element.md) Pokud tyto prvky nejsou povoleny, povolení `<Thread_UseAllCpuGroups>` prvku nemá žádný vliv.

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

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<GCCpuGroup – element >](gccpugroup-element.md)
