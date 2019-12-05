---
title: Element <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802109"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element

Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pevnou velikost paměti.

[**konfigurační >\<** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**  

## <a name="syntax"></a>Syntaxe

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.|

## <a name="enabled-attribute"></a>Atribut enabled

|Hodnota|Popis|
|-----------|-----------------|
|0|Modul CLR (Common Language Runtime) přiděluje proměnnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash. Toto nastavení je výchozí.|
|1|Modul CLR (Common Language Runtime) přiděluje pevnou velikost paměti pro metodu <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> k výpočtu kódů hash.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení modul CLR (Common Language Runtime) přiděluje proměnlivou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí vypočítat hash kód velmi velkých řetězců (více než 1 milion znaků). Přidáním tohoto elementu do konfiguračního souboru aplikace a nastavením jeho `enabled` atributu na hodnotu "1" můžete určit, že metoda <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> používá alternativní algoritmus, který přiděluje pevnou velikost paměti pro výpočet kódů hash.

> [!IMPORTANT]
> Element `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` se nepoužívá v systému Windows 8 a novějších verzích.

## <a name="see-also"></a>Viz také:

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
