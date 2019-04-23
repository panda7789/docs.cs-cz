---
title: Odkazy na deklarované elementy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 0fca02ab2dcb507c1129f18f31a25c7809fc9710
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296703"
---
# <a name="references-to-declared-elements-visual-basic"></a>Odkazy na deklarované elementy (Visual Basic)
Pokud váš kód odkazuje na element deklarovaný, kompilátor jazyka Visual Basic odpovídá názvu v referenci na příslušné prohlášení s tímto názvem. Pokud je teď deklarována více než jeden element se stejným názvem, můžete určit, které z těchto elementů je odkazovat *oprávněným* jeho název.  
  
 Kompilátor se pokusí porovnat název odkazu na deklarace názvu s *od nejužšího oboru po*. To znamená, že začne s kódem odkazu a funguje směrem ven. prostřednictvím po sobě jdoucích úrovně obsahující prvky.  
  
 Následující příklad ukazuje, odkazy na dvě proměnné se stejným názvem. Příklad deklaruje dvě proměnné, každý s názvem `totalCount`, na různých úrovních oboru v modulu `container`. Když postup `showCount` zobrazí `totalCount` bez kvalifikace, kompilátor jazyka Visual Basic přeloží odkaz na prohlášení s zpomalit, a to místní deklarace uvnitř `showCount`. Když kvalifikuje `totalCount` s modulem obsahující `container`, přeloží kompilátor odkaz na prohlášení s širším rozsahem.  
  
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
  
## <a name="qualifying-an-element-name"></a>Název elementu kvalifikace  
 Pokud chcete tento proces hledání a zadejte název deklarovaný v širším rozsahem je nutné *kvalifikovat* k názvu obsahující element širším rozsahem. V některých případech budete také muset kvalifikovat nadřazeného elementu.  
  
 Kvalifikováním názvu prostředky před ve vámi zdroje s informacemi, které určuje, kde je definován cílový element. Tyto informace se volá *kvalifikace řetězec*. Může obsahovat jednu nebo více oborů názvů a modulu, třídy nebo struktury.  
  
 Řetězec kvalifikace musí jednoznačně určovat modulu, třídy nebo struktury obsahující cílového prvku. Kontejner může zase nacházet v jiné nadřazeného elementu, obvykle obor názvů. Možná budete muset obsahují několik obsahující prvky v řetězci kvalifikace.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Pro přístup k element deklarovaný kvalifikováním názvu  
  
1. Určení umístění, ve kterém je definována elementu. To může zahrnovat obor názvů nebo dokonce hierarchie oborů názvů. V rámci oboru názvů nejnižší úrovně elementu musí být součástí modulu, třídy nebo struktury.  
  
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
  
