---
title: Element gcServer
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968938"
---
# <a name="gcserver-element"></a>\<gcServer> – element

Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a>Syntaxe

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje, zda modul runtime spouští uvolňování paměti serveru.|

#### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Description|
|-----------|-----------------|
|`false`|Nespustí shromažďování paměti serveru. Toto nastavení je výchozí.|
|`true`|Spustí shromažďování paměti serveru.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Modul CLR (Common Language Runtime) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, které je k dispozici ve všech systémech a uvolňování paměti serveru, které je k dispozici v systémech s více procesory. Použijte element **gcServer** k řízení typu uvolňování paměti, který modul CLR provede. Pomocí <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> vlastnosti určíte, zda je povoleno uvolňování paměti serveru.

V případě počítačů s jedním procesorem by měla být výchozí kolekce uvolnění paměti pracovní stanice nejrychlejší možností. Pro počítače se dvěma procesory lze použít buď pracovní stanici, nebo server. Uvolňování paměti serveru by mělo být nejrychlejší možností pro více než dva procesory. Nejčastěji serverové systémy s více procesory zakazují použití GC serveru a místo toho používají GC z pracovní stanice, když mnoho instancí serverové aplikace běží na stejném počítači.

Tento element lze použít pouze v konfiguračním souboru aplikace; ignoruje se, pokud je v konfiguračním souboru počítače.

> [!NOTE]
> V .NET Framework 4 a starších verzích není souběžné uvolňování paměti k dispozici, když je povoleno uvolňování paměti serveru. Počínaje .NET Framework 4,5 je shromažďování paměti serveru souběžné. Chcete-li použít nesouběžné uvolňování paměti serveru, nastavte element **gcServer** na `true` a [element gcConcurrent](gcconcurrent-element.md) na `false` .

Počínaje .NET Framework 4.6.2 můžete ke konfiguraci GC serveru použít taky tyto prvky:

- [GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda existuje spřažení mezi haldami a procesory GC serveru. Ve výchozím nastavení je k dispozici jedna Halda GC serveru pro každý procesor.

- [GCHeapCount](gcheapcount-element.md), která omezuje počet hald používaných procesem.

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), která definuje spřažení mezi dostupnými haldami GC serveru a jednotlivými procesory.

## <a name="example"></a>Příklad

Následující příklad povoluje uvolňování paměti serveru:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Zakázání souběžného uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
