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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a2bbd2470b4aec9e95ab67ccb0e736c4c6d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920692"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode – element >

Určuje, zda modul runtime zachovává starší chování při formátování operací <xref:System.TimeSpan?displayProperty=nameWithType> s hodnotami.

\<> Konfigurace \
\<běhové > \
\<TimeSpan_LegacyFormatMode >

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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime používá chování formátování starší <xref:System.TimeSpan?displayProperty=nameWithType> verze s hodnotami.|

## <a name="enabled-attribute"></a>Atribut enabled

|Value|Popis|
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

Počínaje .NET Framework 4 <xref:System.TimeSpan?displayProperty=nameWithType> struktura <xref:System.IFormattable> implementuje rozhraní a podporuje operace formátování pomocí standardních a vlastních formátovacích řetězců. Pokud metoda analýzy narazí na nepodporovaný specifikátor formátu nebo formátovací řetězec, vyvolá <xref:System.FormatException>.

V předchozích verzích .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovala řetězce formátu. Mnoho vývojářů však omylem nepředpokládalo <xref:System.TimeSpan> , že podporovaly sadu formátovacích řetězců a používají je ve [složených formátovacích operacích](../../../../standard/base-types/composite-formatting.md) s <xref:System.String.Format%2A?displayProperty=nameWithType>metodami, jako je například. V případě, že typ implementuje <xref:System.IFormattable> a podporuje řetězce formátu, volání metod formátování s nepodporovanými řetězci formátu obvykle <xref:System.FormatException>vyvolají. Protože <xref:System.TimeSpan> však neimplementoval <xref:System.IFormattable>, modul runtime ignoruje <xref:System.TimeSpan.ToString?displayProperty=nameWithType> řetězec formátu a místo toho se nazývá metoda. To znamená, že přestože formátovací řetězce neobsahovaly žádný vliv na operaci formátování, jejich přítomnost nezpůsobila <xref:System.FormatException>.

V případech, kdy starší verze kódu projde metodou složeného formátování a neplatným formátovacím řetězcem a tento kód nelze znovu zkompilovat, lze pomocí `<TimeSpan_LegacyFormatMode>` elementu obnovit starší verze <xref:System.TimeSpan> chování. Když `enabled` nastavíte atribut tohoto elementu na `true`, metoda složeného formátování <xref:System.TimeSpan.ToString?displayProperty=nameWithType> způsobí volání namísto <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.

## <a name="example"></a>Příklad

Následující příklad vytvoří instanci <xref:System.TimeSpan> objektu a pokusí se ho naformátovat <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> pomocí metody pomocí nepodporovaného standardního formátovacího řetězce.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Když spustíte příklad na .NET Framework 3,5 nebo v dřívější verzi, zobrazí se následující výstup:

```
12:30:45
```

To se liší od výstupu, pokud spustíte příklad na .NET Framework 4 nebo novější verzi:

```
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