2. Určení kvalifikace cestu na základě umístění cílového prvku. Začněte s nejvyšší úrovně oboru názvů, přejít k nejnižší úrovni oboru názvů a končit modulu, třídy nebo struktury obsahující cílového prvku. Každý prvek v cestě musí obsahovat element, která ji následuje.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3. Řetězec kvalifikace Příprava cílového prvku. Umístit tečku (`.`) po každý prvek v cestě. Aplikace musí mít přístup na každý prvek v řetězci vaše kvalifikace.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. Zápis výrazu nebo příkazu přiřazení odkazující na cílový element běžným způsobem.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. Zadejte před název elementu target řetězcem kvalifikace. Název by měl bezprostředně následuje po období (`.`) modulu, třídy nebo struktury, který obsahuje element, který následuje.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. Kompilátor používá k nalezení jednoznačnou, kompletní vymazat deklarace, na který může porovnat odkaz na element target řetězec kvalifikace.  
  
 Budete také muset kvalifikovat název odkazu, pokud má vaše aplikace přístup k více než jeden programový element, který má stejný název. Například <xref:System.Windows.Forms> a <xref:System.Web.UI.WebControls> obory názvů oba obsahují `Label` třídy (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Pokud vaše aplikace používá obě nebo pokud jej definuje vlastní `Label` třídy, musí rozlišovat mezi různými `Label` objekty. Alias oboru názvů nebo import zahrňte v deklaraci proměnné. Alias importu v následujícím příkladu.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Další prvky obsahující členy  
 Při použití nesdílené členem jiné třídy nebo struktury, musí nejdřív kvalifikovat název člena proměnné nebo výraz, který odkazuje na instanci třídy nebo struktury. V následujícím příkladu `demoClass` je instance třídy s názvem `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Samotný název třídy nelze použít k vyfiltrování člena, který není [Shared](../../../../visual-basic/language-reference/modifiers/shared.md). Musíte nejprve vytvořit instanci v proměnné objektu (v tomto případě `demoClass`) a pak na něj odkazovat podle názvu proměnné.  
  
 Pokud má třída nebo struktura `Shared` člen, se můžete kvalifikovat tento člen s názvem třídy nebo struktury nebo proměnné nebo výraz, který odkazuje na instanci.  
  
 Modul nemá žádné samostatných instancí služby, a všechny její členy jsou `Shared` ve výchozím nastavení. Proto kvalifikovat člen modul s názvem modulu.  
  
 Následující příklad ukazuje kvalifikované odkazy na postupy člen modulu. Příklad deklaruje dvě `Sub` postupy, oba s názvem `perform`, v různých modulů v projektu. Každý z nich mohou být zadány bez kvalifikace v rámci své vlastní modul však musí být kvalifikovaný, pokud na něj odkazovat z jakéhokoliv jiného místa. Vzhledem k tomu, že poslední odkaz v `module3` nesplňuje `perform`, kompilátor nemůže vyřešit tento odkaz.  
  
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
 Použití [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) prvky definované v jiném projektu, musíte nejprve nastavit *odkaz* pro tento projekt sestavení nebo typ knihovny. Nastavit odkaz, klikněte na tlačítko **přidat odkaz** na **projektu** nabídky, nebo použijte [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru příkazového řádku.  
  
 Například můžete použít objektový model XML [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Pokud nastavíte na odkaz <xref:System.Xml> obor názvů, můžete deklarovat a použít některou z jeho třídy, jako například <xref:System.Xml.XmlDocument>. Následující příklad používá <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Import, který obsahuje prvky  
 Můžete použít [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k *importovat* obory názvů, které obsahují moduly nebo třídy, které chcete použít. To umožňuje odkazovat na prvky definované v importované oboru názvů bez plně kvalifikovaného jejich názvy. Následující příklad přepíše předchozí příklad import <xref:System.Xml> oboru názvů.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Kromě toho `Imports` příkazu můžete definovat *importovat alias* pro jednotlivé importované obory názvů. Díky tomu se zdrojový kód kratší a snadněji čitelné. Následující příklad přepíše předchozí příklad použití `xD` jako alias pro <xref:System.Xml> oboru názvů.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports` Příkaz neprovede elementy z jiných projektů k dispozici pro vaši aplikaci. To znamená ho nepřijímá místo nastavení odkaz. Import oboru názvů jenom eliminuje nutnost kvalifikovat názvy definované v tomto oboru názvů.  
  
 Můžete také použít `Imports` smlouvu pro import modulů, třídy, struktury a výčty. Potom můžete členy z těchto prvků importované bez kvalifikace. Musíte však vždy kvalifikovat nesdílené členy třídy a struktury s proměnné nebo výraz, který na instance dané třídy nebo struktury.  
  
## <a name="naming-guidelines"></a>Pokyny k pojmenování  
 Při definování nejmíň dva programovací prvky, které mají stejný název, *název nejednoznačnost* může dojít, pokud se kompilátor pokusí přeložit odkaz na tento název. Pokud více než jednu definici je v oboru nebo pokud se žádná definice není v oboru, odkaz je nevyřešitelná. Příklad naleznete v části "Příklad kvalifikovaný odkaz" na tuto stránku nápovědy.  
  
 Mnohoznačnosti názvů můžete vyhnout tím, že všechny prvky jedinečné názvy. Potom můžete vytvořit odkaz na libovolný element bez nutnosti kvalifikovat stejný název jako obor názvů, modulu nebo třídy. Také snížit riziko omylem odkazující na chybný element.  
  
## <a name="shadowing"></a>Stínování  
 Když dva programovací prvky sdílí se stejným názvem, jeden z nich můžete skrýt, nebo *stínové*, druhou. Stínovaný prvek není k dispozici pro referenci; Místo toho pokud váš kód používá název stínovaný elementu, kompilátor jazyka Visual Basic to je řešeno do elementu stínového provozu. Podrobnější vysvětlení s příklady najdete v tématu [stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Viz také:

- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
