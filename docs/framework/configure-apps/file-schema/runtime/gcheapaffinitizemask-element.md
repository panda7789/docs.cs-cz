---
title: Element GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978380"
---
# <a name="gcheapaffinitizemask-element"></a>\<element > GCHeapAffinitizeMask

Definuje spřažení mezi haldami GC a jednotlivými procesory.

Konfigurace \<> \
&nbsp;&nbsp;\<runtime > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask >

## <a name="syntax"></a>Syntaxe

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje spřažení mezi haldami GC a jednotlivými procesory. |

#### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Popis|
|-----------|-----------------|
|`nnnn`|Desítková hodnota, která vytvoří bitovou masku definující spřažení mezi haldami GC serveru a jednotlivými procesory. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s jejich vlastním PROCESORem, aby existovala jedna Halda GC, jedno vlákno GC serveru a jeden podproces GC na pozadí pro každý procesor. Počínaje .NET Framework 4.6.2 můžete použít prvek **GCHeapAffinitizeMask** k řízení spřažení mezi haldami GC serveru a procesory, pokud je počet haldy omezený prvkem **GCHeapCount** .

**GCHeapAffinitizeMask** se obvykle používá společně se dvěma dalšími příznaky:

- [GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda jsou vlákna a haldy GC serveru spřažené s procesory. Atribut `enabled` elementu [GCNoAffinitize](gcnoaffinitize-element.md) musí být `false` (jeho výchozí hodnota) pro použití nastavení **GCHeapAffinitizeMask** .

- [GCHeapCount](gcheapcount-element.md), která omezuje počet hald používaných procesem pro uvolňování paměti serveru. Ve výchozím nastavení je pro každý procesor k dispozici jedna halda.

**nnnn** je Bitová maska vyjádřená jako Desítková hodnota. Bit 0 bajtů 0 představuje procesor 0, bit 1 bajtů 0 představuje procesor 1 atd. Příklad:

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

Hodnota 1023 je 0x3FF nebo 0011 1111 1111b. Proces používá 10 procesorů od procesorů 0 do procesoru 9.

## <a name="example"></a>Příklad

Následující příklad označuje, že aplikace používá GC serveru s 10 haldami nebo vlákny. Vzhledem k tomu, že nechcete, aby se tyto haldy překrývaly s haldami z jiných aplikací spuštěných v systému, použijte **GCHeapAffinitizeMask** a určete tak, že by měl proces používat CPU 0 až 9.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Element GCNoAffinitize](gcnoaffinitize-element.md)
- [Element GCHeapCount](gcheapcount-element.md)
- [Základní informace o uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
