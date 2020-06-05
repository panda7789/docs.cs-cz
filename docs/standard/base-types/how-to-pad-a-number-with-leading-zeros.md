---
title: 'Postupy: Vyplnění čísla úvodními nulami'
description: Naučte se číslo doplnit počátečními nulami. Přidejte počáteční nuly do celých čísel nebo číselných hodnot na konkrétní celkovou délku nebo konkrétní počet počátečních nul.
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
ms.openlocfilehash: 6ef0ddb37f1bc73254aa639d7c018ec6a01abd9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447183"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Postupy: Vyplnění čísla úvodními nulami

Můžete přidat počáteční nuly k celému číslu pomocí [standardního číselného formátovacího řetězce](standard-numeric-format-strings.md) "D" se specifikátorem přesnosti. Pomocí [vlastního řetězce číselného formátu](custom-numeric-format-strings.md)lze přidat úvodní nuly k číslům Integer i s plovoucí desetinnou čárkou. Tento článek ukazuje, jak použít obě metody k vyplnění čísla počátečními nulami.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Vyplnění celého čísla počátečními nulami na určitou délku

1. Určete minimální počet číslic, které mají být zobrazeny v celočíselné hodnotě. V tomto čísle uveďte všechny úvodní číslice.

1. Určete, zda chcete zobrazit celé číslo jako desítkovou hodnotu nebo hexadecimální hodnotu.

    - Chcete-li zobrazit celé číslo jako desítkovou hodnotu, zavolejte svou `ToString(String)` metodu a předejte řetězec "D*n*" jako hodnotu `format` parametru, kde *n* představuje minimální délku řetězce.

    - Chcete-li zobrazit celé číslo jako šestnáctkovou hodnotu, zavolejte svou `ToString(String)` metodu a předejte řetězec "X*n*" jako hodnotu parametru Format, kde *n* představuje minimální délku řetězce.

Řetězec formátu lze použít také v řetězci v [jazyce C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), nebo můžete zavolat metodu, například <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , která používá [složené formátování](composite-formatting.md).

Následující příklad formátuje několik celočíselných hodnot s počátečními nulami tak, aby celková délka formátovaného čísla byla alespoň osm znaků.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Chcete-li doplnit celé číslo s určitým počtem počátečních nul

1. Určete, kolik počátečních nul má být celočíselná hodnota zobrazena.

1. Určete, zda chcete zobrazit celé číslo jako desítkovou hodnotu nebo hexadecimální hodnotu.

    - Formátování jako Desítková hodnota vyžaduje použití specifikátoru standardního formátu "D".

    - Formátování jako hexadecimální hodnota vyžaduje použití specifikátoru standardního formátu "X".

1. Určete délku nedoplněného číselného řetězce voláním celočíselné hodnoty `ToString("D").Length` nebo `ToString("X").Length` metody.

1. Přidejte počet počátečních nul, které chcete zahrnout do formátovaného řetězce, na délku nedoplněného číselného řetězce. Přidání počtu počátečních nul definuje celkovou délku čalouněného řetězce.

1. Zavolejte metodu celočíselné hodnoty `ToString(String)` a předejte řetězec "D*n*" pro desítkové řetězce a "X*n*" pro šestnáctkové řetězce, kde *n* představuje celkovou délku čalouněného řetězce. Můžete také použít formátovací řetězec "D*n*" nebo "X*n*" v metodě, která podporuje složené formátování.

V následujícím příkladu je celočíselná hodnota s pěti počátečními nulami.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Vyplnění číselné hodnoty počátečními nulami na určitou délku

1. Určete, kolik číslic nalevo od desetinné čárky má mít řetězcové vyjádření čísla. V tomto celkovém počtu číslic uveďte všechny úvodní nuly.

1. Definujte vlastní řetězec číselného formátu, který používá nulový zástupný symbol "0" k vyjádření minimálního počtu nul.

1. Zavolejte `ToString(String)` metodu Number a předejte jí vlastní formátovací řetězec. Můžete také použít vlastní řetězec formátu s interpolací řetězce nebo metodou, která podporuje složené formátování.

Následující příklad formátuje několik číselných hodnot s počátečními nulami. V důsledku toho je celková délka formátovaného čísla aspoň osm číslic nalevo od desetinné čárky.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Vyplnění číselné hodnoty určitým počtem počátečních nul

1. Určete, kolik počátečních nul má číselná hodnota.

1. Určuje počet číslic nalevo od desetinné čárky v nedoplněném číselném řetězci:

    1. Určí, zda řetězcové vyjádření čísla obsahuje symbol desetinné čárky.

    1. Pokud obsahuje symbol desetinné čárky, určete počet znaků vlevo od desetinné čárky.

         -nebo-

         Pokud neobsahuje symbol desetinné čárky, určete délku řetězce.

1. Vytvořte vlastní řetězec formátu, který používá:

    - Nulový zástupný symbol "0" pro každou počáteční nuly, která se má objevit v řetězci.

    - Zástupný symbol nula nebo zástupný symbol číslice "#" pro reprezentaci každé číslice ve výchozím řetězci.

1. Zadejte řetězec vlastního formátu jako parametr buď do metody Number, `ToString(String)` nebo do metody, která podporuje složené formátování.

Následující příklad <xref:System.Double> doplní dvě hodnoty pěti počátečními nulami.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Viz také

- [Vlastní řetězce číselného formátu](custom-numeric-format-strings.md)
- [Řetězce standardního číselného formátu](standard-numeric-format-strings.md)
- [Složené formátování](composite-formatting.md)
