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
ms.openlocfilehash: 9225e5fd9fa35ae06414018a109f66515f99363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="inheritance-basics-visual-basic"></a>Základní informace o dědičnosti (Visual Basic)
`Inherits` Příkaz se používá k deklaraci novou třídu, s názvem *odvozené třídy*na stávající třídě, označuje jako základě *základní třída*. Odvozené třídy dědí a můžete rozšířit, vlastnosti, metody, události, pole a konstanty definované v základní třídě. Následující část popisuje některé z pravidel pro dědičnosti a modifikátory, které můžete změnit způsob třídy dědí nebo jsou děděné:  
  
-   Ve výchozím nastavení, všechny třídy lze dědit, pokud označené jako `NotInheritable` – klíčové slovo. Třídy lze dědit z jiné třídy v projektu nebo z třídy v ostatních sestavení, které váš projekt odkazuje.  
  
-   Na rozdíl od jazyky, které umožňují vícenásobná dědičnost Visual Basic, umožňuje pouze jedna dědičnost v třídách; odvozené třídy tedy může mít pouze jeden základní třídy. I když vícenásobná dědičnost není povolena v třídách, můžete implementovat třídy více rozhraní, které můžete efektivně provádět stejné elementy end.  
  
-   Pokud chcete zabránit vystavení s omezeným přístupem položky v základní třídě, musí být typ přístupu odvozené třídy rovna nebo více omezující než její základní třída. Například `Public` třída nemůže Zdědit `Friend` nebo `Private` třída a `Friend` třída nemůže Zdědit `Private` – třída.  
  
## <a name="inheritance-modifiers"></a>Modifikátory dědičnosti  
 Visual Basic představuje následující příkazy úrovni třídy a modifikátory pro podporu dědičnosti:  
  
-   `Inherits` příkaz – určuje základní třídy.  
  
-   `NotInheritable` Modifikátor – programátory bránit v použití třídy jako základní třída.  
  
-   `MustInherit` Modifikátor – Určuje, že třída je určena pro použití jako základní třída. Instance `MustInherit` třídy nelze vytvořit přímo; jejich lze vytvořit pouze jako základní instancí třídy odvozené třídy. (Jinými programovací jazyky, jako je například C++ a C#, použijte termín *abstraktní třída* k popisu taková třída.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Přepsání vlastností a metod v odvozených třídách  
 Ve výchozím nastavení odvozené třídy dědí vlastnosti a metody ze své základní třídy. Pokud zděděnou vlastnost nebo metoda obsahuje chovat jinak v odvozené třídě může být *přepsat*. To znamená můžete definovat nové implementace metody v odvozené třídě. Následující modifikátory je možné určit, jak jsou přepsaná vlastnosti a metody:  
  
-   `Overridable` – Umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.  
  
-   `Overrides` – Přepsání `Overridable` vlastnosti nebo metody definované v základní třídě.  
  
-   `NotOverridable` – Brání vlastnosti nebo metody přepsání dědičných třídy. Ve výchozím nastavení `Public` metody jsou `NotOverridable`.  
  
-   `MustOverride` – Vyžaduje, aby odvozené třídě přepsat vlastnosti nebo metody. Když `MustOverride` – klíčové slovo se používá, definici metody se skládá z jenom na `Sub`, `Function`, nebo `Property` příkaz. Jsou povoleny žádné jiné příkazy a konkrétně neexistuje žádné `End Sub` nebo `End Function` příkaz. `MustOverride` metody musí být deklarován v `MustInherit` třídy.  
  
 Předpokládejme, že chcete definovat pro zpracování mzdy třídy. Můžete třeba definovat obecný `Payroll` třídu, která obsahuje `RunPayroll` metoda, která by vypočítala mzdy typické týden. Poté můžete použít `Payroll` jako základní třída pro více specializované `BonusPayroll` třídy, který může být použit při distribuci bonusy zaměstnanců.  
  
 `BonusPayroll` Třída může dědit a přepsat, `PayEmployee` metoda definované v základní `Payroll` třídy.  
  
 V následujícím příkladu definuje základní třídu, `Payroll,` a odvozené třídy `BonusPayroll`, který přepíše metodu zděděné `PayEmployee`. A postup `RunPayroll`, vytvoří a pak předá `Payroll` objektu a `BonusPayroll` objekt, který má funkci, `Pay`, který provede `PayEmployee` metoda oba objekty.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase – klíčové slovo  
 `MyBase` – Klíčové slovo chová jako objektová proměnná, která odkazuje na základní třídu aktuální instance třídy. `MyBase` často se používá pro přístup k členy základní třídy, které jsou přepsat nebo Stínovaný v odvozené třídě. Konkrétně `MyBase.New` se používá k explicitně volání konstruktoru základní třídy z konstruktoru odvozené třídy.  
  
 Předpokládejme například, že navrhujete odvozené třídy, který přepíše metodu zděděn ze základní třídy. Přepsaná metoda můžete volat metodu v základní třídě a jak je znázorněno v následující fragment kódu upravit návratovou hodnotu:  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 Následující seznam popisuje omezení týkající se použití `MyBase`:  
  
-   `MyBase` odkazuje na přímé základní třídy a její zděděné členy. Nelze použít pro přístup k `Private` členy ve třídě.  
  
-   `MyBase` je klíčové slovo, nikoli skutečné objektu. `MyBase` nelze přiřazený k proměnné, předaný postupy nebo používány `Is` porovnání.  
  
-   Metoda, `MyBase` vyfiltrování nemá být definován ve třídě okamžitou základní; se místo toho mohou být definovány v nepřímo zděděné základní třídy. Aby odkaz kvalifikovaný `MyBase` pro správnou kompilaci některé základní třída musí obsahovat odpovídající název a typy parametrů, které se zobrazují v volání metody.  
  
-   Nemůžete použít `MyBase` volat `MustOverride` základní metody třídy.  
  
-   `MyBase` nelze použít k vyfiltrování sám sebe. Následující kód, proto není platný:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` nelze použít v modulech.  
  
-   `MyBase` nelze použít pro přístup k členy základní třídy, které jsou označeny jako `Friend` Pokud základní třída je v jiném sestavení.  
  
 Další informace a další příklad najdete v tématu [postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>MyClass – klíčové slovo  
 `MyClass` – Klíčové slovo chová jako objektová proměnná, která odkazuje na aktuální instanci třídy v původním implementována. `MyClass` podobá `Me`, ale každý metod a vlastností volání na `MyClass` je zpracováván jako by byly metody nebo vlastnosti [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Proto metody nebo vlastnosti nemá vliv přepsání v odvozené třídě.  
  
-   `MyClass` je klíčové slovo, nikoli skutečné objektu. `MyClass` nelze přiřazený k proměnné, předaný postupy nebo používány `Is` porovnání.  
  
-   `MyClass` odkazuje na třídu obsahující a jeho zděděné členy.  
  
-   `MyClass` lze použít jako kvalifikátory pro `Shared` členy.  
  
-   `MyClass` nelze použít uvnitř `Shared` metoda, ale dá se použít uvnitř metody instance přístup sdíleného člena třídy.  
  
-   `MyClass` nelze použít v standardní moduly.  
  
-   `MyClass` lze použít k vyfiltrování metoda, která je definovaná v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě. Takový odkaz má stejný význam jako `MyBase.` *metoda*.  
  
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
  
 I když `derivedClass` přepsání `testMethod`, `MyClass` – klíčové slovo v `useMyClass` nichž účinnost přepsání a překládá kompilátoru volání základní třída verzi `testMethod`.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
