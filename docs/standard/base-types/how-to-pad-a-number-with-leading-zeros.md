---
title: 'Postupy: Zarovnání čísla úvodními nulami'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3cc6e4d96378cfd8c065a3b04aab865f9b787438
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086719"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Postupy: Zarovnání čísla úvodními nulami
Můžete přidat počáteční nuly na celé číslo pomocí "D" [řetězec standardního číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md) specifikátorem přesnosti. Můžete přidat počáteční nuly celého čísla a čísla s plovoucí desetinnou čárkou pomocí [vlastní číselný formátovací řetězec](../../../docs/standard/base-types/custom-numeric-format-strings.md). Toto téma ukazuje, jak používat obě metody k zarovnání čísla úvodními nulami.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Pro vyplnění celého čísla úvodními nulami na konkrétní délku  
  
1.  Určete minimální počet číslic, které chcete, aby celočíselnou hodnotu pro zobrazení. Zahrňte všechny úvodní číslice tohoto čísla.  
  
2.  Určete, zda chcete pro zobrazení na celé číslo jako hodnotu Desítková nebo šestnáctková hodnota.  
  
    -   Pro zobrazení na celé číslo jako hodnotu decimal, volejte jeho `ToString(String)` a předáte řetězec "D*n*" jako hodnotu `format` parametr, kde *n* představuje minimální délka řetězce.  
  
    -   Pro zobrazení na celé číslo jako šestnáctkové hodnoty, volejte jeho `ToString(String)` a předáte řetězec "X*n*" jako hodnotu `format` parametr, kde *n* představuje minimální délku řetězec.  
  
     Můžete také použít řetězec formátu v metodě, například <xref:System.String.Format%2A> nebo <xref:System.Console.WriteLine%2A>, který používá [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 Následující příklad formátuje několik celočíselné hodnoty počátečními nulami tak, aby celková délka naformátovaného čísla alespoň osm znaků.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Pro vyplnění celé číslo s konkrétní počet počáteční nuly  
  
1.  Určete, kolik počátečních nul chcete celočíselnou hodnotu pro zobrazení.  
  
2.  Určete, zda chcete pro zobrazení na celé číslo jako hodnotu Desítková nebo šestnáctková hodnota. Formátování jako desítková hodnota vyžaduje, že používáte specifikátor standardního formátu "D"; formátování jako šestnáctková hodnota vyžaduje, že používáte specifikátor standardního formátu "X".  
  
3.  Určuje délku nedoplněného číselný řetězec voláním celočíselnou hodnotu `ToString("D").Length` nebo `ToString("X").Length` metody.  
  
4.  Přidáte počet počátečních nul, které chcete zahrnout do formátovaný řetězec, který má délku nedoplněného číselné řetězce. Definuje celková délka doplněného řetězce.  
  
5.  Volání celočíselnou hodnotu `ToString(String)` a předáte řetězec "D*n*" decimal řetězců a "X*n*" pro řetězce v šestnáctkovém formátu, ve kterém *n* představuje celkový počet Délka vyplněný řetězce. Můžete také použít "D*n*" nebo "X*n*" formátovací řetězec v metodě, která podporuje složené formátování.  
  
 Následující příklad vyplní celočíselnou hodnotu pěti nulami.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Pro vyplnění číselnou hodnotu počátečními nulami na konkrétní délku  
  
1.  Určete, kolik číslic nalevo od desetinné čárky chcete řetězcové vyjádření čísla mít. Zahrnout všechny úvodní nuly v tomto celkový počet číslic.  
  
2.  Definujte vlastní číselný formátovací řetězec, který používá k reprezentaci minimální počet nul zástupný symbol nula ("0").  
  
3.  Zavolejte na číslo `ToString(String)` metoda a předejte jí řetězec vlastního formátu. Řetězec vlastního formátu můžete také použít s metodou, která podporuje složené formátování.  
  
 Následující příklad formátuje několik číselných hodnot počátečními nulami tak, aby celková délka naformátovaného čísla alespoň osm číslic nalevo od desetinné čárky.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Pro vyplnění číselná hodnota s konkrétní počet počáteční nuly  
  
1.  Určete, kolik počátečních nul chcete číselná hodnota, která mají.  
  
2.  Určete počet číslic nalevo od desetinné čárky v nedoplněného číselný řetězec. To uděláte takto:  
  
    1.  Určení, zda řetězcové vyjádření čísla zahrnuje symbol desetinné čárky.  
  
    2.  Pokud je symbol desetinné čárky, určete počet znaků vlevo od desetinné čárky.  
  
         -nebo-  
  
         Pokud ho nezahrnete symbol desetinné čárky, určení délky řetězce.  
  
3.  Vytvořte vlastní formátovací řetězec, který používá zástupný symbol nula ("0") pro každou z počátečních nul se zobrazí v řetězci, a k reprezentaci jednotlivých číslice ve výchozí řetězec, který používá zástupný symbol nula nebo zástupný symbol číslice ("#").  
  
4.  Zadat vlastní řetězec formátu jako parametr buď na číslo `ToString(String)` metodu nebo metodu, která podporuje složené formátování.  
  
 Následující příklad vyplní dvě <xref:System.Double> hodnoty pěti nulami.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
- [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
