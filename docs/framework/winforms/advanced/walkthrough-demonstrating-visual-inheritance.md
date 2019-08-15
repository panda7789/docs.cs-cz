---
title: 'Návod: Demonstrace vizuálního dědění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 6fd504269ae9afbfd02b58276582a644674e1e0f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040323"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Návod: Demonstrace vizuálního dědění

Dědičnost vizuálů umožňuje zobrazit ovládací prvky na základním formuláři a přidat nové ovládací prvky. V tomto návodu vytvoříte základní formulář a zkompilujete ho do knihovny tříd. Tuto knihovnu tříd naimportujete do jiného projektu a vytvoříte nový formulář, který bude dědit ze základního formuláře. V tomto návodu se naučíte:

- Vytvořte projekt knihovny tříd obsahující základní formulář.

- Přidejte tlačítko s vlastnostmi, které mohou změnit odvozené třídy základního formuláře.

- Přidejte tlačítko, které nemůže být změněno děděním základního formuláře.

- Vytvořte projekt obsahující formulář, ze `BaseForm`kterého se dědí.

Nakonec tento návod ukáže rozdíl mezi soukromými a chráněnými ovládacími prvky ve zděděném formuláři.

> [!CAUTION]
> Ne všechny ovládací prvky podporují vizuální dědění ze základního formuláře. Následující ovládací prvky nepodporují Scénář popsaný v tomto návodu:
>
>  <xref:System.Windows.Forms.WebBrowser>
>
>  <xref:System.Windows.Forms.ToolStrip>
>
>  <xref:System.Windows.Forms.ToolStripPanel>
>
>  <xref:System.Windows.Forms.TableLayoutPanel>
>
>  <xref:System.Windows.Forms.FlowLayoutPanel>
>
>  <xref:System.Windows.Forms.DataGridView>
>
>  Tyto ovládací prvky ve zděděném formuláři jsou vždycky jen pro čtení, bez ohledu na modifikátory, které`private`používáte `protected`(, `public`nebo).

## <a name="create-a-class-library-project-containing-a-base-form"></a>Vytvořit projekt knihovny tříd obsahující základní formulář

1. V aplikaci Visual Studio v nabídce **soubor** vyberte možnost **Nový** > **projekt** , čímž otevřete dialogové okno **Nový projekt** .

2. Vytvořte aplikaci model Windows Forms s názvem `BaseFormLibrary`.

3. Chcete-li vytvořit knihovnu tříd namísto standardní model Windows Forms aplikace, v **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **BaseFormLibrary** a poté vyberte možnost **vlastnosti**.

4. Ve vlastnostech projektu změňte **Typ výstupu** z **aplikace systému Windows** na **Knihovna tříd**.

5. V nabídce **soubor** klikněte na příkaz **Uložit vše** a uložte projekt a soubory do výchozího umístění.

 Následující dva postupy přidávají tlačítka do základního formuláře. K demonstraci vizuální dědičnosti získáte tlačítka různé úrovně přístupu nastavením jejich `Modifiers` vlastností.

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Přidat tlačítko, které dědí dědění základního formuláře, se může změnit.

1. Otevřete **Form1** v návrháři.

2. Na kartě **všechny model Windows Forms** panelu **nástrojů**klikněte dvakrát na tlačítko a přidejte tak tlačítko do formuláře. Pomocí myši umístěte a změňte velikost tlačítka.

3. V okno Vlastnosti nastavte následující vlastnosti tlačítka:

    - Nastavte vlastnost **text** na text **říká**se Hello.

    - Nastavte vlastnost **(Name)** na **btnProtected**.

    - Nastavte vlastnost **modifikátory** na hodnotu **Protected**. Díky tomu je možné, že formuláře, které dědí z **Form1** , upravou vlastnosti **btnProtected**.

4. Dvojím kliknutím na tlačítko **vyslovení Hello** přidejte obslužnou rutinu události pro událost **Click** .

5. Do obslužné rutiny události přidejte následující řádek kódu:

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Přidejte tlačítko, které nemůže být změněno děděním základního formuláře.

1. Přepněte do zobrazení návrhu kliknutím na kartu **Form1. vb [Design], Form1.cs [Design] nebo Form1. jsl [Design]** nad Editor kódu nebo stisknutím klávesy F7.

