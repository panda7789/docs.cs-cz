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
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349115"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je spojen s třídou nebo strukturou ve velkém, a nikoli s konkrétní instancí třídy nebo struktury.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="when-to-use-shared"></a>Kdy použít Shared  
 Sdílení člena třídy nebo struktury zpřístupňuje každou instanci, nikoli *nesdílenou*, kde každá instance udržuje svou vlastní kopii. To je užitečné, například pokud se hodnota proměnné vztahuje na celou aplikaci. Pokud deklarujete tuto proměnnou, která má být `Shared`, pak všechny instance budou přistupovat ke stejnému umístění úložiště a pokud jedna instance změní hodnotu proměnné, všechny instance budou přistupovat k aktualizované hodnotě.  
  
 Sdílení nemění úroveň přístupu člena. Člen třídy může být například sdílen a privátní (přístupný pouze v rámci třídy) nebo nesdílené a veřejné. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** `Shared` můžete použít jenom na úrovni modulu. To znamená, že kontext deklarace pro prvek `Shared` musí být třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.  
  
- **Kombinované modifikátory.** V rámci stejné deklarace nelze zadat `Shared` spolu s [přepsáními](../../../visual-basic/language-reference/modifiers/overrides.md), [overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)nebo [static](../../../visual-basic/language-reference/modifiers/static.md) .  
  
- **Přístup k.** Ke sdílenému elementu přistupujete tak, že ho zařadíte s názvem jeho třídy nebo struktury, nikoli s názvem proměnné konkrétní instance své třídy nebo struktury. Pro přístup ke sdíleným členům nemusíte ani vytvářet instanci třídy nebo struktury.  
  
     Následující příklad volá sdílenou proceduru <xref:System.Double.IsNaN%2A> vystavenou strukturou <xref:System.Double>.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Implicitní sdílení.** V [příkazu const](../../../visual-basic/language-reference/statements/const-statement.md)nelze použít modifikátor `Shared`, ale konstanty jsou implicitně sdíleny. Podobně nemůžete deklarovat člena modulu nebo rozhraní, které se má `Shared`, ale budou implicitně sdíleny.  
  
## <a name="behavior"></a>Chování  
  
- **Pamì.** Sdílená proměnná nebo událost je uložena v paměti pouze jednou, bez ohledu na to, kolik instancí tvoří svou třídu nebo strukturu. Podobně sdílená procedura nebo vlastnost obsahuje pouze jednu sadu místních proměnných.  
  
- **Přístup prostřednictvím proměnné instance.** Je možné přistupovat ke sdílenému prvku tím, že je kvalifikován s názvem proměnné, která obsahuje konkrétní instanci své třídy nebo struktury. I když to obvykle funguje podle očekávání, kompilátor vygeneruje zprávu upozornění a provede přístup prostřednictvím třídy nebo názvu struktury namísto proměnné.  
  
- **Přístup prostřednictvím výrazu instance.** Pokud přistupujete ke sdílenému prvku prostřednictvím výrazu, který vrací instanci své třídy nebo struktury, kompilátor provede přístup prostřednictvím třídy nebo názvu struktury namísto vyhodnocení výrazu. Výsledkem je neočekávané výsledky, pokud jste určili výraz k provádění dalších akcí a také k vrácení instance. Toto dokládá následující příklad.  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     V předchozím příkladu kompilátor vygeneruje zprávu upozornění, kolikrát kód přistupuje ke sdílené proměnné `total` prostřednictvím instance. V každém případě přistupuje přímo přes třídu `shareTotal` a nevyužívá žádné instance. V případě zamýšleného volání procedury `returnClass`to znamená, že ani nevygeneruje volání `returnClass`, takže se neprovádí další akce zobrazení "Function returnClass () s názvem".  
  
 V těchto kontextech lze použít modifikátor `Shared`:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Doba života v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
