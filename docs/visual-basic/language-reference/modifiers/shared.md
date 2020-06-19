---
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: b51c88e1af3a720912af8ba6aaf8ae4016af9cfa
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990188"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)

Určuje, že nejmíň jeden deklarovaný programový prvek je spojen s třídou nebo strukturou ve velkém, a nikoli s konkrétní instancí třídy nebo struktury.

## <a name="when-to-use-shared"></a>Kdy použít Shared

Sdílení člena třídy nebo struktury zpřístupňuje každou instanci, nikoli *nesdílenou*, kde každá instance udržuje svou vlastní kopii. Sdílení je užitečné, například pokud se hodnota proměnné vztahuje na celou aplikaci. Pokud deklarujete tuto proměnnou `Shared` , pak všechny instance budou přistupovat ke stejnému umístění úložiště a pokud jedna instance změní hodnotu proměnné, všechny instance budou přistupovat k aktualizované hodnotě.

Sdílení nemění úroveň přístupu člena. Například člen třídy může být sdílen a soukromý (přístupný pouze z třídy) nebo nesdílené a veřejné. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Můžete použít `Shared` pouze na úrovni modulu. To znamená, že kontext deklarace pro `Shared` prvek musí být třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.

- **Kombinované modifikátory.** `Shared`V rámci stejné deklarace nelze zadat společně s [Overrides](overrides.md), [overridable](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md)nebo [static](static.md) .

- **Přístup k.** Ke sdílenému elementu přistupujete tak, že ho zařadíte s názvem jeho třídy nebo struktury, nikoli s názvem proměnné konkrétní instance své třídy nebo struktury. Pro přístup ke sdíleným členům nemusíte ani vytvářet instanci třídy nebo struktury.

     V následujícím příkladu je volána sdílená procedura <xref:System.Double.IsNaN%2A> vystavená <xref:System.Double> strukturou.

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- **Implicitní sdílení.** `Shared`V [příkazu const](../statements/const-statement.md)nelze použít modifikátor, ale konstanty jsou implicitně sdíleny. Podobně nemůžete deklarovat člen modulu nebo rozhraní, které mají být `Shared` , ale budou implicitně sdíleny.

## <a name="behavior"></a>Chování

- **Pamì.** Sdílená proměnná nebo událost je uložena v paměti pouze jednou, bez ohledu na to, kolik instancí tvoří svou třídu nebo strukturu. Podobně sdílená procedura nebo vlastnost obsahuje pouze jednu sadu místních proměnných.

- **Přístup prostřednictvím proměnné instance.** Je možné přistupovat ke sdílenému prvku tím, že je kvalifikován s názvem proměnné, která obsahuje konkrétní instanci své třídy nebo struktury. I když to obvykle funguje podle očekávání, kompilátor vygeneruje zprávu upozornění a provede přístup prostřednictvím třídy nebo názvu struktury namísto proměnné.

- **Přístup prostřednictvím výrazu instance.** Pokud přistupujete ke sdílenému prvku prostřednictvím výrazu, který vrací instanci své třídy nebo struktury, kompilátor provede přístup prostřednictvím třídy nebo názvu struktury namísto vyhodnocení výrazu. Tento přístup vytvoří neočekávané výsledky, pokud jste určili výraz k provedení jiných akcí a také k vrácení instance. Následující příklad znázorňuje tuto situaci.
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     V předchozím příkladu kompilátor vygeneruje zprávu upozornění pokaždé, když kód přistupuje ke sdílené vlastnosti `Total` prostřednictvím instance. V každém případě je přístup přímo přes třídu `ShareTotal` a nevyužívá žádné instance. V případě zamýšleného volání procedury `ReturnClass` to znamená, že ani negeneruje volání `ReturnClass` , takže se neprovádí další akce zobrazení "Function ReturnClass () s názvem".

`Shared`V těchto kontextech lze použít modifikátor:

- [Dim – příkaz](../statements/dim-statement.md)
- [Event – příkaz](../statements/event-statement.md)
- [Function – příkaz](../statements/function-statement.md)
- [Operator – příkaz](../statements/operator-statement.md)
- [Property – příkaz](../statements/property-statement.md)
- [Sub – příkaz](../statements/sub-statement.md)
  
## <a name="see-also"></a>Viz také

- [Shadows](shadows.md)
- [Tras](static.md)
- [Doba platnosti v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
