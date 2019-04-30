---
title: 'Postupy: Vyplnění čísla úvodními nulami'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54c3eb734184adf5168607cfc8bcbf6c17ea493a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860643"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Postupy: Vyplnění čísla úvodními nulami

Můžete přidat počáteční nuly na celé číslo pomocí "D" [řetězec standardního číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md) specifikátorem přesnosti. Můžete přidat počáteční nuly celého čísla a čísla s plovoucí desetinnou čárkou pomocí [vlastní číselný formátovací řetězec](../../../docs/standard/base-types/custom-numeric-format-strings.md). Tento článek ukazuje, jak používat obě metody k zarovnání čísla úvodními nulami.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Pro vyplnění celého čísla úvodními nulami na konkrétní délku

1. Určete minimální počet číslic, které chcete, aby celočíselnou hodnotu pro zobrazení. Zahrňte všechny úvodní číslice tohoto čísla.

1. Určete, zda chcete pro zobrazení na celé číslo jako hodnotu Desítková nebo šestnáctková hodnota.

    - Pro zobrazení na celé číslo jako hodnotu decimal, volejte jeho `ToString(String)` a předáte řetězec "D*n*" jako hodnotu `format` parametr, kde *n* představuje minimální délka řetězce.

    - Pro zobrazení na celé číslo jako šestnáctkové hodnoty, volejte jeho `ToString(String)` a předáte řetězec "X*n*" jako hodnoty parametru formátu, ve kterém *n* představuje minimální délka řetězce.

Můžete také použít řetězec formátu v interpolovaném řetězci v obou [ C# ](../../csharp/language-reference/tokens/interpolated.md) a [jazyka Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), nebo můžete volat metodu, jako například <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, používající [ složené formátování](../../../docs/standard/base-types/composite-formatting.md).

Následující příklad formátuje několik celočíselné hodnoty počátečními nulami tak, aby celková délka naformátovaného čísla alespoň osm znaků.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Pro vyplnění celé číslo s konkrétní počet počáteční nuly

1. Určete, kolik počátečních nul chcete celočíselnou hodnotu pro zobrazení.

1. Určete, zda chcete pro zobrazení na celé číslo jako hodnotu Desítková nebo šestnáctková hodnota.

    - Formátování jako desítková hodnota vyžaduje, že používáte specifikátor standardního formátu "D".

    - Formátování jako šestnáctková hodnota vyžaduje, že používáte specifikátor standardního formátu "X".

1. Určuje délku nedoplněného číselný řetězec voláním celočíselnou hodnotu `ToString("D").Length` nebo `ToString("X").Length` metody.

1. Přidáte počet počátečních nul, které chcete zahrnout do formátovaný řetězec, který má délku nedoplněného číselné řetězce. Přidání čísla nulou definuje celková délka doplněného řetězce.

1. Volání celočíselnou hodnotu `ToString(String)` a předáte řetězec "D*n*" decimal řetězců a "X*n*" pro řetězce v šestnáctkovém formátu, ve kterém *n* představuje celkový počet Délka vyplněný řetězce. Můžete také použít "D*n*" nebo "X*n*" formátovací řetězec v metodě, která podporuje složené formátování.

Následující příklad vyplní celočíselnou hodnotu pěti nulami.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Pro vyplnění číselnou hodnotu počátečními nulami na konkrétní délku

1. Určete, kolik číslic nalevo od desetinné čárky chcete řetězcové vyjádření čísla mít. Zahrnout všechny úvodní nuly v tomto celkový počet číslic.

1. Definujte vlastní číselný formátovací řetězec, který používá k reprezentaci minimální počet nul nulový zástupný symbol "0".

1. Zavolejte na číslo `ToString(String)` metoda a předejte jí řetězec vlastního formátu. Můžete také použít řetězec vlastního formátu pomocí interpolace řetězců nebo metodou, která podporuje složené formátování.

Následující příklad formátuje několik číselných hodnot počátečními nulami. Celková délka naformátovaného čísla v důsledku toho je nejméně osm číslic nalevo od desetinné čárky.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Pro vyplnění číselná hodnota s konkrétní počet počáteční nuly

1. Určete, kolik počátečních nul chcete číselná hodnota, která mají.

1. Určete počet číslic nalevo od desetinné čárky v nedoplněného číselných řetězců:

    1. Určení, zda řetězcové vyjádření čísla zahrnuje symbol desetinné čárky.

    1. Pokud je symbol desetinné čárky, určete počet znaků vlevo od desetinné čárky.

         -nebo-

         Pokud neobsahuje symbol desetinné čárky, určení délky řetězce.

1. Vytvořte vlastní formátovací řetězec, který používá:

    - Nulový zástupný symbol "0" pro každou z počátečních nul se zobrazí v řetězci.

    - Zástupný symbol nula nebo zástupný symbol číslice "#" k reprezentaci jednotlivých číslice v řetězci výchozí.

1. Zadat vlastní řetězec formátu jako parametr buď na číslo `ToString(String)` metodu nebo metodu, která podporuje složené formátování.

Následující příklad vyplní dvě <xref:System.Double> hodnoty pěti nulami.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Viz také:

- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
