---
title: gcConcurrent Element
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400041"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> element

Určuje, zda soubor RUNTIME společného jazyka spustí uvolňování paměti v samostatném vlákně.

[\<>konfigurace](../configuration-element.md)\
&nbsp;&nbsp;[\<>za běhu](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>Syntaxe

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje, zda běhový čas spouští souběžné uvolňování paměti.|

#### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Nespustí uvolňování paměti současně.|
|`true`|Souběžně spustí uvolňování paměti. Toto nastavení je výchozí.|

### <a name="child-elements"></a>Podřízené prvky

Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Před rozhraním .NET Framework 4 uvolňování paměti pracovní stanice podporovalo souběžné uvolňování paměti, které provedlo uvolňování paměti na pozadí v samostatném vlákně. V rozhraní .NET Framework 4 bylo souběžné uvolňování paměti nahrazeno gc na pozadí, který také provádí uvolňování paměti na pozadí v samostatném vlákně. Počínaje rozhraním .NET Framework 4.5 je kolekce na pozadí dostupná v uvolňování paměti serveru. Prvek **gcConcurrent** určuje, zda runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.

### <a name="to-disable-background-garbage-collection"></a>Zakázání uvolňování paměti na pozadí

> [!WARNING]
> Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí. Termíny *souběžné* a *pozadí* se používají zaměnitelně v dokumentaci rozhraní .NET Framework. Chcete-li zakázat uvolňování paměti na pozadí, použijte **gcConcurrent** element, jak je popsáno v tomto článku.

Ve výchozím nastavení používá runtime souběžné nebo pozadí uvolňování paměti, který je optimalizován pro latenci. Pokud vaše aplikace zahrnuje náročnou interakci uživatele, ponechte souběžné uvolňování paměti povoleno minimalizovat dobu pozastavení aplikace k provedení uvolňování paměti. Pokud nastavíte `enabled` atribut **gcConcurrent** `false`element , runtime používá non-souběžné uvolňování paměti, který je optimalizován pro propustnost.

Následující konfigurační soubor zakáže uvolňování paměti na pozadí:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Pokud je v konfiguračním souboru počítače nastaveno **gcConcurrentSetting,** definuje výchozí hodnotu pro všechny aplikace rozhraní .NET Framework. Nastavení konfiguračního souboru počítače přepíše nastavení konfiguračního souboru aplikace.

Další informace o souběžné a pozadí uvolňování paměti naleznete [v části Souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), uvolňování paměti pracovní stanice na [pozadí](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)a uvolňování paměti serveru [na pozadí](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) v článku [Základy uvolňování paměti.](../../../../standard/garbage-collection/fundamentals.md)

## <a name="example"></a>Příklad

Následující příklad umožňuje uvolňování paměti na pozadí:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Základy kolekce paměti](../../../../standard/garbage-collection/fundamentals.md)
