---
title: Element GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451218"
---
# <a name="gclohthreshold-element"></a>Element GCLOHThreshold

Určuje velikost prahové hodnoty v bajtech, která způsobí, že systém uvolňování paměti vloží objekty do haldy velkých objektů (LOH).

[konfigurační >\<](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold >

## <a name="syntax"></a>Syntaxe

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br />Určuje velikost prahové hodnoty, která způsobí, že objekty přejdou na haldu velkých objektů.|

### <a name="enabled-attribute"></a>povolený atribut

|Hodnota|Popis|
|-----------|-----------------|
|`nnnn`|Velikost prahové hodnoty (v bajtech), která způsobí, že objekty přejdou na haldu velkých objektů.|

## <a name="child-elements"></a>Podřízené prvky

Žádné.

## <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Toto nastavení bylo zavedeno v .NET Framework 4,8.

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhu](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Základní informace o uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md)
- [Možnosti konfigurace NET Core Runtime pro GC](../../../../core/run-time-config/garbage-collector.md)
