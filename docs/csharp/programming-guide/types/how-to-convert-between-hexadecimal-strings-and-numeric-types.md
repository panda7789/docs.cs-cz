---
title: Převod mezi šestnáctkovými řetězci a číselnými typy – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0e1f6ad2606b367d369c1c644c947831b2aa8289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698518"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Převod mezi šestnáctkovými řetězci a číselnými typy (Průvodce programováním jazyka C#)
Tyto příklady ukazují, jak provádět následující úkoly:  
  
- Získejte šestnáctkovou hodnotu každého znaku v [řetězci](../../language-reference/builtin-types/reference-types.md).  
  
- Získejte [znak,](../../language-reference/builtin-types/char.md) který odpovídá každé hodnotě v šestnáctkovém řetězci.  
  
- Převeďte šestnáctkový `string` na [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Převeďte šestnáctkový `string` převodník na [plovák](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Převeďte [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na šestnáctkové `string`pole .  
  
## <a name="example"></a>Příklad  
 Tento příklad vyvodí šestnáctkovou hodnotu `string`každého znaku v . Nejprve analyzuje `string` pole znaků. Potom volá <xref:System.Convert.ToInt32%28System.Char%29> každý znak získat jeho číselnou hodnotu. Nakonec zformátuje číslo jako jeho šestnáctkové znázornění `string`v .  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Příklad  
 Tento příklad analyzuje `string` šestnáctkové hodnoty a výstupy znak odpovídající každé šestnáctkové hodnoty. Nejprve volá [Split(Char\[\])](xref:System.String.Split(System.Char[])) metoda získat každou šestnáctkovou hodnotu jako jednotlivec `string` v poli. Pak volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> převést šestnáctkovou hodnotu na desetinnou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby, jak získat znak odpovídající tomuto kódu znaku. Používá první <xref:System.Char.ConvertFromUtf32%28System.Int32%29>technika , která vrátí znak odpovídající argumentu `string`celé číslo jako . Druhá technika explicitně `int` vrhá char [.](../../language-reference/builtin-types/char.md)  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje jiný způsob, jak převést šestnáctkové `string` na celé <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> číslo voláním metody.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést šestnáctkové `string` na [float](../../language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> a metody.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na šestnáctkový <xref:System.BitConverter?displayProperty=nameWithType> řetězec pomocí třídy.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Viz také

- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Jak určit, jestli řetězec představuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
