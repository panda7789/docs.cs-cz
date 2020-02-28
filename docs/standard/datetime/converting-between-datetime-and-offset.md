---
title: Převádění mezi DateTime a DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
ms.openlocfilehash: 5c19296f75e9e002e88263c5e5efa9917e185ebc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156033"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Převádění mezi DateTime a DateTimeOffset

I když struktura <xref:System.DateTimeOffset> poskytuje větší stupeň povědomí o časovém pásmu než <xref:System.DateTime> struktura, <xref:System.DateTime> parametry jsou používány častěji při volání metody. Z tohoto důvodu je schopnost převést hodnoty <xref:System.DateTimeOffset> na <xref:System.DateTime> hodnoty a naopak je zvláště důležitá. V tomto tématu se dozvíte, jak provádět tyto převody způsobem, který zachovává co možná nejvíce informací o časovém pásmu.

> [!NOTE]
> <xref:System.DateTime> i <xref:System.DateTimeOffset> typy mají určitá omezení, pokud představují časy v časových pásmech. Díky vlastnosti <xref:System.DateTime.Kind%2A> je <xref:System.DateTime> schopný odrážet pouze koordinovaný světový čas (UTC) a místní časové pásmo systému. <xref:System.DateTimeOffset> odráží časový posun od času UTC, ale neodráží skutečné časové pásmo, do kterého tento posun patří. Podrobnosti o hodnotách času a podpoře časových pásem najdete v tématu [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Převody z DateTime na DateTimeOffset

Struktura <xref:System.DateTimeOffset> poskytuje dva ekvivalentní způsoby, jak provést <xref:System.DateTime> <xref:System.DateTimeOffset> převod, který je vhodný pro většinu převodů:

- Konstruktor <xref:System.DateTimeOffset.%23ctor%2A>, který vytvoří nový objekt <xref:System.DateTimeOffset> na základě hodnoty <xref:System.DateTime>.

- Operátor implicitního převodu, který umožňuje přiřadit <xref:System.DateTime> hodnotu objektu <xref:System.DateTimeOffset>.

V případě hodnot UTC a Local <xref:System.DateTime> hodnoty <xref:System.DateTimeOffset.Offset%2A> výsledné <xref:System.DateTimeOffset> hodnoty přesně odráží časový posun UTC nebo místní časové pásmo. Například následující kód převede čas UTC na ekvivalentní <xref:System.DateTimeOffset>ovou hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

V tomto případě je posunutí proměnné `utcTime2` 00:00. Podobně následující kód převede místní čas na ekvivalentní <xref:System.DateTimeOffset>ovou hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Nicméně pro <xref:System.DateTime> hodnoty, jejichž vlastnost <xref:System.DateTime.Kind%2A> je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, tyto dvě metody převodu vytvoří <xref:System.DateTimeOffset> hodnotu, jejíž posun je to místní časové pásmo. To je znázorněno v následujícím příkladu, který je spuštěn v oblasti USA – Tichomoří (běžný čas).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Pokud hodnota <xref:System.DateTime> odráží datum a čas v jiném než místním časovém pásmu nebo UTC, můžete ho převést na <xref:System.DateTimeOffset> hodnotu a zachovat informace o časovém pásmu voláním přetíženého <xref:System.DateTimeOffset.%23ctor%2A> konstruktoru. Například následující příklad vytvoří instanci objektu <xref:System.DateTimeOffset>, který odráží centrální standardní čas.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Druhý parametr pro přetížení tohoto konstruktoru, <xref:System.TimeSpan> objekt, který představuje posun času od času UTC, by měl být načten zavoláním metody <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> odpovídajícího časového pásma času. Jediným parametrem metody je <xref:System.DateTime> hodnota, která představuje datum a čas, který má být převeden. Pokud časové pásmo podporuje letní čas, tento parametr umožňuje metodě určit odpovídající posun pro konkrétní datum a čas.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Převody z DateTimeOffset na DateTime

Vlastnost <xref:System.DateTimeOffset.DateTime%2A> se nejčastěji používá k provedení <xref:System.DateTimeOffset> k převodu <xref:System.DateTime>. Vrátí ale hodnotu <xref:System.DateTime>, jejíž vlastnost <xref:System.DateTime.Kind%2A> je <xref:System.DateTimeKind.Unspecified>, jak ukazuje následující příklad.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

To znamená, že při použití vlastnosti <xref:System.DateTimeOffset.DateTime%2A> je převod všech informací o vztahu <xref:System.DateTimeOffset> hodnoty na čas UTC ztracený. To má vliv na <xref:System.DateTimeOffset> hodnoty, které odpovídají času UTC nebo místnímu času systému, protože struktura <xref:System.DateTimeOffset.DateTime%2A> odráží pouze dvě časová pásma ve své vlastnosti <xref:System.DateTime.Kind%2A>.

Chcete-li při převodu <xref:System.DateTimeOffset> na <xref:System.DateTime> hodnotu zachovat co nejvíc informací o časovém pásmu, můžete použít vlastnosti <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>.

### <a name="converting-a-utc-time"></a>Převod času UTC

Pro indikaci, že převedená <xref:System.DateTimeOffset.DateTime%2A> hodnota je čas UTC, můžete načíst hodnotu vlastnosti <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>. Liší se od vlastnosti <xref:System.DateTimeOffset.DateTime%2A> dvěma způsoby:

- Vrací hodnotu <xref:System.DateTime>, jejíž vlastnost <xref:System.DateTime.Kind%2A> je <xref:System.DateTimeKind.Utc>.

- Pokud se hodnota vlastnosti <xref:System.DateTimeOffset.Offset%2A> nerovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, převede se čas na UTC.

> [!NOTE]
> Pokud vaše aplikace vyžaduje, aby <xref:System.DateTime> hodnoty jednoznačně identifikovaly jediný bod v čase, měli byste zvážit použití vlastnosti <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> ke zpracování všech <xref:System.DateTimeOffset> <xref:System.DateTime> převodů.

Následující kód používá vlastnost <xref:System.DateTimeOffset.UtcDateTime%2A> k převedení <xref:System.DateTimeOffset> hodnoty, jejíž posun se rovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType> na <xref:System.DateTime>ou hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Následující kód používá vlastnost <xref:System.DateTimeOffset.UtcDateTime%2A> k provedení převodu časového pásma a převodu typu na hodnotu <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Převod místního času

Chcete-li určit, že hodnota <xref:System.DateTimeOffset> představuje místní čas, můžete předat hodnotu <xref:System.DateTime> vrácenou vlastností <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> do `static` (`Shared` in Visual Basic) <xref:System.DateTime.SpecifyKind%2A> metody. Metoda vrátí datum a čas předaný do něj jako svůj první parametr, ale nastaví vlastnost <xref:System.DateTime.Kind%2A> na hodnotu určenou jeho druhým parametrem. Následující kód používá metodu <xref:System.DateTime.SpecifyKind%2A> při převodu <xref:System.DateTimeOffset> hodnoty, jejíž posun odpovídá místnímu časovému pásmu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Vlastnost <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> lze použít také k převedení <xref:System.DateTimeOffset> hodnoty na hodnotu místního <xref:System.DateTime>. Vlastnost <xref:System.DateTime.Kind%2A> vrácené hodnoty <xref:System.DateTime> je <xref:System.DateTimeKind.Local>. Následující kód používá vlastnost <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> při převodu <xref:System.DateTimeOffset> hodnoty, jejíž posun odpovídá místnímu časovému pásmu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Při načtení <xref:System.DateTime> hodnoty pomocí vlastnosti <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>, `get` přistupující objekt vlastnosti nejprve převede <xref:System.DateTimeOffset> hodnotu na UTC a pak ji převede na místní čas voláním metody <xref:System.DateTimeOffset.ToLocalTime%2A>. To znamená, že můžete načíst hodnotu z vlastnosti <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> k provedení převodu časového pásma ve stejnou dobu, jakou provádíte převod typu. Také to znamená, že pravidla úpravy v místním časovém pásmu jsou aplikována při provádění převodu. Následující kód ilustruje použití vlastnosti <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> k provedení jak typu, tak konverze časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda převodu pro obecné účely

Následující příklad definuje metodu s názvem `ConvertFromDateTimeOffset`, která převede <xref:System.DateTimeOffset> hodnoty na <xref:System.DateTime> hodnoty. Na základě jeho posunu určuje, zda <xref:System.DateTimeOffset> hodnota je čas UTC, místní čas nebo nějaký jiný čas, a odpovídajícím způsobem definuje vrácenou vlastnost <xref:System.DateTime.Kind%2A> hodnoty data a času.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Následující příklad volá metodu `ConvertFromDateTimeOffset` pro převod <xref:System.DateTimeOffset> hodnot, které reprezentují čas UTC, místní čas a čas v centrálním časovém pásmu USA – střed.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Všimněte si, že tento kód vytváří dvě předpoklady, které v závislosti na aplikaci a zdroji svých hodnot data a času nemusí být vždy platné:

- Předpokládá, že hodnota data a času, jejíž posun je <xref:System.TimeSpan.Zero?displayProperty=nameWithType> představuje čas UTC. Ve skutečnosti UTC není čas v konkrétním časovém pásmu, ale čas ve vztahu k tomu, kdy jsou standardizovány časy v časových pásmech světa. Časová pásma mohou mít také posun <xref:System.TimeSpan.Zero>.

- Předpokládá, že datum a čas, jehož posun se rovná tomuto místnímu časovému pásmu, představuje místní časové pásmo. Vzhledem k tomu, že hodnoty data a času jsou z původního časového pásma odasociovány, nemusí se jednat o případ; Datum a čas mohou mít původ v jiném časovém pásmu se stejným posunem.

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
