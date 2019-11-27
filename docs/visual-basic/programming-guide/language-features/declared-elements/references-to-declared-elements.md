---
title: Odkazy na deklarované elementy
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: a6477a9f0abaf8eb9176f4f6ab2a920af6c8f500
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345305"
---
# <a name="references-to-declared-elements-visual-basic"></a>Odkazy na deklarované elementy (Visual Basic)
Když váš kód odkazuje na deklarovaný element, kompilátor Visual Basic odpovídá názvu ve vašem odkazu na příslušnou deklaraci daného názvu. Pokud je deklarován více než jeden prvek se stejným názvem, můžete určit, na které prvky mají být odkazovány, pomocí *zařazení* jeho názvu.  
  
 Kompilátor se pokusí vyhledat odkaz na název deklarace názvu s *nejužším oborem*. To znamená, že začíná kódem, který vytváří odkaz a pracuje směrem nahoru až po sobě jdoucí úrovně obsahující prvky.  
  
 Následující příklad ukazuje odkazy na dvě proměnné se stejným názvem. Příklad deklaruje dvě proměnné, každý s názvem `totalCount`v různých úrovních oboru v modulu `container`. Pokud procedura `showCount` zobrazí `totalCount` bez kvalifikace, kompilátor Visual Basic vyřeší odkaz na deklaraci s nejužším rozsahem, konkrétně místní deklarace v `showCount`. Pokud se `totalCount` s obsahem obsahujícím `container`, kompilátor vyřeší odkaz na deklaraci s širším rozsahem.  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>Kvalifikování názvu elementu  
 Pokud chcete tento proces hledání přepsat a zadat název deklarovaný v širším rozsahu, je nutné *kvalifikovat* název obsahující element širšího rozsahu. V některých případech může být také nutné kvalifikovat nadřazený element.  
  
 Kvalifikování názvu znamená před ním ve zdrojovém příkazu informace, které identifikují, kde je cílový element definován. Tyto informace se nazývají *kvalifikační řetězec*. Může zahrnovat jeden nebo více oborů názvů a modulu, třídy nebo struktury.  
  
 Řetězec kvalifikace by měl jednoznačně určovat modul, třídu nebo strukturu obsahující cílový element. Kontejner může být zase umístěný v jiném obsahujícím elementu, obvykle obor názvů. Je možné, že budete muset zahrnout několik obsahující prvky do řetězce kvalifikace.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Přístup k deklarovanému elementu pomocí kvalifikování jeho názvu  
  
