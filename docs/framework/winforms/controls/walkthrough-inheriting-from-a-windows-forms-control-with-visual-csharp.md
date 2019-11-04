---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c54733a340b1855b3fc7b90ff2b5178fad8c5303
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460590"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a>Návod: dědění z ovládacího prvku model Windows Forms pomocí jazyka C\#

Pomocí vizuálu C#můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*. Prostřednictvím dědičnosti můžete vytvářet ovládací prvky, které budou uchovávat veškerou základní funkci standardních model Windows Formsch ovládacích prvků, ale také zahrnovat vlastní funkce. V tomto návodu vytvoříte jednoduchý Zděděný ovládací prvek s názvem `ValueButton`. Toto tlačítko zdědí funkce ze standardního ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> a zpřístupní vlastní vlastnost s názvem `ButtonValue`.

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření nového projektu zadáte jeho název, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že výchozí komponenta bude ve správném oboru názvů.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Vytvoření knihovny ovládacích prvků ValueButtonLib a ovládacího prvku ValueButton

1. V aplikaci Visual Studio vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** a pojmenujte jej **ValueButtonLib**.

     Název projektu, `ValueButtonLib`, je ve výchozím nastavení přiřazen také kořenovému oboru názvů. Kořenový obor názvů slouží k získání názvů komponent v sestavení. Například pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete určit `ValueButton` komponentu pomocí `ValueButtonLib.ValueButton`. Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).

2. V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1.cs**a pak zvolte **Přejmenovat** z místní nabídky. Změňte název souboru na **ValueButton.cs**. Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu '`UserControl1`', klikněte na tlačítko **Ano** .

3. V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **Zobrazit kód**.

4. Vyhledejte řádek příkazu `class`, `public partial class ValueButton`a změňte typ, ze kterého tento ovládací prvek dědí z <xref:System.Windows.Forms.UserControl> na <xref:System.Windows.Forms.Button>. To umožňuje děděnému ovládacímu prvku dědit všechny funkce <xref:System.Windows.Forms.Button>ho ovládacího prvku.

5. V **Průzkumník řešení**otevřete uzel **ValueButton.cs** pro zobrazení souboru kódu generovaného návrhářem **ValueButton.Designer.cs**. Otevřete tento soubor v **editoru kódu**.

6. Vyhledejte metodu `InitializeComponent` a odeberte čáru, která přiřadí vlastnost <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>. Tato vlastnost v ovládacím prvku <xref:System.Windows.Forms.Button> neexistuje.

7. V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.

    > [!NOTE]
    > Vizuální Návrhář již není k dispozici. Vzhledem k tomu, že ovládací prvek <xref:System.Windows.Forms.Button> vlastní malování, nemůžete změnit jeho vzhled v návrháři. Jeho vizuální reprezentace bude přesně stejná jako třída, ze které dědí (to znamená <xref:System.Windows.Forms.Button>), pokud se v kódu nezmění. Na návrhovou plochu stále můžete přidat komponenty, které nemají žádné prvky uživatelského rozhraní.

## <a name="add-a-property-to-your-inherited-control"></a>Přidání vlastnosti k Zděděnému ovládacímu prvku

Jedním z možných použití děděných ovládacích prvků model Windows Forms je vytváření ovládacích prvků, které jsou identické ve vzhledu a chování standardních model Windows Formsch ovládacích prvků, ale zpřístupňují vlastní vlastnosti. V této části přidáte k ovládacímu prvku vlastnost s názvem `ButtonValue`.

### <a name="to-add-the-value-property"></a>Přidání vlastnosti Value

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na **Zobrazit kód** z místní nabídky.

2. Vyhledejte příkaz `class`. Hned za `{`zadejte následující kód:

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     Tento kód nastaví metody, podle kterých je vlastnost `ButtonValue` uložena a načtena. Příkaz `get` nastaví hodnotu vrácenou na hodnotu, která je uložena v `varValue`privátních proměnných, a příkaz `set` nastaví hodnotu soukromé proměnné pomocí klíčového slova `value`.

3. V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.

## <a name="test-the-control"></a>Testování ovládacího prvku

Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru. Chcete-li otestovat ovládací prvek, je nutné zadat projekt testů, aby jej bylo možné spustit v. Je také nutné mít přístup k ovládacímu prvku pro testovací projekt sestavením (kompilováním). V této části vytvoříte ovládací prvek a otestujete ho ve formuláři Windows.

### <a name="to-build-your-control"></a>Sestavení ovládacího prvku

V nabídce **sestavení** klikněte na **Sestavit řešení**. Sestavení by mělo být úspěšné bez chyb nebo upozornění kompilátoru.

### <a name="to-create-a-test-project"></a>Vytvoření testovacího projektu

1. V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt** . tím otevřete dialogové okno **Přidat nový projekt** .

2. Vyberte uzel **Windows** pod uzlem **vizuálů C#**  a klikněte na **model Windows Forms aplikace**.

3. Do pole **název** zadejte **test**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů a pak vyberte možnost **Přidat odkaz** z místní nabídky a zobrazte tak dialogové okno **Přidat odkaz** .

5. Klikněte na kartu s označením **projekty**. Váš projekt ValueButtonLib bude uveden v části **název projektu**. Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.

6. V **Průzkumník řešení** klikněte pravým tlačítkem na **test** a vyberte **sestavit**.

### <a name="to-add-your-control-to-the-form"></a>Přidání ovládacího prvku do formuláře

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a v místní nabídce vyberte **zobrazit Návrhář** .

2. V sadě **nástrojů**vyberte **součásti ValueButtonLib**. Dvakrát klikněte na **ValueButton**.

     Ve formuláři se zobrazí **ValueButton** .

3. Klikněte pravým tlačítkem na **ValueButton** a v místní nabídce vyberte **vlastnosti** .

4. V okně **vlastnosti** prověřte vlastnosti tohoto ovládacího prvku. Všimněte si, že jsou stejné jako vlastnosti zveřejněné standardním tlačítkem, s výjimkou toho, že existuje další vlastnost ButtonValue.

5. Nastavte vlastnost **ButtonValue** na hodnotu **5**.

6. Na kartě **všechny model Windows Forms** **panelu nástrojů**přidejte ovládací prvek <xref:System.Windows.Forms.Label> do formuláře dvojitým kliknutím na položku **popisek** .

7. Přemístěte popisek na střed formuláře.

8. Dvakrát klikněte na `valueButton1`.

     Otevře se **Editor kódu** pro událost `valueButton1_Click`.

9. Vložte následující řádek kódu.

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

11. V nabídce **ladění** vyberte **Spustit ladění**.

     zobrazí se `Form1`.

12. Klikněte na `valueButton1`.

     V `label1`se zobrazí číslice 5, které demonstruje, že vlastnost `ButtonValue` zděděného ovládacího prvku byla předána `label1` prostřednictvím metody `valueButton1_Click`. Proto váš ovládací prvek `ValueButton` dědí všechny funkce standardního model Windows Formsho tlačítka, ale zpřístupňuje další vlastní vlastnost.

## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
