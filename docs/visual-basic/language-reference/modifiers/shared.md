---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Určuje, že jeden nebo více deklarované programovací elementy jsou spojeny s třídu nebo strukturu ve velkém a ne s konkrétní instanci třídu nebo strukturu.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="when-to-use-shared"></a>Kdy použít sdílené  
 Sdílení členem třídu nebo strukturu je k dispozici pro všechny instance, místo *sdíleném*, kde každá instance zachová vlastní kopie. To je užitečné, například pokud hodnota proměnné platí v celé aplikaci. Pokud je deklarovat tuto proměnnou na `Shared`, pak všechny instance přístup k stejné umístění úložiště, a pokud se jedna instance se změní hodnota proměnné, všechny instance k aktualizované hodnoty.  
  
 Sdílení nezmění úroveň přístupu tohoto člena. Například je možné sdílet člena třídy a privátní (k dispozici pouze z v rámci třídy), nebo sdíleném a veřejné. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Shared` jenom na úrovni modulu. To znamená kontext deklarace `Shared` element musí být třídu nebo strukturu a nemůže být zdrojový soubor, obor názvů nebo postupu.  
  
-   **Kombinovaná parametrů.** Nelze zadat `Shared` společně s [přepsání](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), nebo [ Statické](../../../visual-basic/language-reference/modifiers/static.md) ve stejné deklaraci.  
  
-   **Přístup k.** Můžete zobrazit sdílené element kvalifikující ho s názvem třídu nebo strukturu, ne při název proměnné konkrétní instanci jeho třídu nebo strukturu. I nemáte k vytvoření instance třídu nebo strukturu pro přístup k jeho sdílení členové.  
  
     V následujícím příkladu volání sdílený postup <xref:System.Double.IsNaN%2A> vystavené <xref:System.Double> struktura.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Implicitní sdílení.** Nelze použít `Shared` modifikátor v [příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md), ale konstanty implicitně sdílejí. Podobně nelze deklarovat být členem skupiny modulu nebo rozhraní `Shared`, ale jsou implicitně sdílené.  
  
## <a name="behavior"></a>Chování  
  
-   **Úložiště.** Sdílené proměnné nebo událostí je uložené v paměti pouze po, bez ohledu na to, kolik nebo několik instancí vytvoření z jeho třídu nebo strukturu. Podobně sdílený postup nebo vlastnost obsahuje pouze jednu sadu lokální proměnné.  
  
-   **Přístup k prostřednictvím proměnnou Instance.** Je možné získat přístup k prvku sdílené s kvalifikující s názvem proměnné, která obsahuje konkrétní instanci jeho třídu nebo strukturu. I když tento postup obvykle funguje podle očekávání, kompilátor vygeneruje upozornění a umožňuje přístup pomocí názvu třídu nebo strukturu místo proměnnou.  
  
-   **Přístup k prostřednictvím výrazu Instance.** Pokud máte přístup k prvku sdílené prostřednictvím výraz, který vrací instanci třídy jeho třídu nebo strukturu, kompilátor umožňuje přístup pomocí názvu třídu nebo strukturu místo hodnocení výrazu. To poskytuje neočekávané výsledky, pokud má výraz, který se provádět další akce, jakož i vrací instanci. Toto dokládá následující příklad.  
  
    ```  
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
  
     V předchozím příkladu, kompilátor vygeneruje upozornění obou časy kód přistupuje k sdílené proměnné `total` prostřednictvím instance. V každém případě umožňuje přístup přímo prostřednictvím třídy `shareTotal` a zajistěte, aby nebyly používat všechny instance. V případě určený volání postup `returnClass`, to znamená i negeneruje volání `returnClass`, takže není provést další akce zobrazení "Funkce returnClass() názvem".  
  
 `Shared` Modifikátor lze použít v těchto kontexty:  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Stínů](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Statické](../../../visual-basic/language-reference/modifiers/static.md)  
 [Doba platnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
