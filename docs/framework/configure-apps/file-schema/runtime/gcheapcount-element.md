---
title: Element GCHeapCount
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283075"
---
# <a name="gcheapcount-element"></a>\<element > GCHeapCount

Určuje počet hald/vláken, které se mají použít pro uvolňování paměti serveru.

Konfigurace \<> \
&nbsp;&nbsp;\<runtime > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount >

## <a name="syntax"></a>Syntaxe

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje počet hald, které se mají použít pro uvolňování paměti serveru. Skutečný počet hald je minimální počet hald, které zadáte, a počet procesorů, které může váš proces používat. |

#### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Popis|
|-----------|-----------------|
|`nn`|Počet hald pro použití pro GC serveru.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s jejich vlastním PROCESORem, aby existovala jedna Halda GC, jedno vlákno GC serveru a jeden podproces GC na pozadí pro každý procesor. Počínaje .NET Framework 4.6.2 můžete použít prvek **GCHeapCount** k omezení počtu hald používaných vaší aplikací pro uvolňování serveru. Omezení počtu hald používaných pro GC serveru je zvlášť užitečné pro systémy, které spouštějí více instancí serverové aplikace.

**GCHeapCount** se obvykle používá společně se dvěma dalšími příznaky:

- [GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda jsou vlákna a haldy GC serveru spřažené s procesory.

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), která řídí spřažení vláken a hald GC s procesory.

Pokud je nastavená možnost **GCHeapCount** a **GCNoAffinitize** je zakázaná (výchozí nastavení), existuje spřažení mezi vlákny *NN* GC/haldami a prvními procesory *NN* . Pomocí elementu **GCHeapAffinitizeMask** můžete určit, které procesory jsou používány haldami GC serveru procesu. V opačném případě, pokud je v systému spuštěno více procesů serveru, jejich využití procesoru se překrývá.

Pokud je nastavená možnost **GCHeapCount** a je povolená možnost **GCNoAffinitize** , uvolňování paměti omezuje počet PROCESORů používaných pro uvolňování serveru, ale nespřažení haldy a procesory GC.

## <a name="example"></a>Příklad

Následující příklad označuje, že aplikace používá GC serveru s 10 haldami nebo vlákny. Vzhledem k tomu, že nechcete, aby se tyto haldy překrývaly s haldami z jiných aplikací spuštěných v systému, použijte **GCHeapAffinitizeMask** a určete tak, že by měl proces používat procesory 0 až 9.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

Následující příklad nespřaženíuje vlákna uvolňování paměti serveru a omezuje počet hald a vláken GC na 10.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Element GCNoAffinitize](gcnoaffinitize-element.md)
- [Element GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)
- [Základní informace o uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
