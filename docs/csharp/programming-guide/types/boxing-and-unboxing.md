---
title: Zabalení a rozbalení C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 849983bb9cce6c9e0f41247a898747300fd29435
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588531"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Zabalení a rozbalení (Průvodce programováním v C#)
Zabalení je proces převodu [typu hodnoty](../../language-reference/keywords/value-types.md) na typ `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Když pole CLR vyhodnotí typ hodnoty, zalomí hodnotu uvnitř <xref:System.Object?displayProperty=nameWithType> instance a uloží ji na spravovanou haldu. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; rozbalení je explicitní. Pojem zabalení a rozbalení představuje C# sjednocený pohled na systém typů, ve kterém může být hodnota libovolného typu považována za objekt.  
  
 V následujícím příkladu je proměnná `i` typu Integer *zabalená* a přiřazená objektu. `o`  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 Objekt `o` pak může být nezabalený a přiřazený celočíselné `i`proměnné:  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 Následující příklady ilustrují, jak se používá zabalení C#v.  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a>Výkon  
 Ve vztahu k jednoduchým přiřazením se zabalení a rozbalení počítají jako výpočetní náročné procesy. Když je hodnotový typ v krabici, musí být přidělen a vytvořen nový objekt. V menší míře je přetypování vyžadované pro rozbalení také nákladné výpočetní. Další informace najdete v tématu [výkon](../../../framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Zabalení  
 Zabalení se používá k ukládání typů hodnot v haldě uvolňování paměti. Zabalení je implicitní převod [typu hodnoty](../../language-reference/keywords/value-types.md) na typ `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Zabalení typu hodnoty přiděluje instanci objektu na haldě a zkopíruje hodnotu do nového objektu.  
  
 Zvažte následující deklaraci proměnné typu hodnoty:  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 Následující příkaz implicitně aplikuje operaci zabalení na proměnnou `i`:  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 Výsledek tohoto příkazu vytváří odkaz `o`na objekt v zásobníku, který odkazuje na hodnotu typu `int`, na haldě. Tato hodnota je kopií hodnoty typu hodnoty přiřazené proměnné `i`. Rozdíl mezi dvěma proměnnými `i` a `o`, je znázorněno na následujícím obrázku převodu zabalení:  
  
 ![Obrázek znázorňující rozdíl mezi proměnnými i a o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení není nikdy vyžadováno:  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a>Popis  
 Tento příklad převede proměnnou `i` celého čísla na objekt `o` pomocí zabalení. Pak se hodnota uložená v proměnné `i` změní z `123` na `456`. Příklad ukazuje, že původní typ hodnoty a zabalený objekt používají oddělené umístění paměti, a proto může ukládat jiné hodnoty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a>Rozbalení  
 Rozbalení je explicitní převod z typu `object` na [typ hodnoty](../../language-reference/keywords/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní. Rozbalení operace se skládá z těchto:  
  
- Kontrola instance objektu, aby se zajistilo, že se jedná o zabalenou hodnotu daného typu hodnoty.  
  
- Zkopírování hodnoty z instance do proměnné typu hodnoty.  
  
 Následující příkazy ukazují operace zabalení a rozbalení:  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 Následující obrázek ukazuje výsledek předchozích příkazů: 
  
 ![Obrázek znázorňující převod rozbalení](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 Pro rozbalení typů hodnot, které mají být v době běhu úspěšné, musí být položka unboxed odkaz na objekt, který byl dříve vytvořen zabalením instance daného typu hodnoty. Pokus o unbox `null` <xref:System.NullReferenceException>způsobí. Pokus o unbox odkazu na nekompatibilní typ hodnoty způsobí <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje případ neplatného rozbalení a výsledného `InvalidCastException`. Při `try` použití `catch`a se zobrazí chybová zpráva, když dojde k chybě.  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 Výstup tohoto programu:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Pokud změníte příkaz:  
  
```csharp
int j = (short) o;  
```  
  
 na  
  
```csharp
int j = (int) o;  
```  
  
 provede se převod a zobrazí se výstup:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Odkazové typy](../../language-reference/keywords/reference-types.md)  
  
- [Typy hodnot](../../language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
