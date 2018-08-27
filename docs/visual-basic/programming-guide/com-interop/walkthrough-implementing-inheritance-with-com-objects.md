---
title: 'Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: a1c1b7c247d3277c6614a4774395650c4c069c2f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929995"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)
Lze odvodit třídy jazyka Visual Basic z `Public` třídy v objektech COM, včetně těch, které jsou vytvořeny v dřívějších verzích jazyka Visual Basic. Vlastnosti a metody třídy dědí od objektů COM může přepsat nebo přetížené stejně jako vlastnosti a metody jiné základní třídy lze přepsat nebo přetížené. Dědičnost z objektů COM je užitečné, pokud máte existující knihovny tříd, které nechcete, aby se musela kompilovat.  
  
 Následující postup ukazuje, jak pomocí jazyka Visual Basic 6.0 můžete vytvořit objekt modelu COM, který obsahuje třídu a pak použít jako základní třídu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>K vytvoření objektu COM, který se používá v tomto názorném postupu  
  
1.  V jazyce Visual Basic 6.0 otevřete nový projekt knihovny DLL ActiveX. Projekt s názvem `Project1` se vytvoří. Obsahuje třídu s názvem `Class1`.  
  
2.  V **Project Exploreru**, klikněte pravým tlačítkem na **Project1**a potom klikněte na tlačítko **Project1 vlastnosti**. **Vlastnosti projektu** se zobrazí dialogové okno.  
  
3.  Na **Obecné** karty **vlastnosti projektu** dialogové okno pole, změňte název projektu tak, že zadáte `ComObject1` v **název projektu** pole.  
  
4.  V **Project Exploreru**, klikněte pravým tlačítkem na `Class1`a potom klikněte na tlačítko **vlastnosti**. **Vlastnosti** se zobrazí okno pro třídu.  
  
5.  Změnit `Name` vlastnost `MathFunctions`.  
  
6.  V **Project Exploreru**, klikněte pravým tlačítkem na `MathFunctions`a potom klikněte na tlačítko **zobrazit kód**. **Editor kódu** se zobrazí.  
  
7.  Přidáte místní proměnnou pro uchování hodnoty vlastnosti:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Přidat vlastnost `Let` a vlastnost `Get` procedury vlastnosti:  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. Přidání funkce:  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. Vytvoření a registrace objektu COM kliknutím **zkontrolujte ComObject1.dll** na **souboru** nabídky.  
  
    > [!NOTE]
    >  I když můžete také zveřejnit třídy vytvořené pomocí jazyka Visual Basic jako objekt modelu COM, není objekt modelu COM true a nelze použít v tomto názorném postupu. Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Sestavení vzájemné spolupráce  
 V následujícím postupu vytvoříte definiční sestavení, která funguje jako most mezi nespravovaný kód (například objekt modelu COM) a spravovaný kód, který používá Visual Studio. Sestavení vzájemné spolupráce, který vytvoří jazyka Visual Basic zpracovává řadu podrobnosti o práci s objekty COM, například *zařazování spolupráce*, proces balení parametry a návratové hodnoty do ekvivalentní datové typy při přechodu a od objektů COM. Odkaz v aplikaci Visual Basic odkazuje na sestavení vzájemné spolupráce, nikoli skutečný objekt modelu COM.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Objekt modelu COM pomocí jazyka Visual Basic 2005 a novějších verzích  
  
1.  Otevřete nový projekt aplikace Windows jazyka Visual Basic.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.  
  
     **Přidat odkaz** se zobrazí dialogové okno.  
  
3.  Na **COM** kartu, dvakrát klikněte na panel `ComObject1` v **název komponenty** seznamu a klikněte na tlačítko **OK**.  
  
4.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
     **Přidat novou položku** se zobrazí dialogové okno.  
  
5.  V **šablony** podokně klikněte na tlačítko **třídy**.  
  
     Výchozí název souboru `Class1.vb`, zobrazí se v **název** pole. Toto pole MathClass.vb a kliknutím na tlačítko Změnit **přidat**. Tím se vytvoří třídu s názvem `MathClass`a zobrazí jeho kód.  
  
6.  Přidejte následující kód k hornímu okraji `MathClass` dědit ze třídy modelu COM.  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  Přetížení veřejnou metodu základní třídy přidáním následujícího kódu `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  Zděděné třídy rozšířit přidáním následujícího kódu `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 Nová třída dědí vlastnosti ze základní třídy objektu COM, přetížení metody a definuje novou metodu rozšíření třídy.  
  
#### <a name="to-test-the-inherited-class"></a>Chcete-li testovat zděděné třídy  
  
1.  Přidání tlačítka do formuláře při spuštění a pak dvojím kliknutím ho zobrazte jeho kód.  
  
2.  Na tlačítku `Click` procedury Obslužná rutina události, přidejte následující kód k vytvoření instance `MathClass` a volání přetížené metody:  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  Stisknutím klávesy F5 spusťte projekt.  
  
 Když kliknete na tlačítko na formuláři `AddNumbers` metoda nejdříve volána s `Short` datového typu čísla, a Visual Basic zvolí vhodné metody ze základní třídy. Druhé volání `AddNumbers` směřuje na přetížení metody z `MathClass`. Třetí volání volání `SubtractNumbers` metodu, která rozšiřuje třídu. Nastavte vlastnost v základní třídě a hodnota se zobrazí.  
  
## <a name="next-steps"></a>Další kroky  
 Mohli jste si všimnout, který přetížené `AddNumbers` funkce zřejmě má stejný datový typ jako metody zděděné ze základní třídy objektu COM. Důvodem je, že argumentů a parametrů metody základní třídy jsou definovány jako 16bitová celá čísla v jazyce Visual Basic 6.0, ale jsou vystaveny jako 16bitová celá čísla typu `Short` v pozdějších verzích jazyka Visual Basic. Nové funkce přijímá 32bitová celá čísla a přetížení funkce základní třídy.  
  
 Při práci s objekty COM, ujistěte se, abyste ověřili velikost a datové typy parametrů. Například při použití objektu COM, který přijímá objekt kolekce jazyka Visual Basic 6.0 jako argument, nelze zadat kolekci z novější verze sady Visual Basic.  
  
 Vlastností a metod zděděných z tříd modelu COM, lze přepsat, což znamená, že je možné deklarovat lokální vlastnost nebo metoda, která se nahradí vlastnost nebo metoda zděděné ze základní třídy modelu COM. Pravidla pro přepsání zděděné vlastnosti modelu COM jsou podobné pravidlům pro přepsání další vlastnosti a metody s následujícími výjimkami:  
  
-   Pokud přepíšete všechny vlastnosti nebo metody, které dědí z třídy modelu COM, je nutné přepsat všechny ostatní zděděné vlastnosti a metody.  
  
-   Vlastnosti, které používají `ByRef` parametry nelze přepsat.  
  
## <a name="see-also"></a>Viz také  
 [Interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
