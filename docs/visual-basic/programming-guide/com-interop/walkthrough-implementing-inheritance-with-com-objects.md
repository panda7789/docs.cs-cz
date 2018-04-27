---
title: 'Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b03b81c9e04e79f8ce7763ecf8a489d248ff480b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)
Odvozujete tříd jazyka Visual Basic z `Public` třídy v objekty modelu COM, včetně těch, které jsou vytvořené v dřívějších verzích jazyka Visual Basic. Vlastnosti a metody třídy dědí z objektů COM můžete přepsat nebo přetížený stejně jako vlastnosti a metody všechny základní třídy lze přepsat nebo přetížený. Dědičnost z objektů COM je užitečné, když máte existující knihovny tříd, které nechcete znovu zkompilovat.  
  
 Následující postup ukazuje, jak vytvořit objekt COM, která obsahuje třídu pomocí Visual Basic 6.0 a použít jej jako základní třída.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>K vytvoření objektu COM, která se používá v tomto návodu  
  
1.  V jazyce Visual Basic 6.0 otevřete nový projekt ActiveX knihovny DLL. Projekt s názvem `Project1` je vytvořena. Obsahuje třídy s názvem `Class1`.  
  
2.  V **Project Exploreru**, klikněte pravým tlačítkem na **Project1**a potom klikněte na **Project1 vlastnosti**. **Vlastnosti projektu** se zobrazí dialogové okno.  
  
3.  Na **Obecné** kartě **vlastnosti projektu** dialogové okno pole, změňte název projektu zadáním `ComObject1` v **název projektu** pole.  
  
4.  V **Project Exploreru**, klikněte pravým tlačítkem na `Class1`a potom klikněte na **vlastnosti**. **Vlastnosti** zobrazí se okno pro třídu.  
  
5.  Změna `Name` vlastnost `MathFunctions`.  
  
6.  V **Project Exploreru**, klikněte pravým tlačítkem na `MathFunctions`a potom klikněte na **kód zobrazení**. **Editor kódu** se zobrazí.  
  
7.  Přidejte místní proměnné pro uložení hodnota vlastnosti:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Přidat vlastnost `Let` a vlastnost `Get` procedury vlastností:  
  
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
  
10. Vytvořit a registrovat objekt COM kliknutím **zkontrolujte ComObject1.dll** na **souboru** nabídky.  
  
    > [!NOTE]
    >  I když můžete také zveřejnit třídu vytvořit pomocí jazyka Visual Basic jako objekt COM, není objekt true COM a nelze použít v tomto návodu. Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Sestavení spolupráce  
 V následujícím postupu vytvoříte spolupráce sestavení, která funguje jako most mezi nespravovaného kódu (například objekt COM) a spravovaný kód, který se používá v sadě Visual Studio. Sestavení vzájemné spolupráce, který vytváří jazyka Visual Basic zpracovává mnoho podrobnosti o práci s objekty modelu COM, jako například *zařazování spolupráce*, proces balení parametry a návratové hodnoty do ekvivalentní datové typy jako se přesouvají do a z COM – objekty. Referenční dokumentace jazyka Visual Basic aplikace odkazuje na sestavení vzájemné spolupráce, nikoli skutečné objektu COM.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Chcete-li objekt modelu COM pomocí jazyka Visual Basic 2005 a novějších verzích  
  
1.  Otevřete nový projekt aplikace Windows Visual Basic.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.  
  
     **Přidat odkaz na** se zobrazí dialogové okno.  
  
3.  Na **COM** kartě, dvakrát klikněte na `ComObject1` v **název komponenty** seznamu a klikněte na tlačítko **OK**.  
  
4.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
     **Přidat novou položku** se zobrazí dialogové okno.  
  
5.  V **šablony** podokně klikněte na tlačítko **třída**.  
  
     Výchozí název souboru, `Class1.vb`, zobrazí se v **název** pole. Změňte toto pole na MathClass.vb a klikněte na tlačítko **přidat**. Tím se vytvoří třídu s názvem `MathClass`a zobrazí jeho kód.  
  
6.  Přidejte následující kód do horní části `MathClass` dědění ze třídy COM.  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  Přetížení veřejná metoda základní třídy přidáním následující kód do `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  Zděděné třídy rozšířit přidáním následující kód do `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 Nové třídy dědí vlastnosti základní třídy v objektu COM, přetížení metody a definuje nové metody rozšíření třídy.  
  
#### <a name="to-test-the-inherited-class"></a>K testování zděděné třídy  
  
1.  Přidání tlačítka do svého formuláře spuštění a potom dvojím kliknutím zobrazit jeho kód.  
  
2.  U tlačítka `Click` procedury Obslužná rutina události, přidejte následující kód k vytvoření instance `MathClass` a volání přetížené metody:  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  Stisknutím klávesy F5 spusťte projekt.  
  
 Po kliknutí na tlačítko ve formuláři `AddNumbers` metoda je nejdříve volána s `Short` datový typ čísla, a Visual Basic vybere odpovídající metodu ze základní třídy. Druhé volání `AddNumbers` se přesměruje na metodu přetížení z `MathClass`. Třetí volání volání `SubtractNumbers` metoda, která rozšiřuje třídu. Je nastavena v základní třídě a hodnota se zobrazí.  
  
## <a name="next-steps"></a>Další kroky  
 Jste si všimli, přetížené `AddNumbers` funkce zřejmě stejný datový typ. jako metodu zděděn ze základní třídy objektu COM. Je to proto argumentů a parametrů metody základní třídy jsou definovány jako 16bitové celá čísla v jazyce Visual Basic 6.0, ale jsou zveřejněné jako 16bitové celá čísla typu `Short` v novější verzi jazyka Visual Basic. Nové funkce přijímá 32bitová celá čísla a přetížení funkce základní třídy.  
  
 Při práci s objekty modelu COM, ujistěte se, abyste ověřili velikost a datové typy parametrů. Například při použití objektu COM, který přijímá objekt kolekce Visual Basic 6.0 jako argument, nemůžete zadat kolekci z novější verze sady Visual Basic.  
  
 Vlastnosti a metody, které dědí z třídy COM, lze přepsat, což znamená, můžou deklarovat místní vlastnosti nebo metody, která nahrazuje vlastnost nebo metoda zděděn ze základní třídy COM. Pravidla pro přepis zděděných vlastností COM jsou podobné pravidla pro přepis ostatní vlastnosti a metody s následujícími výjimkami:  
  
-   Pokud přepíšete všechny vlastnosti nebo metody dědí z třídy COM, je nutné přepsat všechny ostatní zděděné vlastnosti a metody.  
  
-   Vlastnosti, které používají `ByRef` parametry nelze přepsat.  
  
## <a name="see-also"></a>Viz také  
 [Interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
