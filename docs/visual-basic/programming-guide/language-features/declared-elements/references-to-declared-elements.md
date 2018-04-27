---
title: Odkazy na deklarované elementy (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 86d25d42688cffbf4076c4fb42eccc3b917d1dc1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="references-to-declared-elements-visual-basic"></a>Odkazy na deklarované elementy (Visual Basic)
Pokud váš kód odkazoval element deklarované, Visual Basic – kompilátor odpovídá názvu ve vašem odkaz na odpovídající deklarace s tímto názvem. Když se stejným názvem je deklarován více než jeden element, můžete řídit, která z těchto elementů má odkazovat *opravňující* její název.  
  
 Kompilátor se pokusí o porovnání název odkaz na název deklarace s *zpomalit*. To znamená, že začne s kódem odkazu a funguje i přes následných úrovně obsahující elementy.  
  
 Následující příklad ukazuje, odkazy na dvě proměnné se stejným názvem. V příkladu deklaruje dvě proměnné, každý s názvem `totalCount`, na různých úrovních oboru v modulu `container`. Při procesu `showCount` zobrazí `totalCount` bez kvalifikace, Visual Basic – kompilátor přeloží odkaz na prohlášení s zpomalit, a to místní deklarace uvnitř `showCount`. Po vyfiltrování `totalCount` s modulem obsahující `container`, kompilátor vyřeší odkaz na prohlášení k širší oboru.  
  
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
  
## <a name="qualifying-an-element-name"></a>Kvalifikující název elementu  
 Pokud chcete přepsat tento proces vyhledávání a zadejte název deklarované v širší oboru, je nutné *kvalifikaci* názvu s obsahující element širší oboru. V některých případech budete také muset kvalifikaci obsahující element.  
  
 Určení názvu způsob předcházející v příkazu zdroje s informacemi, které určuje, kde je definován cílový element. Tyto informace se nazývá *kvalifikace řetězec*. Může obsahovat jednu nebo více obory názvů a modul, třídy a struktury.  
  
 Řetězec kvalifikace musí jednoznačně určovat modulu, třídu nebo strukturu obsahující cílový element. Kontejner může zase nacházet v jiné obsahující elementu, obvykle obor názvů. Možná budete muset zahrnout několik obsahující prvky kvalifikace řetězce.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Pro přístup k deklarovaný element podle určení jeho názvu  
  
1.  Určete umístění, ve kterém byla definována elementu. To může zahrnovat obor názvů nebo i hierarchie oborů názvů. V rámci oboru názvů nejnižší úroveň element musí být součástí modulu, třídu nebo strukturu.  
  
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
  
2.  Určete cestu kvalifikace podle umístění cílového elementu. Začněte s nejvyšší obor názvů, pokračovat na nejnižší úrovni obor názvů a končit modulu, třídu nebo strukturu obsahující cílový element. Každý prvek v cestě musí obsahovat elementu, který následuje.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  Připravte cílový element kvalifikace řetězec. Umístěte období (`.`) po každý element v cestě. Aplikace musí mít přístup k každý element ve vašem kvalifikace řetězci.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  Zápis výraz nebo příkaz přiřazení odkazující na cílový element běžným způsobem.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  Zadejte před název cílový element kvalifikace řetězec. Název by měl splňovat okamžitě období (`.`) modulu, třídu nebo strukturu, která obsahuje element, který následuje.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  Kompilátor používá k nalezení deklaraci jasné, jednoznačným, ke kterému může porovnat odkaz na element target kvalifikace řetězec.  
  
 Také může mít pro kvalifikaci odkaz na název, pokud má aplikace přístup k více než jeden programovací element, který má stejný název. Například <xref:System.Windows.Forms> a <xref:System.Web.UI.WebControls> obory názvů obě obsahují `Label` – třída (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Pokud vaše aplikace používá oba, nebo pokud definuje vlastní `Label` třídu, musí rozlišovat různými `Label` objekty. Alias oboru názvů nebo import zahrňte do deklarace proměnné. Následující příklad používá alias importu.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Členové další obsahující elementy  
 Pokud používáte sdíleném členem jiné třídu nebo strukturu, musíte nejprve před název člena s proměnnou nebo výraz, který odkazuje na instanci třídu nebo strukturu. V následujícím příkladu `demoClass` je instance třídy s názvem `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Samotný název třídy nelze použít k vyfiltrování člena, který není [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md). Je nutné nejprve vytvořit instanci v proměnné objektu (v tomto případě `demoClass`) a pak na ni odkazujte podle názvu proměnné.  
  
 Pokud má třídu nebo strukturu `Shared` člen kvalifikovat tento člen s názvem třídu nebo strukturu, nebo proměnnou nebo výraz, který odkazuje na instanci.  
  
 Modul nemá žádné samostatné instance, a všichni její členové jsou `Shared` ve výchozím nastavení. Proto kvalifikaci modulu člen s názvem modulu.  
  
 Následující příklad ukazuje kvalifikované odkazy na postupy člen modulu. V příkladu deklaruje dvě `Sub` postupy, jak s názvem `perform`, v různých modulů v projektu. Každé z nich lze zadat bez kvalifikace v jeho vlastní modul ale musí být kvalifikovaný, pokud na něj odkazovat z někde jinde. Protože konečné odkaz v `module3` není způsobilá `perform`, kompilátor nelze přeložit tento odkaz.  
  
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
 Použít [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) elementy definovaný v jiném projektu, musíte nejprve nastavit *odkaz* do knihovny typ nebo sestavení tohoto projektu. Chcete-li nastavit odkaz, klikněte na tlačítko **přidat odkaz na** na **projektu** nabídky, nebo použijte [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru příkazového řádku.  
  
 Například můžete použít model objektu XML [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Pokud nastavíte na odkaz <xref:System.Xml> obor názvů, můžete deklarovat a použít některou z jejích tříd, jako třeba <xref:System.Xml.XmlDocument>. Následující příklad používá <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Import obsahující elementy  
 Můžete použít [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k *importovat* obory názvů, které obsahují moduly nebo třídy, které chcete použít. To umožňuje odkazovat na elementy definované v importovaných oboru názvů bez plně kvalifikovaného jejich názvy. Následující příklad přepíše předchozí příklad k importu <xref:System.Xml> oboru názvů.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Kromě toho `Imports` můžete definovat příkaz *importovat alias* pro jednotlivé importované obory názvů. To můžete provést ve zdrojovém kódu kratší a snadněji číst. Následující příklad přepíše předchozí příklad použití `xD` jako alias <xref:System.Xml> oboru názvů.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports` Příkaz zpřístupnění elementů od jiné projekty do vaší aplikace. Nevyžaduje tedy místní nastavení odkaz. Import oboru názvů právě eliminuje požadavek na kvalifikaci názvy definované v daném oboru názvů.  
  
 Můžete také `Imports` příkaz k importu modulů, tříd, struktur a výčty. Potom můžete členy z těchto prvků importované bez kvalifikace. Však musí vždy kvalifikaci sdíleném členy třídy a struktury s proměnnou nebo výraz, který se vyhodnotí na instanci třídu nebo strukturu.  
  
## <a name="naming-guidelines"></a>Pokyny pro pojmenování  
 Když definujete dvou nebo více elementům programování, které mají stejný název, *název nejednoznačnosti* může dojít při kompilátor pokusí přeložit odkaz na tento název. Pokud se více než jednu definici nachází v oboru, nebo pokud žádné definice není v oboru, odkaz je irresolvable. Příklad naleznete v části "Kvalifikovaný odkaz na příklad" na této stránce nápovědy.  
  
 Mnohoznačnosti názvů se můžete vyhnout tím, že všechny elementy jedinečné názvy. Pak můžete nastavit odkaz na libovolný element, aniž by museli kvalifikaci stejný název jako obor názvů, modulu nebo třída. Můžete také sníží pravděpodobnost omylem odkazující na chybný element.  
  
## <a name="shadowing"></a>Stínový provoz  
 Když dva programovací elementy sdílet stejný název, jednu z nich můžete skrýt, nebo *stínové*, jiný. Element stíněné není k dispozici pro referenci; Místo toho že pokud váš kód používá název stíněné elementu, Visual Basic – kompilátor ho přeloží na stínového provozu elementu. Podrobnější vysvětlení s příklady najdete v tématu [stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Viz také  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)
