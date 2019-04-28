---
title: Element <gcConcurrent>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674100"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> Element

Určuje, zda modul common language runtime spustí uvolnění paměti na samostatném vlákně.

\<Konfigurace > \
\<modul runtime > \
\<gcConcurrent>

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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime souběžně spustí uvolňování paměti.|

## <a name="enabled-attribute"></a>Atribut enabled

|Value|Popis|
|-----------|-----------------|
|`false`|Není souběžně spustit uvolňování paměti.|
|`true`|Uvolňování paměti běží souběžně. Toto nastavení je výchozí.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Před rozhraní .NET Framework 4 uvolnění paměti pracovní stanice nepodporuje souběžné uvolňování paměti, které provádí uvolňování paměti na pozadí v samostatném vlákně. Souběžné uvolňování paměti v rozhraní .NET Framework 4, byl nahrazen uvolňování paměti, který také provádí uvolňování paměti na pozadí v samostatném vlákně na pozadí. Od verze rozhraní .NET Framework 4.5, shromažďování na pozadí jsou dostupné v uvolňování paměti serveru. `<gcConcurrent>` Prvek určuje, zda modul runtime provádí buď souběžné nebo při uvolňování paměti na pozadí, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.

### <a name="to-disable-background-garbage-collection"></a>Zakázání uvolňování paměti na pozadí

> [!WARNING]
> Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí. Podmínky *souběžných* a *pozadí* zaměňují v dokumentaci k rozhraní .NET Framework. Chcete-li zakázat uvolňování paměti na pozadí, použijte `<gcConcurrent>` elementu, jak je popsáno v tomto článku.

Ve výchozím nastavení používá modul runtime souběžné nebo uvolňování paměti na pozadí, které je optimalizováno pro zpoždění. Pokud aplikace vyžaduje interakci uživatele náročné, nechte souběžné uvolňování paměti povoleno, chcete-li minimalizovat čas pozastavení aplikace pro provádění uvolnění. Pokud jste nastavili `enabled` atribut `<gcConcurrent>` element `false`, používá modul runtime nesouběžné uvolňování paměti, které je optimalizováno pro výkon. Následující konfigurační soubor zakáže uvolňování paměti na pozadí.

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 Pokud je `<gcConcurrentSetting>` nastavení v konfiguračním souboru počítače, definuje výchozí hodnotu pro všechny aplikace rozhraní .NET Framework. Nastavení konfiguračního souboru počítače přepíše nastavení konfiguračního souboru aplikace.

 Další informace o současných a uvolňování paměti na pozadí, najdete v článku [souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) tématu [základy kolekce paměti](../../../../standard/garbage-collection/fundamentals.md) článku.

## <a name="example"></a>Příklad

Následující příklad umožňuje souběžné uvolňování paměti:

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
