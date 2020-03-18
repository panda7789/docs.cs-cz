---
title: Finalizační metody – programovací příručka Jazyka C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: c8ad738baa3ff76cf9ae8367f2fd2a1fb44a79d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170296"
---
# <a name="finalizers-c-programming-guide"></a>Finalizační metody (Průvodce programováním jazyka C#)
Finalizační metody (které se také nazývají **destruktory)** se používají k provedení všech nezbytných konečných vyčištění při shromažďování instance třídy systémem uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
  
- Finalizační metody nelze definovat ve strukturách. Používají se pouze s třídami.  
  
- Třída může mít pouze jednu finalizační metodu.  
  
- Finalizační metody nelze zdědit nebo přetížené.  
  
- Finalizační metody nelze volat. Jsou vyvolány automaticky.  
  
- Finalizační metoda nepřijímá modifikátory nebo má parametry.  
  
 Například následující je deklarace finalizační metody `Car` pro třídu.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Finalizační metodu lze také implementovat jako definici těla výrazu, jak ukazuje následující příklad.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Finalizační metoda implicitně volá <xref:System.Object.Finalize%2A> základní třídu objektu. Proto volání finalizační metody je implicitně přeloženo do následujícího kódu:  
  
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
  
 To znamená, `Finalize` že metoda se nazývá rekurzivně pro všechny instance v řetězci dědičnosti, od nejvíce odvozených po nejméně odvozené.  
  
> [!NOTE]
> Prázdné finalizační metody by neměly být používány. Pokud třída obsahuje finalizační metodu, je `Finalize` ve frontě vytvořena položka. Při volání finalizační metody je vyvolána systém uvolňování paměti ke zpracování fronty. Prázdná finalizační metoda způsobí zbytečnou ztrátu výkonu.  
  
 Programátor nemá žádnou kontrolu nad při finalizační metody je volána, protože to je určeno uvolňování paměti. Systém uvolňování paměti kontroluje objekty, které již nejsou používány aplikací. Pokud považuje objekt způsobilý pro dokončení, volá finalizační metodu (pokud existuje) a uvolní paměť použitou k uložení objektu.

 V aplikacích rozhraní .NET Framework (ale ne v aplikacích .NET Core) jsou při ukončení programu také volány finalizační metody.
  
 Je možné vynutit uvolňování <xref:System.GC.Collect%2A>paměti voláním , ale většinu času, je třeba se tomu vyhnout, protože může způsobit problémy s výkonem.  
  
## <a name="using-finalizers-to-release-resources"></a>Použití finalizačních metod k uvolnění prostředků  
 Obecně c# nevyžaduje tolik správy paměti, jak je potřeba při vývoji s jazykem, který necílí na runtime s uvolňování paměti. Důvodem je, že systém uvolňování paměti rozhraní .NET Framework implicitně spravuje přidělení a uvolnění paměti pro vaše objekty. Pokud však aplikace zapouzdřuje nespravované prostředky, jako jsou okna, soubory a síťová připojení, měli byste tyto prostředky uvolnit pomocí finalizačních metod. Pokud je objekt způsobilý pro dokončení, systém `Finalize` uvolňování paměti spustí metodu objektu.  
  
## <a name="explicit-release-of-resources"></a>Explicitní uvolnění zdrojů  
 Pokud vaše aplikace používá nákladné externí prostředek, doporučujeme také poskytnout způsob, jak explicitně uvolnit prostředek před uvolňování uvolní objekt. Provedete to implementací `Dispose` metody <xref:System.IDisposable> z rozhraní, které provádí nezbytné vyčištění objektu. To může výrazně zlepšit výkon aplikace. I s touto explicitní kontrolu nad prostředky finalizační metody se stane `Dispose` ochrannou pro vyčištění prostředků, pokud volání metody se nezdařilo.  
  
 Další podrobnosti o čištění prostředků naleznete v následujících tématech:  
  
- [Vymazání nespravovaných prostředků](../../../standard/garbage-collection/unmanaged.md)  
  
- [Implementace metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using – příkaz](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři třídy, které vytvářejí řetězec dědičnosti. Třída `First` `Second` je základní třída, je `First`odvozena `Third` od , `Second`a je odvozen a . Všechny tři mají finalizační metody. V `Main`aplikaci je vytvořena instance nejvíce odvozené třídy. Při spuštění programu všimněte si, že finalizační metody pro tři třídy jsou volány automaticky a v pořadí od nejvíce odvozené k nejméně odvozené.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace naleznete v části [Destruktory](~/_csharplang/spec/classes.md#destructors) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).
  
## <a name="see-also"></a>Viz také

- <xref:System.IDisposable>
- [Programovací příručka jazyka C#](../index.md)
- [Konstruktory](./constructors.md)
- [Kolekce paměti](../../../standard/garbage-collection/index.md)
