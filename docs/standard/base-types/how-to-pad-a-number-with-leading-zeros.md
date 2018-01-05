---
title: "Postupy: Zarovnání čísla úvodními nulami"
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
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7ea854f69e59c614d03f10ff546bd3181f5b51ff
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Postupy: Zarovnání čísla úvodními nulami
Úvodní nuly na celé číslo můžete přidat pomocí "D" [standardního řetězce formátu čísel](../../../docs/standard/base-types/standard-numeric-format-strings.md) s specifikátorem přesnosti. Můžete přidat pomocí úvodní nuly celé číslo a čísla s plovoucí desetinnou čárkou [vlastní číselný formátovací řetězec](../../../docs/standard/base-types/custom-numeric-format-strings.md). Toto téma ukazuje, jak používat obě metody k zarovnání čísla úvodními nulami.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Chcete-li doplnit celé číslo s úvodními nulami na konkrétní délku  
  
1.  Určete minimální počet číslic, které chcete celočíselnou hodnotu pro zobrazení. Zahrňte všechny úvodní číslice toto číslo.  
  
2.  Určí, zda chcete zobrazit na celé číslo jako hodnotu decimal nebo šestnáctkové hodnoty.  
  
    -   Chcete-li zobrazit celé číslo jako hodnotu decimal, volejte jeho `ToString(String)` metoda a předejte jí řetězec "D*n*" jako hodnotu `format` parametr, kde  *n*  představuje minimální délka řetězce.  
  
    -   Pro zobrazení na celé číslo jako šestnáctkové hodnoty, volejte jeho `ToString(String)` metoda a předejte jí řetězec "X*n*" jako hodnotu `format` parametr, kde  *n*  představuje minimální délka řetězce.  
  
     Můžete také použít řetězec formátu metoda, jako například <xref:System.String.Format%2A> nebo <xref:System.Console.WriteLine%2A>, která používá [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 Následující příklad formátuje několik celočíselné hodnoty úvodními nulami tak, aby celková délka číslo naformátovaný aspoň osm znaků.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Chcete-li doplnit celé číslo s konkrétní počet úvodní nuly  
  
1.  Určete, kolik úvodní nuly chcete celočíselnou hodnotu pro zobrazení.  
  
2.  Určí, zda chcete zobrazit na celé číslo jako hodnotu decimal nebo šestnáctkové hodnoty. Formátování jako desítkovou hodnotu vyžaduje, abyste používali specifikátor standardní formát "D"; formátování jako šestnáctkové hodnoty vyžaduje, že používáte specifikátor standardní formát "X".  
  
3.  Určete délku nedoplněného číselných řetězců voláním celočíselnou hodnotu `ToString("D").Length` nebo `ToString("X").Length` metoda.  
  
4.  Přidáte počet úvodní nuly, které chcete zahrnout do formátovaný řetězec, který má délku nedoplněného číselných řetězců. Definuje celková délka doplněného řetězce.  
  
5.  Volání celočíselnou hodnotu `ToString(String)` metoda a předejte jí řetězec "D*n*" pro desítkové řetězce a "X*n*" pro řetězce v šestnáctkovém, kde  *n*  představuje celková délka doplněného řetězce. Můžete také "D*n*" nebo "X*n*" naformátovat řetězec v metodu, která podporuje složené formátování.  
  
 Následující příklad doplní hodnotu celého čísla úvodními nulami pět.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Chcete-li doplnit číselnou hodnotu úvodními nulami na konkrétní délku  
  
1.  Určete, kolik číslic nalevo od desetinné čárky chcete řetězcovou reprezentaci číslo, které má mít. Zahrnout všechny úvodní nuly v celkový počet číslic.  
  
2.  Definujte vlastní číselného formátu řetězec, který používá nulový zástupný symbol ("0"), které představují minimální počet nul.  
  
3.  Zavolat číslo `ToString(String)` metoda a předejte ji vlastní řetězec formátu. Můžete také vlastní formátovací řetězec pomocí metody, která podporuje složené formátování.  
  
 Následující příklad formátuje několik číselných hodnot úvodními nulami tak, aby celková délka číslo formátovaný alespoň osm číslic nalevo od desetinné čárky.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Chcete-li doplnit číselnou hodnotu s konkrétní počet úvodní nuly  
  
1.  Určete, kolik úvodní nuly chcete číselná hodnota, která mají.  
  
2.  Určete počet číslic nalevo od desetinné čárky v nedoplněného číselných řetězců. Provedete to následujícím způsobem:  
  
    1.  Určí, zda řetězcovou reprezentaci číslo obsahuje symbol desetinné čárky.  
  
    2.  Pokud obsahuje symbol desetinné čárky, určete počet znaků směrem doleva od desetinné čárky.  
  
         -nebo-  
  
         Pokud nebude obsahovat symbol desetinné čárky, zjistěte délku řetězce.  
  
3.  Vytvoření vlastní formát řetězce používající nulový zástupný symbol ("0") pro každou úvodní nuly se objeví v řetězci, který používá nulový zástupný symbol nebo zástupný symbol číslice ("#") k reprezentaci jednotlivých číslice v výchozí řetězec.  
  
4.  Zadat vlastní řetězec formátu jako parametr buď na číslo `ToString(String)` metodu nebo metodu, která podporuje složené formátování.  
  
 Následující příklad doplňuje dvě <xref:System.Double> hodnoty pěti úvodními nulami.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