1. Určete umístění, ve kterém byl prvek definován. To může zahrnovat obor názvů nebo dokonce i hierarchii oborů názvů. V rámci oboru názvů nejnižší úrovně musí být element obsažen v modulu, třídě nebo struktuře.  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. Určete cestu kvalifikace na základě umístění cílového elementu. Začněte s oborem názvů nejvyšší úrovně, přejděte k oboru názvů nejnižší úrovně a ukončete modul, třídu nebo strukturu obsahující cílový element. Každý prvek v cestě musí obsahovat element, který následuje za ním.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3. Připravte řetězec kvalifikace pro cílový element. Po každém elementu v cestě vložte tečku (`.`). Vaše aplikace musí mít přístup ke každému prvku v řetězci kvalifikace.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. Napište výraz nebo příkaz přiřazení odkazující na cílový element v normálním způsobu.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. Před název cílového elementu uveďte řetězec kvalifikace. Název by měl následovat po tečkě (`.`), která následuje za modulem, třídou nebo strukturou, která obsahuje element.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. Kompilátor používá řetězec kvalifikace k nalezení jasné, jednoznačné deklarace, ke které se může shodovat s odkazem na cílový element.  
  
 Může být také nutné kvalifikovat odkaz na název, pokud má aplikace přístup k více než jednomu programovacímu prvku, který má stejný název. Například obory názvů <xref:System.Windows.Forms> a <xref:System.Web.UI.WebControls> obsahují třídu `Label` (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Pokud vaše aplikace používá obojí nebo pokud definuje svou vlastní třídu `Label`, je nutné odlišit různé objekty `Label`. V deklaraci proměnné zahrňte obor názvů nebo alias importu. V následujícím příkladu je použit alias importu.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Členové ostatních obsahující prvky  
 Použijete-li nesdíleného člena jiné třídy nebo struktury, musíte nejprve kvalifikovat název člena pomocí proměnné nebo výrazu, který odkazuje na instanci třídy nebo struktury. V následujícím příkladu je `demoClass` instance třídy s názvem `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Samotný název třídy nelze použít k získání člena, který není [sdílen](../../../../visual-basic/language-reference/modifiers/shared.md). Musíte nejdřív vytvořit instanci v objektové proměnné (v tomto případě `demoClass`) a pak na ni odkazovat pomocí názvu proměnné.  
  
 Pokud třída nebo struktura má `Shared` člen, můžete kvalifikovat tento člen buď s názvem třídy nebo struktury, nebo s proměnnou nebo výrazem, který odkazuje na instanci.  
  
 Modul nemá žádné samostatné instance a všechny jeho členy jsou ve výchozím nastavení `Shared`. Proto jste kvalifikováni člena modulu s názvem modulu.  
  
 Následující příklad ukazuje kvalifikované odkazy na členské procedury modulu. Příklad deklaruje dva `Sub` postupy, s názvem `perform`, v různých modulech v projektu. Každý z nich je možné zadat bez kvalifikace v rámci vlastního modulu, ale musí být kvalifikován, pokud je odkazován z libovolného místa jinde. Vzhledem k tomu, že poslední odkaz v `module3` nesplňuje `perform`, kompilátor nemůže tento odkaz vyřešit.  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>Odkazy na projekty  
 Chcete-li použít [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) prvky definované v jiném projektu, je nutné nejprve nastavit *odkaz* na sestavení projektu nebo knihovnu typů. Chcete-li nastavit odkaz, klikněte na tlačítko **Přidat odkaz** v nabídce **projekt** nebo použijte možnost kompilátoru [-Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) příkazového řádku.  
  
 Například můžete použít objektový model XML .NET Framework. Pokud nastavíte odkaz na obor názvů <xref:System.Xml>, můžete deklarovat a použít kteroukoli z jeho tříd, jako je například <xref:System.Xml.XmlDocument>. Následující příklad používá <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Import obsahující prvky  
 Můžete použít [příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k *importu* oborů názvů, které obsahují moduly nebo třídy, které chcete použít. Díky tomu můžete odkazovat na prvky definované v importovaném oboru názvů, aniž byste museli plně kvalifikovat jejich názvy. Následující příklad přepíše předchozí příklad pro import <xref:System.Xml> obor názvů.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Kromě toho příkaz `Imports` může definovat *alias importu* pro každý importovaný obor názvů. To může mít za krátkou a snazší čtení zdrojového kódu. Následující příklad přepíše předchozí příklad pro použití `xD` jako alias pro obor názvů <xref:System.Xml>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 Příkaz `Imports` nezpřístupňuje prvky z jiných projektů, které jsou k dispozici pro vaši aplikaci. To znamená, že nevezme místo nastavení odkaz. Import oboru názvů pouhým odebráním požadavku vyřadíte názvy definované v daném oboru názvů.  
  
 Pomocí příkazu `Imports` lze také importovat moduly, třídy, struktury a výčty. Pak můžete použít členy takových importovaných prvků bez kvalifikace. Je však nutné vždy kvalifikovat nesdílené členy tříd a struktur s proměnnou nebo výrazem, který je vyhodnocen jako instance třídy nebo struktury.  
  
## <a name="naming-guidelines"></a>Pokyny k pojmenování  
 Pokud definujete dva nebo více programovacích prvků, které mají stejný název, může dojít k *nejednoznačnosti názvu* , pokud se kompilátor pokusí přeložit odkaz na tento název. Pokud je v oboru více než jedna definice nebo pokud není v oboru žádná definice, je odkaz nevyřešitelná. Příklad naleznete v části "kvalifikovaný referenční příklad" na této stránce s nápovědu.  
  
 Nejednoznačnosti názvů můžete zabránit tím, že všem vašim prvkům udělíte jedinečné názvy. Pak můžete vytvořit odkaz na libovolný prvek bez nutnosti kvalifikovat jeho název pomocí oboru názvů, modulu nebo třídy. Také snížíte pravděpodobnost nechtěného odkazování na nesprávný prvek.  
  
## <a name="shadowing"></a>Stínování  
 Pokud dva programovací prvky mají stejný název, jeden z nich může skrýt nebo *stín*, druhý. Stínovaný element není pro referenci k dispozici. místo toho, když kód používá stínovaný název elementu, kompilátor Visual Basic ho přeloží na stínový element. Podrobnější vysvětlení s příklady najdete v tématu [vytváření stínových kopií v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Viz také:

- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
