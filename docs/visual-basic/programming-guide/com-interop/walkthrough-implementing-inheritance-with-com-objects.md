---
title: 'Návod: Implementace dědičnosti pomocí objektů COM'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: bdb891e1a150f0d7b79aefcc3db1f18dc8e84be4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396724"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)

Třídy Visual Basic můžete odvodit ze `Public` tříd v objektech com, a to i těch, které byly vytvořeny v dřívějších verzích Visual Basic. Vlastnosti a metody tříd zděděných z objektů COM mohou být přepsány nebo přetíženy stejně jako vlastnosti a metody jakékoli jiné základní třídy mohou být přepsány nebo přetíženy. Dědičnost z objektů modelu COM je užitečná v případě, že máte existující knihovnu tříd, kterou nechcete znovu kompilovat.

Následující postup ukazuje, jak použít Visual Basic 6,0 k vytvoření objektu modelu COM, který obsahuje třídu, a jeho následné použití jako základní třídy.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Vytvoření objektu COM, který je použit v tomto návodu

1. V Visual Basic 6,0 otevřete nový projekt knihovny DLL ActiveX. Vytvoří se projekt s názvem `Project1` . Obsahuje třídu s názvem `Class1` .

2. V **Průzkumníku projektu**klikněte pravým tlačítkem na **Project1**a pak klikněte na **vlastnosti Project1**. Zobrazí se dialogové okno **Vlastnosti projektu** .

3. Na kartě **Obecné** v dialogovém okně **Vlastnosti projektu** změňte název projektu zadáním `ComObject1` do pole **název projektu** .

4. V **Průzkumníku projektu**klikněte pravým tlačítkem myši `Class1` a pak klikněte na **vlastnosti**. Zobrazí se okno **vlastnosti** třídy.

5. Změňte `Name` vlastnost na `MathFunctions` .

6. V **Průzkumníku projektu**klikněte pravým tlačítkem myši `MathFunctions` a pak klikněte na **Zobrazit kód**. Zobrazí se **Editor kódu** .

7. Přidejte místní proměnnou pro uchování hodnoty vlastnosti:

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. Přidat procedury vlastností vlastností `Let` a vlastností `Get` :

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. Přidejte funkci:

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. Vytvořte a zaregistrujte objekt COM kliknutím na příkaz **vytvořit ComObject1. dll** v nabídce **soubor** .

    > [!NOTE]
    > I když můžete vystavit třídu vytvořenou pomocí Visual Basic jako objekt modelu COM, nejedná se o skutečný objekt COM a nelze ji použít v tomto návodu. Podrobnosti najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](com-interoperability-in-net-framework-applications.md).

## <a name="interop-assemblies"></a>Definiční sestavení

V následujícím postupu vytvoříte definiční sestavení, které funguje jako most mezi nespravovaným kódem (například objektem COM) a spravovaným kódem, který používá Visual Studio. Definiční sestavení, které Visual Basic vytvoří, zpracovává mnoho podrobností o práci s objekty COM, jako je například *Interop Marshaling*, proces balení parametrů a návratové hodnoty do ekvivalentních datových typů při přesunu do a z objektů com. Odkaz v aplikaci Visual Basic odkazuje na definiční sestavení, nikoli na samotný objekt modelu COM.

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Použití objektu COM s Visual Basic 2005 a novějšími verzemi

1. Otevřete nový Visual Basic projekt aplikace systému Windows.

2. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

     Zobrazí se dialogové okno **Přidat odkaz** .

3. Na kartě **com** poklikejte na `ComObject1` seznam **název součásti** a klikněte na **OK**.

4. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku**.

5. V podokně **šablony** klikněte na **Třída**.

     Výchozí název souboru se `Class1.vb` zobrazí v poli **název** . Změňte toto pole na MathClass. vb a klikněte na **Přidat**. Tím se vytvoří třída s názvem `MathClass` a zobrazí se její kód.

6. Přidejte následující kód na začátek `MathClass` k dědění z třídy com.

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. Přetížení veřejné metody základní třídy přidáním následujícího kódu do `MathClass` :

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. Rozšíří zděděnou třídu přidáním následujícího kódu do `MathClass` :

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

Nová třída zdědí vlastnosti základní třídy v objektu COM, přetěžuje metodu a definuje novou metodu pro rozšiřování třídy.

### <a name="to-test-the-inherited-class"></a>Testování zděděné třídy

1. Přidejte tlačítko do formuláře po spuštění a pak dvakrát klikněte na něj, aby se zobrazil jeho kód.

2. V `Click` proceduře obslužné rutiny události tlačítka přidejte následující kód pro vytvoření instance `MathClass` a volání přetížených metod:

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. Spusťte projekt stisknutím klávesy F5.

Po kliknutí na tlačítko ve formuláři `AddNumbers` je metoda nejprve volána s `Short` čísly datového typu a Visual Basic zvolí vhodnou metodu ze základní třídy. Druhé volání na `AddNumbers` je přesměrováno na metodu přetížení z `MathClass` . Třetí volání volá `SubtractNumbers` metodu, která rozšiřuje třídu. Vlastnost v základní třídě je nastavena a zobrazí se hodnota.

## <a name="next-steps"></a>Další kroky

Možná jste si všimli, že přetížená `AddNumbers` funkce má stejný datový typ jako metoda zděděná od základní třídy objektu com. Důvodem je, že argumenty a parametry metody základní třídy jsou definovány jako 16bitová celá čísla v Visual Basic 6,0, ale jsou vystavena jako 16bitové celé číslo typu `Short` v pozdějších verzích Visual Basic. Nová funkce přijímá 32 celých čísel a přetěžuje funkci základní třídy.

Při práci s objekty modelu COM ověřte, zda je nutné ověřit velikost a datové typy parametrů. Například při použití objektu COM, který přijímá objekt kolekce Visual Basic 6,0 jako argument, nelze poskytnout kolekci z novější verze Visual Basic.

Vlastnosti a metody zděděné z tříd modelu COM lze přepsat, což znamená, že lze deklarovat místní vlastnost nebo metodu, která nahrazuje vlastnost nebo metodu zděděnou ze základní třídy COM. Pravidla pro přepsání zděděných vlastností modelu COM jsou podobná pravidlům pro přepsání dalších vlastností a metod s následujícími výjimkami:

- Pokud přepíšete jakoukoliv vlastnost nebo metodu děděnou z třídy modelu COM, je nutné přepsat všechny ostatní zděděné vlastnosti a metody.

- Vlastnosti, které používají `ByRef` parametry, nelze přepsat.

## <a name="see-also"></a>Viz také

- [Interoperabilita modelů COM v aplikacích .NET Framework](com-interoperability-in-net-framework-applications.md)
- [Inherits – příkaz](../../language-reference/statements/inherits-statement.md)
- [Short – datový typ](../../language-reference/data-types/short-data-type.md)
