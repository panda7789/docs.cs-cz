---
title: Finalizační metody (C# Programming Guide)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960508"
---
# <a name="finalizers-c-programming-guide"></a>Finalizační metody (C# Programming Guide)
Finalizační metody se používají k destrukci instancí tříd.  
  
## <a name="remarks"></a>Poznámky  
  
-   Finalizační metody nelze definovat ve strukturách. Používají se jenom s třídami.  
  
-   Třída může mít pouze jeden finalizační metodu.  
  
-   Finalizační metody nemůže zděděné nebo přetížené.  
  
-   Nelze volat finalizační metody. Jsou vyvolány automaticky.  
  
-   Finalizační metoda nepodporuje trvat modifikátory ani mít parametry.  
  
 Například tady je deklarace finalizační metodu pro `Car` třídy.
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

Finalizační metoda je také možné implementovat jako definici tělo výrazu, jak ukazuje následující příklad.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Implicitně volá finalizační metodu <xref:System.Object.Finalize%2A> v základní třídě objektu. Proto volání finalizační metoda implicitně převádějí na následující kód:  
  
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
  
 To znamená, že `Finalize` metoda se volá rekurzivně pro všechny instance v řetězu dědičnosti z nejvíce odvozenému pro nejméně odvozené.  
  
> [!NOTE]
>  Prázdné finalizační metody se nesmí používat. Pokud třída obsahuje finalizační metodu, je vytvořena položka v `Finalize` fronty. Když je zavolána finalizační metodu, je vyvolána systému uvolňování paměti ke zpracování fronty. Prázdná finalizační metoda způsobí pouze zbytečně ke ztrátě výkonu.  
  
 Programátor nemá žádnou kontrolu nad při finalizační metoda je volána, protože ta se určují podle systému uvolňování paměti. Kontroluje, systému uvolňování paměti pro objekty, které jsou již nejsou déle používány aplikací. Pokud bude objekt oprávnění k dokončení, volá finalizační metody (pokud existuje) a uvolňování paměti pro ukládání objektu. Finalizační metody se také označují jako při ukončení programu.  
  
 Je možné vynutit uvolnění voláním <xref:System.GC.Collect%2A>, ale ve většině případů, toto by měl být vyhnout, protože může způsobit problémy s výkonem.  
  
## <a name="using-finalizers-to-release-resources"></a>Pomocí finalizační metody k uvolnění prostředků  
 Obecně platí C# nevyžaduje, aby Správa tolik paměti, jak je zapotřebí při vývoji v jazyce, který sdělení nebudete cílit na modul runtime s uvolňování paměti. Je to proto, že uvolňování paměti rozhraní .NET Framework implicitně spravuje přidělování a uvolňování paměti pro objekty. Ale když vaše aplikace zapouzdřuje nespravované prostředky, jako jsou windows, soubory a připojení k síti, by měl použít finalizační metody k uvolnění těchto prostředků. Pokud je objekt oprávnění k dokončení, uvolňování paměti běží `Finalize` metodu objektu.  
  
## <a name="explicit-release-of-resources"></a>Explicitní uvolnění prostředků  
 Pokud vaše aplikace používá nákladné externí prostředek, doporučujeme také, že poskytují způsob, jak explicitně uvolnění prostředku před systému uvolňování paměti uvolní objekt. Můžete to provést pomocí implementace `Dispose` metodu z <xref:System.IDisposable> rozhraní, které provádí potřebné vyčištění objektu. To může výrazně zlepšit výkon aplikace. I při tomto explicitní kontrolu nad prostředky, finalizační metodu, stane se ochrana pro vyčištění prostředků, pokud volání `Dispose` metody se nezdařilo.  
  
 Podrobné informace o vymazání prostředků naleznete v následujících tématech:  
  
-   [Vymazání nespravovaných prostředků](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Implementace metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři třídy, které usnadňují řetězu dědičnosti. Třída `First` je základní třídou `Second` je odvozen z `First`, a `Third` je odvozen z `Second`. Všechny tři mají finalizační metody. V `Main`, je vytvořena instance třídy odvozený. Když se program spouští, Všimněte si, že finalizační metody pro tři třídy jsou volaní automaticky a v pořadí, nejvíce odvozenému na typ derived nejméně.  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IDisposable>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Uvolňování paměti](../../../standard/garbage-collection/index.md)
