---
title: Zabalení a rozbalení (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 4cf6a81a2738d4aff94089c89fcc39e785127a82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336128"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Zabalení a rozbalení (Průvodce programováním v C#)
Zabalení je proces převodu [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo k libovolnému typu rozhraní implementované tento typ hodnoty. Když modulu CLR oknech typ hodnoty, zabalí hodnotu uvnitř System.Object a uloží je v spravovaná halda. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; Rozbalení je explicitní. Koncept zabalení a rozbalení základem zobrazení jazyka C# unified typ systému, ve kterém lze hodnotu libovolného typu zacházet jako objekt.  
  
 V následujícím příkladu, proměnná s celým číslem `i` je *do pole* a přiřazené k objektu `o`.  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 Objekt `o` lze poté nezabalený a přiřazená proměnná s celým číslem `i`:  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Následující příklady ilustrují použití zabalení v C#.  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Výkon  
 Ve vztahu k jednoduché přiřazení zabalení a rozbalení jsou náročné procesy. Pokud je do pole zadejte hodnotu, musí být nový objekt přidělené a zkonstruovat. V menší míře přetypování požadované pro rozbalení je také nákladné u. Další informace najdete v tématu [výkonu](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).  
  
## <a name="boxing"></a>Zabalení  
 Zabalení slouží k uložení hodnotové typy v haldě uvolňování paměti. Zabalení je implicitní převod [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo k libovolnému typu rozhraní implementované tento typ hodnoty. Zabalení typu hodnoty přiděluje instanci objektu v haldě a hodnota zkopírována do nového objektu.  
  
 Vezměte v úvahu následující deklaraci typu hodnoty proměnné:  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 Operace zabalení na proměnnou implicitně platí následující příkaz `i`:  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 Výsledek tohoto prohlášení vytváří odkaz na objekt `o`, v zásobníku, která odkazuje na hodnotu typu `int`, v haldě. Tato hodnota je kopii typ hodnoty hodnotu přiřazenou proměnné `i`. Rozdíl mezi dvě proměnné, `i` a `o`, je znázorněno na následujícím obrázku.  
  
 ![BoxingConversion – grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Převod zabalení  
  
 Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení je nutná nikdy:  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Popis  
 Tento příklad převede proměnná typu integer `i` do objektu `o` s použitím zabalení. Potom s hodnotou uloženou v proměnné `i` změněn z `123` k `456`. Příklad ukazuje, že původní typ hodnoty a objekt zabalené použít samostatnou paměť umístění a proto můžete ukládat různé hodnoty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Rozbalení  
 Rozbalení je explicitní převod z typu `object` k [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní. Rozbalení operace se skládá z:  
  
-   Kontrola instance objektu a ujistěte se, že se jedná o zabalené hodnoty typu předané hodnoty.  
  
-   Kopírování hodnotu z instance do proměnné typ hodnoty.  
  
 Následující příkazy ukazují, jak zabalení a rozbalení operace:  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 Následující obrázek ukazuje výsledek předchozí příkazy.  
  
 ![Rozbalení převod obrázku](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Převodu rozbalení  
  
 Položka se nezabalený rozbalení typů hodnot v době běhu proběhla úspěšně, musí být odkaz na objekt, který byl dříve vytvořen zabalení instance tohoto typu hodnoty. Probíhá pokus o unbox `null` způsobí, že <xref:System.NullReferenceException>. Probíhá pokus o unbox – odkaz na nekompatibilní hodnotu typu příčiny <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje rozbalení neplatný případ a výsledná `InvalidCastException`. Pomocí `try` a `catch`, chybová zpráva se zobrazí, když dojde k chybě.  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 Tento program výstupy:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Pokud změníte příkaz:  
  
```  
int j = (short) o;  
```  
  
 na  
  
```  
int j = (int) o;  
```  
  
 Převod se provede, a zobrazí se výstup:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
