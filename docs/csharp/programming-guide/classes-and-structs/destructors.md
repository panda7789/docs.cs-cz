---
title: Finalizační metody – C# Průvodce programováním
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 9c00f14da9d79418e4fb204bac30e539b234197f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715017"
---
# <a name="finalizers-c-programming-guide"></a>Finalizační metody (C# Průvodce programováním)
Finalizační metody (označované také jako **destruktory**) se používají k provedení všech nezbytných finálních vyčištění při shromažďování instance třídy systémem uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
  
- Finalizační metody nelze definovat ve strukturách. Používají se pouze s třídami.  
  
- Třída může mít pouze jeden finalizační metodu.  
  
- Finalizační metody nemůžou být zděděné nebo přetížené.  
  
- Finalizační metody nelze volat. Jsou vyvolány automaticky.  
  
- Finalizační metoda nepřijímá modifikátory nebo má parametry.  
  
 Například následující je deklarace finalizační metody pro třídu `Car`.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Finalizační metodu lze také implementovat jako definici těla výrazu, jak ukazuje následující příklad.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Finalizační metoda implicitně volá <xref:System.Object.Finalize%2A> základní třídy objektu. Proto volání finalizační metody je implicitně přeloženo na následující kód:  
  
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
  
 To znamená, že metoda `Finalize` je volána rekurzivně pro všechny instance v řetězu dědičnosti, od nejvíce odvozené k nejméně odvozenému.  
  
> [!NOTE]
> Nemusíte používat prázdné finalizační metody. Pokud třída obsahuje finalizační metodu, je vytvořena položka ve frontě `Finalize`. Po volání finalizační metody je vyvolán systém uvolňování paměti pro zpracování fronty. Prázdný finalizační metoda vyvolá jenom nepotřebnou ztrátu výkonu.  
  
 Programátor nemá žádné řízení při volání finalizační metody, protože je určen systémem uvolňování paměti. Systém uvolňování paměti kontroluje objekty, které již aplikace nepoužívá. Pokud se považuje za objekt s nárokem na finalizaci, zavolá finalizační metodu (pokud existuje) a uvolní paměť použitou k uložení objektu. 
 
 V .NET Frameworkch aplikacích (ale ne v aplikacích .NET Core), jsou také volány finalizační metody při ukončení programu. 
  
 Je možné vynutit uvolňování paměti voláním <xref:System.GC.Collect%2A>, ale většinou by se to mělo vyhnout, protože může způsobit problémy s výkonem.  
  
## <a name="using-finalizers-to-release-resources"></a>Použití finalizační metody k uvolnění prostředků  
 Obecně platí, C# že při vývoji s jazykem, který necílí na modul runtime s uvolňováním paměti, nevyžaduje co největší správu paměti, jak je potřeba. Důvodem je to, že systém uvolňování paměti .NET Framework implicitně spravuje přidělování a uvolňování paměti pro vaše objekty. Pokud však vaše aplikace zapouzdřuje nespravované prostředky, jako jsou například Windows, soubory a síťová připojení, měli byste k uvolnění těchto prostředků použít finalizační metody. Pokud je objekt způsobilý pro finalizaci, systém uvolňování paměti spustí metodu `Finalize` objektu.  
  
## <a name="explicit-release-of-resources"></a>Explicitní vydání prostředků  
 Pokud vaše aplikace používá nákladný externí prostředek, doporučujeme vám, abyste poskytli způsob, jak prostředek explicitně uvolnit před tím, než systém uvolňování paměti uvolní objekt. To provedete implementací metody `Dispose` z rozhraní <xref:System.IDisposable>, které provádí nezbytné vyčištění objektu. To může výrazně zlepšit výkon aplikace. I s tímto explicitním ovládáním prostředků se finalizační metoda stala ochranou pro vyčištění prostředků v případě, že volání metody `Dispose` se nezdařilo.  
  
 Další podrobnosti o čištění prostředků najdete v následujících tématech:  
  
- [Vymazání nespravovaných prostředků](../../../standard/garbage-collection/unmanaged.md)  
  
- [Implementace metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using – příkaz](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři třídy, které tvoří řetěz dědičnosti. Třída `First` je základní třídou, `Second` je odvozena z `First`a `Third` je odvozena z `Second`. Všechny tři mají finalizační metody. V `Main`je vytvořena instance nejvíce odvozené třídy. Když se program spustí, Všimněte si, že finalizační metody pro tři třídy jsou volány automaticky a v pořadí od nejvíce odvozené k nejmenšímu odvozenému.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace naleznete v části [destruktory](~/_csharplang/spec/classes.md#destructors) [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).
  
## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable>
- [Průvodce programováním v jazyce C#](../index.md)
- [Konstruktory](./constructors.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
