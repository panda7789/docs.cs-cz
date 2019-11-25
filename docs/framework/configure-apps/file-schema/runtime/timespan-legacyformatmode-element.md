---
title: Element <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968910"
---
# <a name="timespan_legacyformatmode-element"></a>Element \<TimeSpan_LegacyFormatMode >

Určuje, zda modul runtime zachovává starší chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnotami.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**  

## <a name="syntax"></a>Syntaxe

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime používá chování při formátování starší verze s <xref:System.TimeSpan?displayProperty=nameWithType>mi hodnotami.|

## <a name="enabled-attribute"></a>Atribut enabled

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Modul runtime neobnovuje chování při formátování starší verze.|
|`true`|Modul runtime obnoví chování formátování starší verze.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky

Počínaje .NET Framework 4 struktura <xref:System.TimeSpan?displayProperty=nameWithType> implementuje rozhraní <xref:System.IFormattable> a podporuje operace formátování pomocí standardních a vlastních formátovacích řetězců. Pokud metoda analýzy narazí na nepodporovaný specifikátor formátu nebo formátovací řetězec, vyvolá <xref:System.FormatException>.

V předchozích verzích .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovala řetězce formátu. Mnoho vývojářů však omylem nepředpokládalo, že <xref:System.TimeSpan> podporovala sadu formátovacích řetězců a použila je ve [složených operacích formátování](../../../../standard/base-types/composite-formatting.md) s metodami, jako je <xref:System.String.Format%2A?displayProperty=nameWithType>. V případě, že typ implementuje <xref:System.IFormattable> a podporuje řetězce formátu, volání metod formátování s nepodporovanými řetězci formátu obvykle vyvolají <xref:System.FormatException>. Vzhledem k tomu, že <xref:System.TimeSpan> neimplementoval <xref:System.IFormattable>, modul runtime ignoruje řetězec formátu a místo toho volal metodu <xref:System.TimeSpan.ToString?displayProperty=nameWithType>. To znamená, že přestože formátovací řetězce neobsahovaly žádný vliv na operaci formátování, jejich přítomnost nemá za následek <xref:System.FormatException>.

V případech, kdy starší verze kódu projde metodou složeného formátování a neplatným formátovacím řetězcem, a tento kód nelze znovu zkompilovat, lze použít prvek `<TimeSpan_LegacyFormatMode>` k obnovení starších <xref:System.TimeSpan> chování. Nastavíte-li atribut `enabled` tohoto prvku na hodnotu `true`, výsledkem metody složeného formátování je volání <xref:System.TimeSpan.ToString?displayProperty=nameWithType> spíše než <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.

## <a name="example"></a>Příklad

Následující příklad vytvoří instanci objektu <xref:System.TimeSpan> a pokusí se ho naformátovat pomocí metody <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> pomocí nepodporovaného standardního formátovacího řetězce.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Když spustíte příklad na .NET Framework 3,5 nebo v dřívější verzi, zobrazí se následující výstup:

```console
12:30:45
```

To se liší od výstupu, pokud spustíte příklad na .NET Framework 4 nebo novější verzi:

```console
Invalid Format
```

Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a potom spustíte příklad na .NET Framework 4 nebo novější verzi, výstup je stejný jako v příkladu, který je vytvořen v příkladu při spuštění v .NET Framework 3,5.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
