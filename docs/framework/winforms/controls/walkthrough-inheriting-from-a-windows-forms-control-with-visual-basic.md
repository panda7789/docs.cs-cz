---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 378d7b0c67791e6c48e9859e0546594df3ccc85e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931005"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu
Pomocí Visual Basic můžete pomocí dědičnosti vytvářet výkonné vlastní ovládacíprvky. Prostřednictvím dědičnosti můžete vytvářet ovládací prvky, které budou uchovávat veškerou základní funkci standardních model Windows Formsch ovládacích prvků, ale také zahrnovat vlastní funkce. V tomto návodu vytvoříte jednoduchý Zděděný ovládací prvek s názvem `ValueButton`. Toto tlačítko zdědí funkce ze standardního ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> a zpřístupní vlastní vlastnost s názvem. `ButtonValue`

## <a name="creating-the-project"></a>Vytvoření projektu
 Při vytváření nového projektu zadáte jeho název, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že výchozí komponenta bude ve správném oboru názvů.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Vytvoření knihovny ovládacích prvků ValueButtonLib a ovládacího prvku ValueButton

1. V nabídce **soubor** přejděte na příkaz **Nový** a potom klikněte na **projekt** . otevře se dialogové okno **Nový projekt** .

2. V seznamu Visual Basic projektů vyberte šablonu projektu **knihovny ovládacích prvků model Windows Forms** a do pole **název** zadejte `ValueButtonLib` .

     Název projektu, `ValueButtonLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů. Kořenový obor názvů slouží k získání názvů komponent v sestavení. Například pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete určit svou `ValueButton` komponentu pomocí `ValueButtonLib.ValueButton`. Další informace najdete v tématu [obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).

3. V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1. vb**a pak zvolte **Přejmenovat** z místní nabídky. Změňte název souboru na `ValueButton.vb`. Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu ' UserControl1 ', klikněte na tlačítko **Ano** .

4. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .

5. Otevřete uzel **ValueButton. vb** pro zobrazení souboru kódu generovaného návrhářem **ValueButton. Designer. vb**. Otevřete tento soubor v **editoru kódu**.

6. Vyhledejte příkaz, a `Partial Public Class ValueButton`změňte typ, ze <xref:System.Windows.Forms.UserControl> kterého <xref:System.Windows.Forms.Button>tento ovládací prvek dědí. `Class` Tím umožníte zděděnému ovládacímu prvku dědění všech funkcí <xref:System.Windows.Forms.Button> ovládacího prvku.

7. Vyhledejte metodu a odstraňte čáru, která <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> přiřadí vlastnost. `InitializeComponent` Tato vlastnost v <xref:System.Windows.Forms.Button> ovládacím prvku neexistuje.

8. V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.

     Všimněte si, že vizuální Návrhář již není k dispozici. Vzhledem k tomu, že ovládacíprvekprovedevlastnímalování,nemůžetezměnitjehovzhledvnávrháři.<xref:System.Windows.Forms.Button> Jeho vizuální reprezentace bude přesně stejná jako třída, ze které dědí ( <xref:System.Windows.Forms.Button>tj.), pokud není upravena v kódu.

> [!NOTE]
> Na návrhovou plochu stále můžete přidat komponenty, které nemají žádné prvky uživatelského rozhraní.

## <a name="adding-a-property-to-your-inherited-control"></a>Přidání vlastnosti do zděděného ovládacího prvku
 Jedním z možných použití děděných ovládacích prvků model Windows Forms je vytváření ovládacích prvků, které jsou identické vzhledy a chování (vzhled a chování) pro standardní model Windows Forms ovládací prvky, ale zpřístupňují vlastní vlastnosti. V této části přidáte k ovládacímu prvku vlastnost s `ButtonValue` názvem.

### <a name="to-add-the-value-property"></a>Přidání vlastnosti Value

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton. vb**a pak klikněte na **Zobrazit kód** z místní nabídky.

2. `Public Class ValueButton` Vyhledejte příkaz. Hned pod tímto příkazem zadejte následující kód:

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     Tento kód nastaví metody, podle kterých `ButtonValue` je vlastnost uložena a načtena. Příkaz nastaví hodnotu vrácenou na hodnotu, která je uložena v soukromé proměnné `varValue`, a `Set` příkaz nastaví hodnotu soukromé proměnné `Value` pomocí klíčového slova. `Get`

3. V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.

## <a name="testing-your-control"></a>Testování ovládacího prvku
 Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru. Chcete-li otestovat ovládací prvek, je nutné zadat projekt testů, aby jej bylo možné spustit v. Je také nutné mít přístup k ovládacímu prvku pro testovací projekt sestavením (kompilováním). V této části vytvoříte ovládací prvek a otestujete ho ve formuláři Windows.

### <a name="to-build-your-control"></a>Sestavení ovládacího prvku

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

     Sestavení by mělo být úspěšné bez chyb nebo upozornění kompilátoru.

### <a name="to-create-a-test-project"></a>Vytvoření testovacího projektu

1. V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt** . tím otevřete dialogové okno **Přidat nový projekt** .

2. Vyberte uzel Visual Basic projekty a klikněte na **model Windows Forms aplikace**.

3. Do pole **název** zadejte `Test`.

4. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .

5. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů a pak vyberte možnost **Přidat odkaz** z místní nabídky a zobrazte tak dialogové okno **Přidat odkaz** .

6. Klikněte na kartu **projekty** .

7. Klikněte na kartu s označením **projekty**. Projekt bude uveden v části **název projektu.** `ValueButtonLib` Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.

8. V **Průzkumník řešení** klikněte pravým tlačítkem na **test** a vyberte **sestavit**.

### <a name="to-add-your-control-to-the-form"></a>Přidání ovládacího prvku do formuláře

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1. vb** a v místní nabídce vyberte **zobrazit Návrhář** .

2. V sadě **nástrojů**klikněte na **součásti ValueButtonLib**. Dvakrát klikněte na **ValueButton**.

     Ve formuláři se zobrazí **ValueButton** .

3. Klikněte pravým tlačítkem na **ValueButton** a v místní nabídce vyberte **vlastnosti** .

4. V okně **vlastnosti** prověřte vlastnosti tohoto ovládacího prvku. Všimněte si, že jsou stejné jako vlastnosti zveřejněné standardním tlačítkem, s výjimkou toho, že existuje další vlastnost `ButtonValue`,.

5. Nastavte `ButtonValue` vlastnost `5`.

6. Na kartě **Všechny model Windows Forms** **panelu nástrojů**přidejte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře dvojitým kliknutím na položku **popisek** .

7. Přemístěte popisek na střed formuláře.

8. Poklikejte na `ValueButton1`.

     Otevře se **Editor kódu** pro `ValueButton1_Click` událost.

9. Zadejte následující řádek kódu.

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

11. V nabídce **ladění** vyberte **Spustit ladění**.

     `Form1`uvedeny.

12. Klikněte `Valuebutton1`na.

     Číslice "5" se zobrazí `Label1`v, `ButtonValue` což demonstruje, že vlastnost zděděného `Label1` ovládacího prvku byla předána prostřednictvím `ValueButton1_Click` metody. Proto váš `ValueButton` ovládací prvek zdědí všechny funkce standardního model Windows Formsho tlačítka, ale zpřístupňuje další vlastní vlastnost.

## <a name="see-also"></a>Viz také:

- [Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Základy dědičnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
