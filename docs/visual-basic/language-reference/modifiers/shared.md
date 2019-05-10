---
title: Shared (Visual Basic)
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
ms.openlocfilehash: fd43ef7cb5c16995fff87a65fc0f0974d8f4a47d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647707"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přidružená k třídě nebo struktuře ve velkém a ne s konkrétní instanci dané třídy nebo struktury.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="when-to-use-shared"></a>Kdy použít sdílené  
 Sdílení členem třídy nebo struktury je k dispozici pro každou instanci spíše než *nesdílené*, kde každá instance udržuje svůj vlastní kopie. To je užitečné, například, pokud hodnota proměnné se vztahuje na celé aplikace. Pokud deklarujete tuto proměnnou deklarovanou `Shared`, pak všechny instance přístup ke stejné umístění úložiště, a pokud jedna instance se změní hodnota proměnné, přístup všechny instance aktualizovanou hodnotu.  
  
 Sdílení nezmění úroveň přístupu členu. Například je možné sdílet člena třídy a privátní (přístupný pouze uvnitř třídy), nebo nesdílené a public. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>pravidla  
  
- **Místní deklarace.** Můžete použít `Shared` pouze na úrovni modulu. To znamená, že deklarace kontext `Shared` elementu musí být třídou nebo strukturou a nemůže být zdrojový soubor, obor názvů nebo proceduru.  
  
- **Kombinované modifikátory.** Nelze zadat `Shared` spolu s [přepíše](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), nebo [ Statické](../../../visual-basic/language-reference/modifiers/static.md) ve stejné deklaraci.  
  
- **Přístup k.** Přístup sdíleného element ho kvalifikaci pomocí názvu třídy nebo struktury, nikoli název proměnné o konkrétní instanci její třídy nebo struktury. Ještě nemáte k vytvoření instance třídy nebo struktury pro přístup k její sdílené členy.  
  
     Následující příklad volá sdílený postup <xref:System.Double.IsNaN%2A> vystavené <xref:System.Double> struktury.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Implicitní sdílení.** Nelze použít `Shared` modifikátor v [Const příkaz](../../../visual-basic/language-reference/statements/const-statement.md), ale konstanty jsou implicitně sdílené. Podobně nelze deklarovat člen modul nebo rozhraní být `Shared`, ale jsou implicitně sdílené.  
  
## <a name="behavior"></a>Chování  
  
- **Úložiště.** Sdílené proměnné nebo událostí je uložen v paměti pouze jednou, bez ohledu na to, kolik nebo několik instancí vytvořit jeho třídy nebo struktury. Podobně sdílený postup nebo vlastnost obsahuje pouze jednu sadu lokální proměnné.  
  
- **Přístup k prostřednictvím proměnné Instance.** Je možné pro přístup k prvku sdílené kvalifikaci s názvem proměnné, která obsahuje konkrétní instanci její třídy nebo struktury. I když to obvykle funguje podle očekávání, kompilátor vygeneruje upozornění a zajišťuje tak přístup prostřednictvím názvu třídy nebo struktury namísto proměnné.  
  
- **Přístup prostřednictvím výrazu Instance.** Pokud element sdílené přistupujete prostřednictvím výraz, který vrací instanci její třídy nebo struktury, kompilátor provede přístup pomocí názvu třídy nebo struktury místo vyhodnocení výrazu. Pokud jste zamýšleli výraz, který má provádět další akce, jakož i vrací instanci výsledkem neočekávané výsledky. Toto dokládá následující příklad.  
  
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
  
     V předchozím příkladu, kompilátor vygeneruje upozornění obou časů kód přistupuje ke sdílené proměnné `total` prostřednictvím instance. V každém případě je přístup přímo prostřednictvím třídy `shareTotal` a neprovede použít jakékoli instance. V případě zamýšlený volání do procedury `returnClass`, to znamená, že i negeneruje volání `returnClass`, takže není provádět další akce zobrazení "Volá funkci returnClass()".  
  
 `Shared` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Doba platnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
