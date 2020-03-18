---
title: 'Postupy: Zarovnání čísla úvodními nulami'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131979"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Postupy: Zarovnání čísla úvodními nulami

Počáteční nuly můžete přidat k celé číslo pomocí [standardního číselného formátovacího řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" s specifikátorem přesnosti. Počáteční nuly můžete přidat k číslům celého čísla i čísla s plovoucí desetinnou desetinnou hodnotou pomocí [vlastního číselného formátovacího řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md). Tento článek ukazuje, jak používat obě metody k vyložce číslo s úvodními nulami.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Vytvoření celého čísla s počátečními nulami na určitou délku

1. Určete minimální počet číslic, které chcete zobrazit v celé řadové hodnotě. Do tohoto čísla uveďte všechny úvodní číslice.

1. Určete, zda chcete zobrazit celé číslo jako desetinnou hodnotu nebo šestnáctkovou hodnotu.

    - Chcete-li zobrazit celé číslo jako desítkovou `ToString(String)` hodnotu, zavolejte jeho metodu a `format` předejte řetězec "D*n*" jako hodnotu parametru, kde *n* představuje minimální délku řetězce.

    - Chcete-li zobrazit celé číslo jako šestnáctkovou hodnotu, zavolejte její `ToString(String)` metodu a předejte řetězec "X*n*" jako hodnotu parametru format, kde *n* představuje minimální délku řetězce.

Formátovací řetězec můžete také použít v interpolovaném řetězci v [jazyce C#](../../csharp/language-reference/tokens/interpolated.md) i <xref:System.String.Format%2A?displayProperty=nameWithType> [jazyce Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)nebo můžete volat metodu, například nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, která používá složené [formátování](../../../docs/standard/base-types/composite-formatting.md).

Následující příklad zformátuje několik vícečíselných hodnot s počátečními nulami tak, aby celková délka formátovaného čísla byla alespoň osm znaků.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Vytvoření celého čísla s určitým počtem počátečních nul

1. Určete, kolik počátečních nul se má celá hodnota zobrazit.

1. Určete, zda chcete zobrazit celé číslo jako desetinnou hodnotu nebo šestnáctkovou hodnotu.

    - Formátování jako desetinné hodnoty vyžaduje použití standardního specifikátoru formátu D.

    - Formátování jako šestnáctkové hodnoty vyžaduje použití standardního specifikátoru formátu "X".

1. Určete délku nepolstrovaného číselného řetězce voláním `ToString("D").Length` `ToString("X").Length` celé hodnoty nebo metody.

1. Přidejte počet počátečních nul, které chcete zahrnout do formátovaného řetězce, na délku nepolstrovaného číselného řetězce. Přidáním počtu úvodních nul definujete celkovou délku polstrovaného řetězce.

1. Volat `ToString(String)` metodu hodnota celé číslo a předat řetězec "D*n*" pro desetinné řetězce a "X*n*" pro šestnáctkové řetězce, kde *n* představuje celkovou délku polstrovanéřetězce. Můžete také použít formátovací řetězec "D*n*" nebo "X*n*" v metodě, která podporuje složené formátování.

Následující příklad vycpává hodnotu celéčíslo s pěti počátečními nulami.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Vyřadit číselnou hodnotu s počátečními nulami na určitou délku

1. Určete, kolik číslic nalevo od desetinného místa chcete mít řetězcovou reprezentaci čísla. Do tohoto celkového počtu číslic zahrňte všechny počáteční nuly.

1. Definujte vlastní číselný formátovací řetězec, který používá nulový zástupný symbol "0" k reprezentaci minimálního počtu nul.

1. Zavolejte `ToString(String)` metodu čísla a předejte mu vlastní formátovací řetězec. Můžete také použít vlastní formátovací řetězec s interpolací řetězců nebo s metodou, která podporuje složené formátování.

Následující příklad formátuje několik číselných hodnot s úvodními nulami. V důsledku toho je celková délka formátovaného čísla nejméně osm číslic nalevo od desetinného místa.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Vytvoření číselné hodnoty s určitým počtem počátečních nul

1. Určete, kolik počátečních nul má číselná hodnota mít.

1. Určete počet číslic nalevo od desetinného místa v nepolstrovaném číselném řetězci:

    1. Určete, zda řetězcová reprezentace čísla obsahuje symbol desetinné čárky.

    1. Pokud obsahuje symbol desetinné čárky, určete počet znaků nalevo od desetinné čárky.

         -nebo-

         Pokud neobsahuje symbol desetinné čárky, určete délku řetězce.

1. Vytvořte vlastní formátovací řetězec, který používá:

    - Nulový zástupný symbol "0" pro každou z úvodních nul, která se zobrazí v řetězci.

    - Buď žádný zástupný symbol nebo zástupný symbol číslice "#", který představuje každou číslici ve výchozím řetězci.

1. Zadejte vlastní formátovací řetězec jako parametr `ToString(String)` metodu čísla nebo metodu, která podporuje složené formátování.

Následující příklad vycpává dvě <xref:System.Double> hodnoty s pěti počátečními nulami.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Viz také

- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
