---
title: Řetězce formátu výčtu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: c32fd9d59f61b6befe94ff9eb85b0c39ce926adb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348269"
---
# <a name="enumeration-format-strings"></a>Řetězce formátu výčtu

Metodu <xref:System.Enum.ToString%2A?displayProperty=nameWithType> lze použít k vytvoření nového řetězcového objektu, který představuje číselnou, šestnáctkovou nebo řetězcovou hodnotu člena výčtu. Tato metoda přebírá jeden z formátovacích řetězců výčtu k určení hodnoty, kterou chcete vrátit.

V následujících oddílech jsou uvedeny řetězce formátování výčtu a hodnoty, které vrací. Tyto specifikátory formátu nerozlišují velká a malá písmena.

## <a name="g-or-g"></a>G nebo g

Zobrazuje položku výčtu jako řetězcovou hodnotu, pokud je to možné, a jinak zobrazuje celočíselnou hodnotu aktuální instance. Pokud je výčet definován s nastaveným atributem **Flags** , jsou řetězcové hodnoty každé platné položky zřetězeny dohromady, oddělené čárkami. Pokud atribut **Flags** není nastaven, zobrazí se jako číselná položka neplatná hodnota. Následující příklad znázorňuje specifikátor formátu G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F nebo f

Pokud je to možné, zobrazí položku výčtu jako řetězcovou hodnotu. Pokud hodnota může být zcela zobrazená jako součet položek ve výčtu (i když atribut **Flags** není přítomný), jsou řetězcové hodnoty každé platné položky zřetězeny dohromady, oddělené čárkami. Pokud hodnota nemůže být zcela určena položkami výčtu, bude hodnota formátována jako celočíselná hodnota. Následující příklad ilustruje specifikátor formátu F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D nebo d

Zobrazí položku výčtu jako celočíselnou hodnotu v nejkratší možné reprezentaci. Následující příklad ilustruje specifikátor formátu D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X nebo x

Zobrazí položku výčtu jako šestnáctkovou hodnotu. Hodnota je vyjádřena podle potřeby počátečními nulami pro zajištění, že výsledný řetězec má dva znaky pro každý bajt v [základním číselném typu](xref:System.Enum.GetUnderlyingType%2A)typu výčtu. Následující příklad znázorňuje specifikátor formátu X. V příkladu je podkladový typ obou <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> <xref:System.Int32>nebo celé číslo 32 (nebo 4 bajt), které vytváří výsledný řetězec 8 znaků.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Příklad

Následující příklad definuje výčet s názvem `Colors`, který se skládá ze tří položek: `Red`, `Blue`a `Green`.

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Po definování výčtu může být instance deklarována následujícím způsobem.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

Metodu `Color.ToString(System.String)` lze následně použít k zobrazení hodnoty výčtu různými způsoby v závislosti na použitém specifikátoru formátu.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Viz také:

- [Typy formátování](formatting-types.md)
