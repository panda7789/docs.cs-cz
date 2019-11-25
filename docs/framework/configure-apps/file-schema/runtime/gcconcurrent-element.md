---
title: Element gcConcurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969231"
---
# <a name="gcconcurrent-element"></a>\<element > gcConcurrent

Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti v samostatném vlákně.

[konfigurační >\<](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent >

## <a name="syntax"></a>Syntaxe

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje, zda modul runtime současně spustí uvolňování paměti.|

#### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Nespustí souběžný sběr paměti.|
|`true`|Souběžně spustí uvolňování paměti. Toto nastavení je výchozí.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Před verzí .NET Framework 4 bylo podporováno souběžné uvolňování paměti pracovní stanice, které provedlo uvolňování paměti na pozadí v samostatném vlákně. V .NET Framework 4 se souběžné uvolňování paměti nahradilo pomocí GC na pozadí, které také provádí uvolňování paměti na pozadí v samostatném vlákně. Počínaje .NET Framework 4,5 se kolekce na pozadí stala k dispozici v uvolňování paměti serveru. Element **gcConcurrent** řídí, zda modul runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.

### <a name="to-disable-background-garbage-collection"></a>Zakázání uvolňování paměti na pozadí

> [!WARNING]
> Počínaje .NET Framework 4 je souběžné uvolňování paměti nahrazeno kolekcí paměti na pozadí. V dokumentaci .NET Framework se používají zaměnitelné a *pozadí* podmínek. Chcete-li zakázat uvolňování paměti na pozadí, použijte element **gcConcurrent** , jak je popsáno v tomto článku.

Ve výchozím nastavení používá modul runtime souběžné nebo pozadí uvolňování paměti, které je optimalizováno pro latenci. Pokud vaše aplikace zahrnuje těžkou interakci s uživatelem, nechte souběžné uvolňování paměti povolené, aby se minimalizovala doba pozastavení aplikace, aby se provádělo uvolňování paměti. Pokud nastavíte atribut `enabled` elementu **gcConcurrent** na `false`, modul runtime používá nesouběžné uvolňování paměti, které je optimalizováno pro propustnost.

Následující konfigurační soubor zakáže uvolňování paměti na pozadí:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Pokud je v konfiguračním souboru počítače **NagcConcurrentSettingé** nastavení, definuje se výchozí hodnota pro všechny aplikace .NET Framework. Nastavení konfiguračního souboru počítače přepisuje nastavení konfiguračního souboru aplikace.

Další informace o souběžném a uvolňování paměti na pozadí najdete v částech [souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [uvolňování paměti pracovní stanice na pozadí](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)a [uvolňování paměti serveru na pozadí](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) v článku [Základy uvolňování](../../../../standard/garbage-collection/fundamentals.md) paměti.

## <a name="example"></a>Příklad

Následující příklad povoluje uvolňování paměti na pozadí:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Základy kolekce paměti](../../../../standard/garbage-collection/fundamentals.md)
