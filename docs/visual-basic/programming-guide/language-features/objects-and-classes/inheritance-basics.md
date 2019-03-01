---
title: Základní informace o dědičnosti (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 3d772fb81eb13b9454f44ff8ae4256bdb4144caa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970295"
---
# <a name="inheritance-basics-visual-basic"></a>Základní informace o dědičnosti (Visual Basic)
`Inherits` Prohlášení se používá k deklaraci nové třídy, nazvané *odvozené třídy*založená na stávající třídě, označované jako *základní třída*. Odvozené třídy dědit a můžete rozšířit, vlastnosti, metody, události, polí a konstanty definované v základní třídě. Následující část popisuje některé z pravidel pro dědičnost a modifikátory, které vám umožní změnit způsob, jak třídy dědit nebo jsou zděděny:  
  
-   Ve výchozím nastavení, všechny třídy lze dědit, pokud označené `NotInheritable` – klíčové slovo. Třídy mohou dědit z jiné třídy v projektu nebo z třídy v jiných sestavení, na které odkazuje váš projekt.  
  
-   Na rozdíl od jazyky, které umožňují vícenásobná dědičnost Visual Basic umožňuje pouze jedna dědičnost tříd; To znamená, že odvozené třídy mohou mít pouze jednu základní třídu. I když vícenásobná dědičnost není povolený ve třídách, třídy můžou implementovat více rozhraní, které můžete efektivně provádět stejné elementy end.  
  
-   Pokud chcete zabránit zveřejnění položky s omezeným přístupem v základní třídě, musí být typ přístupu odvozené třídy rovná nebo je více omezující než její základní třídě. Například `Public` třída nemůže dědit `Friend` nebo `Private` třídy a `Friend` třída nemůže dědit `Private` třídy.  
  
## <a name="inheritance-modifiers"></a>Modifikátory dědičnosti  
 Visual Basic představuje následující příkazy na úrovni třídy a modifikátory pro podporu dědičnosti:  
  
-   `Inherits` příkaz – určuje základní třídu.  
  
-   `NotInheritable` Modifikátor – zbavuje programátory horizontálních oddílů pomocí třídy jako základní třídu.  
  
-   `MustInherit` Modifikátor – Určuje, že třída je určena pro použití jako základní třídu. Instance `MustInherit` třídy nelze vytvořit přímo, mohou být vytvořeny pouze jako základní třída instance odvozené třídy. (Jiných programovacích jazycích, jako je například C++ a C#, použijte termín *abstraktní třídu* k popisu takové třídy.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Přepsání vlastností a metod v odvozených třídách  
 Ve výchozím nastavení dědí odvozená třída vlastnosti a metody ze své základní třídy. Pokud zděděnou vlastnost nebo metoda mají chovat jinak než v odvozené třídě může být *přepsat*. To znamená můžete definovat novou implementaci metody v odvozené třídě. Následující modifikátory umožňují určit, jak přepsat vlastnosti a metody:  
  
-   `Overridable` – Povoluje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.  
  
-   `Overrides` – Přepíše `Overridable` vlastnosti nebo metody definované v základní třídě.  
  
-   `NotOverridable` – Brání vlastnosti nebo metody v přepsání v dědičné třídě. Ve výchozím nastavení `Public` metody jsou `NotOverridable`.  
  
-   `MustOverride` – Vyžaduje, aby odvozená třída přepsat vlastnosti nebo metody. Když `MustOverride` klíčové slovo se používá, se skládá z definice metody jenom `Sub`, `Function`, nebo `Property` příkaz. Jsou povoleny žádné jiné příkazy a konkrétně neexistuje žádné `End Sub` nebo `End Function` příkazu. `MustOverride` metody musí být deklarována v `MustInherit` třídy.  
  
 Předpokládejme, že chcete definovat třídy pro zpracování mezd. Můžete například definovat obecnou `Payroll` třídu, která obsahuje `RunPayroll` metodu, která vypočítá mezd typické týden. Můžete pak použít `Payroll` jako základní třída pro více specializované `BonusPayroll` třídy, který může být použit při distribuci bonusy zaměstnance.  
  
 `BonusPayroll` Třída může dědit a přepsat, `PayEmployee` metodu definovanou v základní třídě `Payroll` třídy.  
  
 Následující příklad definuje základní třídu, `Payroll,` a odvozené třídy `BonusPayroll`, která přepíše metodu zděděné `PayEmployee`. Proceduře `RunPayroll`, vytvoří a pak předá `Payroll` objektu a `BonusPayroll` objekt funkce, `Pay`, který se spustí `PayEmployee` metoda oba objekty.  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a>MyBase – klíčové slovo  
 `MyBase` – Klíčové slovo se chová jako proměnné objektu, který odkazuje na základní třídu aktuální instance třídy. `MyBase` často se používá pro přístup ke členům základní třídy, přepsat nebo Stínovaný v odvozené třídě. Zejména `MyBase.New` se používá explicitně volat konstruktor základní třídy v konstruktoru odvozené třídy.  
  
 Předpokládejme například, že při návrhu odvozenou třídu, která přepíše metodu zděděné ze základní třídy. Přepsané metody lze volat metodu v základní třídě a vrácenou hodnotu změnit, jak je znázorněno v následujícím fragmentu kódu:  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 Následující seznam popisuje omezení pro používání `MyBase`:  
  
-   `MyBase` odkazuje na přímé základní třídy a jejích zděděných členů. Nedá se použít pro přístup k `Private` členy třídy.  
  
-   `MyBase` je klíčové slovo, nikoli skutečný objekt. `MyBase` nelze přiřadit k proměnné, předány do procedury nebo použít v `Is` porovnání.  
  
-   Metoda, která `MyBase` kvalifikuje nemusí být definován v přímé základní třídy je místo toho mohou být definovány v nepřímo zděděné základní třídy. Aby odkaz kvalifikována `MyBase` pro správnou kompilaci některé základní třída musí obsahovat odpovídající název a typy parametrů, které se zobrazí při volání metody.  
  
-   Nemůžete použít `MyBase` volat `MustOverride` základní metody třídy.  
  
-   `MyBase` nelze použít k vyfiltrování samotný. Následující kód proto není platná:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` nelze použít v modulech.  
  
-   `MyBase` nelze použít pro přístup k členům základní třídy, které jsou označeny jako `Friend` Pokud základní třída je v jiném sestavení.  
  
 Další informace a další příklad naleznete v tématu [jak: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>MyClass – klíčové slovo  
 `MyClass` – Klíčové slovo se chová jako proměnné objektu, který odkazuje na aktuální instanci třídy, jak byly původně implementované. `MyClass` se podobá `Me`, ale každé metody a vlastnosti volat na `MyClass` je zacházeno, jako kdyby byly metody nebo vlastnosti [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Proto že metoda nebo vlastnost nemá vliv přepsání v odvozené třídě.  
  
-   `MyClass` je klíčové slovo, nikoli skutečný objekt. `MyClass` nelze přiřadit k proměnné, předány do procedury nebo použít v `Is` porovnání.  
  
-   `MyClass` odkazuje na třídu obsahující a jejích zděděných členů.  
  
-   `MyClass` lze použít jako kvalifikátory pro `Shared` členy.  
  
-   `MyClass` nelze použít uvnitř `Shared` metody, ale můžou se používat pro přístup ke sdílenému členu třídy uvnitř metody instance.  
  
-   `MyClass` nelze použít standardní moduly.  
  
-   `MyClass` lze použít k vyfiltrování metodu, která je definována v základní třídě a, který nemá žádnou implementaci metody, které jsou k dispozici v dané třídě. Takový odkaz má stejný význam jako `MyBase.` *metoda*.  
  
 Následující příklad porovnává `Me` a `MyClass`.  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 I když `derivedClass` přepíše `testMethod`, `MyClass` – klíčové slovo v `useMyClass` nichž účinky přepsání a odstraňuje kompilátoru volání základní třídy verzi `testMethod`.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
