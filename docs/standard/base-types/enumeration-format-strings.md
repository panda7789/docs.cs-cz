---
title: Vytvoření výčtu řetězců formátu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4402bf58ea853d8a373592eec274a8bf75e7e90c
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925739"
---
# <a name="enumeration-format-strings"></a>Vytvoření výčtu řetězců formátu
Můžete použít <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodu pro vytvoření nového objektu řetězec, který představuje číselná, šestnáctkové číslo nebo řetězcové hodnoty na člena výčtu. Tato metoda přebírá jeden výčet formátování řetězce k určení, které se mají vracet hodnotu.

Následující tabulka uvádí výčet formátování řetězců a hodnoty, které vracejí. Tyto specifikátory formátu nerozlišují malá a velká písmena.

| Formátovací řetězec | Výsledek |
| ------------- | ------ |
| G nebo g | Zobrazí výčet položku jako hodnotu řetězce, pokud je to možné a v opačném případě se zobrazí celočíselnou hodnotu aktuální instance. Pokud je definován výčet s **příznaky** nastaven atribut řetězců jsou hodnoty pro každou platnou položku zřetězených dohromady, oddělené čárkami. Pokud **příznaky** atribut není nastaven, je neplatná hodnota zobrazí jako číselného vstupu. Následující příklad ukazuje specifikátor formátu.<br /><br />[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)] |
| F nebo f | Zobrazí výčet položku jako řetězcovou hodnotu, pokud je to možné. Pokud hodnota může být zcela zobrazena jako souhrn položky ve výčtu (i v případě, **příznaky** atribut není k dispozici), řetězcové hodnoty pro každou platnou položku jsou společně zřetězených, oddělené čárkami. Pokud hodnotu nelze určit zcela podle položek výčtu, hodnota formátována jako hodnota celého čísla. Následující příklad ukazuje specifikátor formátu F.<br /><br />[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)] |
| D nebo d | Zobrazí výčet položku jako celočíselnou hodnotu v nejkratší možné reprezentaci. Následující příklad ukazuje specifikátor formátu D.<br /><br />[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)] |
| X nebo x | Zobrazí výčet položku jako šestnáctková hodnota. Hodnota je reprezentován počátečními nulami podle potřeby zajistit, že hodnota je minimální osm číslic v délce. Následující příklad ukazuje specifikátor formátu X.<br /><br /> [!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)] |

## <a name="example"></a>Příklad

Následující příklad definuje výčet nazvaný `Colors` , který se skládá ze tří položek: `Red`, `Blue`, a `Green`.

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Po definování výčtu instance mohou být deklarovány následujícím způsobem.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

`Color.ToString(System.String)` Metoda je pak možné k zobrazení hodnoty výčtu různými způsoby v závislosti na specifikátor formátu do něho předaný.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Viz také

[Typy formátování](formatting-types.md)