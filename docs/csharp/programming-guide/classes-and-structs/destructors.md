---
title: Finalizační metody (C# Průvodce programováním)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313963"
---
# <a name="finalizers-c-programming-guide"></a>Finalizační metody (C# Průvodce programováním)
Finalizační metody se používají k destruct instance tříd.  
  
## <a name="remarks"></a>Poznámky  
  
-   Finalizační metody nemůže být definovaný ve struktury. Použijí se jenom s třídami.  
  
-   Třída může mít pouze jeden finalizační metodu.  
  
-   Finalizační metody nelze zděděná nebo přetížený.  
  
-   Nelze volat finalizační metody. Jsou vyvolány automaticky.  
  
-   Finalizační metody nemá trvat modifikátory nebo mít parametry.  
  
 Například následující je deklaraci finalizační metodu pro `Car` třídy.
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

Finalizační metody lze také implementovat jako definici textu výrazu, jak ukazuje následující příklad.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Implicitně volá finalizační metodu <xref:System.Object.Finalize%2A> na základní třídu objektu. Proto volání finalizační metody implicitně převést na následující kód:  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 To znamená, že `Finalize` metoda je volána rekurzivně pro všechny instance v řetězu dědičnosti z většinou odvozených pro odvozené nejmenší.  
  
> [!NOTE]
>  Prázdné finalizační metody by nemělo být použito. Pokud třída obsahuje finalizační metody, vytvoří se záznam v `Finalize` fronty. Při volání finalizační metodu volá se ke zpracování fronty uvolňování paměti. Prázdné finalizační metodu právě způsobí, že zbytečně snížením výkonu.  
  
 Programátorů nemá žádnou kontrolu nad při volání finalizační metodu, protože to je dáno uvolňování paměti. Uvolňování paměti kontroluje pro objekty, které jsou již používá aplikace. Pokud objekt považuje vhodné pro dokončení, zavolá finalizační metodu (pokud existuje) a uvolní paměť použitá k uložení objektu. Finalizační metody se také nazývají při ukončení programu.  
  
 Je možné vynutit uvolňování voláním <xref:System.GC.Collect%2A>, ale ve většině případů, to je nutno vzhledem k tomu může způsobit problémy s výkonem.  
  
## <a name="using-finalizers-to-release-resources"></a>Pomocí finalizační metody k prostředkům verze  
 Obecně platí jazyka C# nevyžaduje, aby Správa tolik paměti, jako je potřeba při vývoji v jazyce, který není zaměřen modulu runtime s uvolňování paměti. To je proto garbage collector v rozhraní .NET Framework implicitně spravuje přidělování a uvolňování paměti pro objektů. Ale při aplikaci zapouzdří nespravovaných prostředků, jako jsou windows, soubory a připojení k síti, byste měli použít finalizační metody k uvolnění těchto prostředků. Pokud je objekt vhodné pro dokončení, bude systém uvolňování běží `Finalize` metodu objektu.  
  
## <a name="explicit-release-of-resources"></a>Explicitní uvolnění prostředků  
 Pokud vaše aplikace používá nákladné externí prostředek, doporučujeme také zadat způsob, jak explicitně verzi prostředku před uvolňování uvolní objekt. To provedete tím, že implementujete `Dispose` metoda z <xref:System.IDisposable> rozhraní, které provádí nezbytné vyčištění pro objekt. To může výrazně zlepšit výkon aplikace. I přes tato explicitní kontrolu nad prostředky finalizační metodu bude chránit vyčištění prostředků, pokud volání `Dispose` metoda se nezdařilo.  
  
 Další podrobnosti o vymazání prostředků najdete v následujících tématech:  
  
-   [Vymazání nespravovaných prostředků](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Implementace metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři třídy, které Ujistěte se, řetězce dědičnosti. Třída `First` je základní třídou `Second` je odvozený od `First`, a `Third` je odvozený od `Second`. Všechny tři mít finalizační metody. V `Main`, je vytvořena instance většinou odvozených tříd. Když se program spouští, Všimněte si, že finalizační metody pro tři třídy jsou volány automaticky a v pořadí, z většinou odvozených pro odvozené nejmenší.  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IDisposable>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Uvolňování paměti](../../../standard/garbage-collection/index.md)
