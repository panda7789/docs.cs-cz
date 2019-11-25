---
title: Element GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978373"
---
# <a name="gcnoaffinitize-element"></a>\<element > GCNoAffinitize

Určuje, jestli se mají spřažení vlákna GC serveru pomocí procesorů.

Konfigurace \<> \
&nbsp;&nbsp;\<runtime > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize >

## <a name="syntax"></a>Syntaxe

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje, zda jsou vlákna nebo haldy GC serveru spřažené s procesory dostupnými v počítači.|

#### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Spřáhne vlákna GC serveru pomocí procesorů. Toto nastavení je výchozí.|
|`true`|Nespřaženíuje vlákna GC serveru pomocí procesorů.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s příslušnými procesory. Každý z dostupných procesorů systému má vlastní haldu a vlákno GC. To je obvykle preferované nastavení, protože optimalizuje využití mezipaměti. Počínaje .NET Framework 4.6.2 nastavením atributu `enabled` elementu **GCNoAffinitize** na hodnotu `false`můžete určit, že vlákna uvolňování paměti serveru a CPU by neměly být pevně spojeny.

Můžete zadat pouze konfigurační element **GCNoAffinitize** , aby nespřaženíy vlákna GC serveru pomocí CPU. Můžete ji také použít spolu s elementem [GCHeapCount](gcheapcount-element.md) k řízení počtu hald GC a vláken používaných aplikací.

Pokud je atribut `enabled` elementu **GCNoAffinitize** `false` (jeho výchozí hodnota), můžete také použít element [GCHeapCount](gcheapcount-element.md) k určení počtu vláken GC a hald společně s elementem [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pro určení procesorů, do kterých jsou vlákna uvolňování paměti a haldy spřažené.

## <a name="example"></a>Příklad

Následující příklad neprovádí pevným spřažením vláken v GC serveru:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

Následující příklad nespřaženíuje vlákna uvolňování paměti serveru a omezuje počet hald a vláken GC na 10:

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
- [Element GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)
- [Element GCHeapCount](gcheapcount-element.md)
- [Základní informace o uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