2. Přidejte druhé tlačítko a nastavte jeho vlastnosti následujícím způsobem:

    - Nastavte vlastnost **text** na **nepravdu**.

    - Nastavte vlastnost **(Name)** na **btnPrivate**.

    - Nastavte vlastnost **modifikátory** na **Private**. To znemožňuje, aby formuláře, které dědí z **Form1** , upravily vlastnosti **btnPrivate**.

3. Dvojím kliknutím na tlačítko **vyslovit** nemožnost přidejte obslužnou rutinu události pro událost **Click** . Do procedury události vložte následující řádek kódu:

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. V nabídce **sestavení** vyberte možnost **sestavit BaseForm Library** a sestavte knihovnu tříd.

     Po sestavení knihovny můžete vytvořit nový projekt, který dědí z formuláře, který jste právě vytvořili.

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Vytvoří projekt obsahující formulář, který dědí z základního formuláře.

1. V nabídce **soubor** zvolte možnost **Přidat** a **Nový projekt** . otevře se dialogové okno **Přidat nový projekt** .

2. Vytvořte aplikaci model Windows Forms s názvem `InheritanceTest`.

## <a name="add-an-inherited-form"></a>Přidat zděděný formulář

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **InheritanceTest** , vyberte možnost **Přidat**a poté vyberte možnost **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte kategorii **model Windows Forms** (Pokud máte seznam kategorií) a pak vyberte zděděnou šablonu **formuláře** .

3. Ponechte výchozí název `Form2` a pak klikněte na **Přidat**.

4. V dialogovém okně **Výběr dědičnosti** vyberte v projektu **BaseFormLibrary** položku **Form1** jako formulář, ze kterého chcete dědit, a klikněte na tlačítko **OK**.

     Tím se vytvoří formulář v projektu **InheritanceTest** , který je odvozený z formuláře v **BaseFormLibrary**.

5. Otevřete zděděný formulář (**Form2**) v Návrháři tak, že na něj dvakrát kliknete, pokud ještě není otevřený.

     V Návrháři mají zděděná tlačítka symbol (![Snímek obrazovky Visual Basic symbolu dědičnosti](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) v horním rohu, což označuje, že jsou zděděné.

6. Vyberte tlačítko **vyslovit Hello** a sledujte úchyty pro změnu velikosti. Vzhledem k tomu, že je toto tlačítko chráněno, mohou dědit jej přesunout, změnit jeho popisek a provést další úpravy.

7. Vyberte tlačítko pro nemožnost nevlastníení a Všimněte si, že nemá úchyty pro změnu velikosti. Kromě toho v okně **vlastnosti** jsou vlastnosti tohoto tlačítka zobrazeny šedě, aby označovaly, že nelze upravovat.

8. Pokud používáte vizuál C#:

    1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **Form1** v projektu **InheritanceTest** a pak zvolte **Odstranit**. V zobrazeném okně se zprávou potvrďte odstranění kliknutím na tlačítko **OK** .

    2. Otevřete soubor program.cs a změňte řádek `Application.Run(new Form1());` na. `Application.Run(new Form2());`

9. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **InheritanceTest** a vyberte **nastavit jako spouštěný projekt**.

10. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **InheritanceTest** a vyberte **vlastnosti**.

11. Na stránkách vlastností **InheritanceTest** nastavte **spouštěcí objekt** na zděděný formulář (**Form2**).

12. Stisknutím klávesy **F5** spusťte aplikaci a sledujte chování zděděné formuláře.

## <a name="next-steps"></a>Další kroky

Dědičnost uživatelských ovládacích prvků pracuje podobně jako u sebe. Otevřete nový projekt knihovny tříd a přidejte uživatelský ovládací prvek. Umístěte ovládací prvky prvku na ni a zkompilujte projekt. Otevřete jiný nový projekt knihovny tříd a přidejte odkaz na zkompilované knihovny tříd. Také se pokuste přidat Zděděný ovládací prvek (pomocí dialogového okna **Přidat nové položky** ) do projektu a použít **Výběr dědičnosti**. Přidejte uživatelský ovládací prvek a změňte `Inherits` příkaz (`:` v jazyce Visual C#). Další informace najdete v tématu [jak: Zdědit model Windows Forms](how-to-inherit-windows-forms.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Zdědit model Windows Forms](how-to-inherit-windows-forms.md)
- [Vizuální dědění modelu Windows Forms](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
