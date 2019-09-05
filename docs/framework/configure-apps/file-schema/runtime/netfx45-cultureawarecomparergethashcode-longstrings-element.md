---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef814d1b5f32359033e8a19999d6271677315fff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252425"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element

Určuje, zda modul runtime používá k výpočtu kódů hash pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pevnou velikost paměti.

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
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

|Value|Popis|
|-----------|-----------------|
|0|Modul CLR (Common Language Runtime) přiděluje proměnnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu výpočtu kódů hash. Toto nastavení je výchozí.|
|1|Modul CLR (Common Language Runtime) přiděluje pevnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu výpočtu kódů hash.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení modul CLR (Common Language Runtime) přiděluje proměnlivé množství paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pro metodu <xref:System.ArgumentException> a může být vyvolána, když se metoda pokusí vypočítat hash kód velmi velkých řetězců (více než 1 milion znaků). Přidáním tohoto elementu do konfiguračního souboru aplikace a nastavením jeho `enabled` atributu na hodnotu "1" můžete určit <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> , že metoda používá alternativní algoritmus, který přiděluje pevnou velikost paměti pro výpočet kódů hash.

> [!IMPORTANT]
> Element se nepoužívá v [!INCLUDE[win8](../../../../../includes/win8-md.md)] a novějších verzích. `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`

## <a name="see-also"></a>Viz také:

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
