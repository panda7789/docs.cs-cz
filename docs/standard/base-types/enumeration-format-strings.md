---
title: Formátové řetězce výčtu
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
ms.openlocfilehash: da7634758f5c4319fa18612d216682dc141318fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155955"
---
# <a name="enumeration-format-strings"></a>Formátové řetězce výčtu

Metodu <xref:System.Enum.ToString%2A?displayProperty=nameWithType> můžete použít k vytvoření nového objektu řetězce, který představuje číselnou, šestnáctkovou nebo řetězcovou hodnotu člena výčtu. Tato metoda trvá jeden z řetězce formátování výčtu určit hodnotu, kterou chcete vrátit.

V následujících částech jsou uvedeny řetězce formátování výčtu a hodnoty, které vracejí. Tyto specifikátory formátu nejsou rozlišována malá a velká písmena.

## <a name="g-or-g"></a>G nebo g

Zobrazí položku výčtu jako hodnotu řetězce, pokud je to možné, a jinak zobrazí celou hodnotu aktuální instance. Pokud je výčet definován pomocí sady atributů **Flags,** řetězcové hodnoty každé platné položky jsou spojeny dohromady, oddělené čárkami. Pokud atribut **Flags** není nastaven, zobrazí se jako číselná položka neplatná hodnota. Následující příklad ilustruje specifikátor formátu G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F nebo f

Pokud je to možné, zobrazí položku výčtu jako hodnotu řetězce. Pokud hodnota může být zcela zobrazena jako součet položek ve výčtu (i v **případě, že** atribut Flags není k dispozici), řetězcové hodnoty každé platné položky jsou spojeny dohromady, oddělené čárkami. Pokud hodnotu nelze zcela určit položkami výčtu, je hodnota formátována jako celá hodnota. Následující příklad ilustruje specifikátor formátu F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D nebo d

Zobrazí položku výčtu jako celou hodnotu v co nejkratší reprezentaci. Následující příklad ilustruje specifikátor formátu D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X nebo x

Zobrazí položku výčtu jako šestnáctkovou hodnotu. Hodnota je podle potřeby reprezentována počátečními nulami, aby bylo zajištěno, že výsledný řetězec má dva znaky pro každý bajt v [základním číselném typu](xref:System.Enum.GetUnderlyingType%2A)typu výčtu . Následující příklad ilustruje specifikátor formátu X. V příkladu základní typ <xref:System.ConsoleColor> obou <xref:System.IO.FileAttributes> <xref:System.Int32>a je , nebo 32bitové (nebo 4 bajtové) celé číslo, které vytváří řetězec výsledků 8 znaků.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Příklad

Následující příklad definuje výčet s `Colors` názvem, který se `Red` `Blue`skládá `Green`ze tří položek: , a .

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Po vytvoření výčtu je definována instance může být deklarována následujícím způsobem.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

Metodu `Color.ToString(System.String)` lze pak použít k zobrazení hodnoty výčtu různými způsoby v závislosti na specifikátoru formátu, který jí byl předán.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Viz také

- [Typy formátování](formatting-types.md)
