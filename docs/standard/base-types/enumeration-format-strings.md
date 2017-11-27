---
title: "Vytvoření výčtu řetězců formátu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0992d8591711073f9094c29fad980a8e652e686
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="enumeration-format-strings"></a>Vytvoření výčtu řetězců formátu
Můžete použít <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodu pro vytvoření nového objektu řetězec, který představuje numerické, šestnáctkové nebo řetězcovou hodnotu člena výčtu. Tato metoda přijímá jeden výčet formátování řetězce zadejte hodnotu, která mají být vráceny.  
  
 Následující tabulka uvádí výčet formátování řetězců a hodnoty, které vracejí. Tyto specifikátory formátu nerozlišují malá a velká písmena.  
  
| Řetězec formátu | Výsledek |  
| ------------- | ------ |  
| G nebo g | Zobrazí položku výčtu jako řetězcovou hodnotu, pokud je to možné a v opačném případě zobrazí celočíselnou hodnotu aktuální instance. Pokud výčet definován se **příznaky** sadu atributů, řetězec hodnoty každé platné položka jsou zřetězeny společně, oddělených čárkami. Pokud **příznaky** není nastavený atribut, jako číselná položka je zobrazena neplatná hodnota. Následující příklad ilustruje specifikátor formátu.<br><br>[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)] |  
| F nebo f | Zobrazí položku výčtu jako řetězcovou hodnotu, pokud je to možné. Pokud hodnota může být zcela zobrazena jako souhrn položek ve výčtu (i když **příznaky** atribut není k dispozici), řetězcové hodnoty každé platné položka jsou zřetězen dohromady, oddělených čárkami. Pokud hodnotu nelze určit zcela podle položek výčtu, hodnota je naformátován jako celočíselnou hodnotu. Následující příklad ukazuje specifikátor formátu F.<br><br>[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)] |  
| D nebo d | Zobrazí položku výčtu jako celočíselnou hodnotu v nejkratší možné reprezentaci. Následující příklad ukazuje specifikátor formátu D.<br><br>[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)] |  
| X nebo x | Zobrazí výčet položku jako šestnáctkové hodnoty. Hodnota je zajistit, že hodnota je minimální osm číslic v rozsahu určeném úvodními nulami podle potřeby. Následující příklad ukazuje specifikátor formátu X.<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)] |  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje výčet nazvaný `Colors` , tvoří tři položky: `Red`, `Blue`, a `Green`.  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 Po definování výčtu instance lze deklarovat následujícím způsobem.  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 `Color.ToString(System.String)` Metoda pak lze použít k zobrazení hodnot výčtu různými způsoby v závislosti na specifikátor formátu do ní předán.  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
