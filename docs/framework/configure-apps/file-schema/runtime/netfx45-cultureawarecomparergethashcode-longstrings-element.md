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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802109"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>Element \<NetFx45_CultureAwareComparerGetHashCode_LongStrings>

Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

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

|Hodnota|Description|
|-----------|-----------------|
|0|Modul CLR (Common Language Runtime) přiděluje proměnnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu výpočtu kódů hash. Toto nastavení je výchozí.|
|1|Modul CLR (Common Language Runtime) přiděluje pevnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu výpočtu kódů hash.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení modul CLR (Common Language Runtime) přiděluje proměnlivé množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí vypočítat hash kód velmi velkých řetězců (více než 1 milion znaků). Přidáním tohoto elementu do konfiguračního souboru aplikace a nastavením jeho `enabled` atributu na hodnotu "1" můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> Metoda používá alternativní algoritmus, který přiděluje pevnou velikost paměti pro výpočet kódů hash.

> [!IMPORTANT]
> `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Element se nepoužívá v systému Windows 8 a novějších verzích.

## <a name="see-also"></a>Viz také

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
