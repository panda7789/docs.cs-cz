---
title: Zabalení a rozbalení - C# Průvodce programováním
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
ms.openlocfilehash: 811123ac195bbc92d9e690dcd828535daa246460
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878943"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Zabalení a rozbalení (Průvodce programováním v C#)
Zabalení je proces převodu [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Když modul CLR pole typu hodnoty, obtéká hodnotu uvnitř <xref:System.Object?displayProperty=nameWithType> instance a uloží ji na spravované haldě. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; Rozbalení je explicitní. Pojem zabalení a rozbalení základem sjednocené zobrazení C# systému typů, ve kterém lze považovat hodnotu libovolného typu za objekt.  
  
 V následujícím příkladu proměnná integer `i` je *boxed* a přiřazené k objektu `o`.  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 Objekt `o` lze potom rozbalit a přiřadit k proměnné celého čísla `i`:  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 Následující příklady ilustrují použití zabalení v jazyce C#.  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a>Výkon  
 Vzhledem k jednoduchým přiřazením jsou zabalení a rozbalení výpočetně náročné procesy. Když je typ hodnoty v poli, musí být přiděleny a konstruovány nový objekt. V menší míře je přetypování potřebné pro rozbalení je také nákladné výpočetně. Další informace najdete v tématu [výkonu](../../../../docs/framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Zabalení  
 Zabalení slouží k uložení typů hodnot haldy uvolňování. Zabalení je implicitní převod [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Zabalení typu hodnoty přiděluje instance objektu na haldě a kopíruje hodnotu do nového objektu.  
  
 Vezměte v úvahu následující deklarace proměnné hodnotového typu:  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 Následující příkaz se implicitně týká operace zabalení pro proměnnou `i`:  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 Výsledkem tohoto příkazu je vytvoření odkazu na objekt `o`, v zásobníku, který odkazuje na hodnotu typu `int`, na haldě. Tuto hodnotu je kopií hodnoty hodnotového typu přiřazena k proměnné `i`. Rozdíl mezi dvěma proměnnými, `i` a `o`, je znázorněn na následujícím obrázku převod na uzavřené určení:  
  
 ![Obrázek znázorňující rozdíl mezi i a o proměnné.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 Je také možné provést zabalení explicitně jako v následujícím příkladu, ale nikdy není vyžadováno explicitní zabalení:  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a>Popis  
 V tomto příkladu se převede celočíselná proměnná `i` objektu `o` pomocí uzavřeného určení. Následně je hodnota uložená v proměnné `i` se změnil z `123` k `456`. Příklad ukazuje, že typ původní hodnoty a zabalený objekt používají samostatná paměťová místa a proto mohou uchovávat různé hodnoty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a>Rozbalení  
 Rozbalení je explicitní převod z typu `object` k [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) nebo z typu rozhraní na typ hodnoty, která implementuje rozhraní. Operace rozbalení se skládá ze:  
  
- Kontrola instance objektu, abyste měli jistotu, že se jedná o zabalenou hodnotu daného typu hodnoty.  
  
- Kopírování hodnoty z instance do proměnné typu hodnoty.  
  
 Následující příkazy ukazují operace zabalení a rozbalení:  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 Následující obrázek ukazuje výsledek předchozích příkazů: 
  
 ![Obrázek znázorňující unboxingového převodu.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 Pro rozbalení typů hodnot v době spuštění úspěšné, musí být rozbalená položka odkazem na objekt, který byl dříve vytvořen zabalením instance tohoto typu hodnoty. Při pokusu o rozbalení `null` způsobí, že <xref:System.NullReferenceException>. Při pokusu o vybalení odkazu na nekompatibilní hodnotu způsobí typ <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje případ neplatného rozbalení a výsledné `InvalidCastException`. Pomocí `try` a `catch`, když dojde k chybě, zobrazí se chybová zpráva.  
  
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
  
 Převod se provede, a zobrazí se výstup:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
  
- [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
