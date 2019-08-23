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
ms.openlocfilehash: c06639ef2f2ced8bd128adea636efe8be1715764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931024"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>Návod: Dědění z ovládacího prvku model Windows Forms s Visual C\#
Pomocí vizuálu C#můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*. Prostřednictvím dědičnosti můžete vytvářet ovládací prvky, které budou uchovávat veškerou základní funkci standardních model Windows Formsch ovládacích prvků, ale také zahrnovat vlastní funkce. V tomto návodu vytvoříte jednoduchý Zděděný ovládací prvek s názvem `ValueButton`. Toto tlačítko zdědí funkce ze standardního ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> a zpřístupní vlastní vlastnost s názvem. `ButtonValue`

## <a name="creating-the-project"></a>Vytvoření projektu
 Při vytváření nového projektu zadáte jeho název, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že výchozí komponenta bude ve správném oboru názvů.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Vytvoření knihovny ovládacích prvků ValueButtonLib a ovládacího prvku ValueButton

1. V nabídce **soubor** přejděte na příkaz **Nový** a potom klikněte na **projekt** . otevře se dialogové okno **Nový projekt** .

2. V seznamu vizuálních C# projektů vyberte šablonu projektu `ValueButtonLib` **knihovny ovládacích prvků model Windows Forms** a do pole **název** zadejte.

     Název projektu, `ValueButtonLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů. Kořenový obor názvů slouží k získání názvů komponent v sestavení. Například pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete určit svou `ValueButton` komponentu pomocí `ValueButtonLib.ValueButton`. Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).

3. V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1.cs**a pak zvolte **Přejmenovat** z místní nabídky. Změňte název souboru na `ValueButton.cs`. Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu '`UserControl1`', klikněte na tlačítko Ano.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **Zobrazit kód**.

5. Vyhledejte řádek `public partial class ValueButton` <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>příkazu, a změňte typ, ze kterého tento ovládací prvek dědí. `class` Tím umožníte zděděnému ovládacímu prvku dědění všech funkcí <xref:System.Windows.Forms.Button> ovládacího prvku.

6. V **Průzkumník řešení**otevřete uzel **ValueButton.cs** pro zobrazení souboru kódu generovaného návrhářem **ValueButton.Designer.cs**. Otevřete tento soubor v **editoru kódu**.

7. Vyhledejte metodu a odstraňte čáru, která <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> přiřadí vlastnost. `InitializeComponent` Tato vlastnost v <xref:System.Windows.Forms.Button> ovládacím prvku neexistuje.

8. V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.

    > [!NOTE]
    > Vizuální Návrhář již není k dispozici. Vzhledem k tomu, že ovládacíprvekprovedevlastnímalování,nemůžetezměnitjehovzhledvnávrháři.<xref:System.Windows.Forms.Button> Jeho vizuální reprezentace bude přesně stejná jako třída, ze které dědí ( <xref:System.Windows.Forms.Button>tj.), pokud není upravena v kódu. Na návrhovou plochu stále můžete přidat komponenty, které nemají žádné prvky uživatelského rozhraní.

## <a name="adding-a-property-to-your-inherited-control"></a>Přidání vlastnosti do zděděného ovládacího prvku
 Jedním z možných použití děděných ovládacích prvků model Windows Forms je vytváření ovládacích prvků, které jsou identické ve vzhledu a chování standardních model Windows Formsch ovládacích prvků, ale zpřístupňují vlastní vlastnosti. V této části přidáte k ovládacímu prvku vlastnost s `ButtonValue` názvem.

### <a name="to-add-the-value-property"></a>Přidání vlastnosti Value

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na **Zobrazit kód** z místní nabídky.

2. `class` Vyhledejte příkaz. Hned za `{`a zadejte následující kód:

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

     Tento kód nastaví metody, podle kterých `ButtonValue` je vlastnost uložena a načtena. Příkaz nastaví hodnotu vrácenou na hodnotu, která je uložena v soukromé proměnné `varValue`, a `set` příkaz nastaví hodnotu soukromé proměnné `value` pomocí klíčového slova. `get`

3. V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.

## <a name="testing-your-control"></a>Testování ovládacího prvku
 Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru. Chcete-li otestovat ovládací prvek, je nutné zadat projekt testů, aby jej bylo možné spustit v. Je také nutné mít přístup k ovládacímu prvku pro testovací projekt sestavením (kompilováním). V této části vytvoříte ovládací prvek a otestujete ho ve formuláři Windows.

### <a name="to-build-your-control"></a>Sestavení ovládacího prvku

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

     Sestavení by mělo být úspěšné bez chyb nebo upozornění kompilátoru.

### <a name="to-create-a-test-project"></a>Vytvoření testovacího projektu

1. V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt** . tím otevřete dialogové okno **Přidat nový projekt** .

2. Vyberte uzel **Windows** pod uzlem **vizuálů C#**  a klikněte na **model Windows Forms aplikace**.

3. Do pole **název** zadejte `Test`.

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů a pak vyberte možnost **Přidat odkaz** z místní nabídky a zobrazte tak dialogové okno **Přidat odkaz** .

5. Klikněte na kartu s označením **projekty**. Projekt bude uveden v části **název projektu.** `ValueButtonLib` Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.

6. V **Průzkumník řešení** klikněte pravým tlačítkem na **test** a vyberte **sestavit**.

### <a name="to-add-your-control-to-the-form"></a>Přidání ovládacího prvku do formuláře

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a v místní nabídce vyberte **zobrazit Návrhář** .

2. V sadě **nástrojů**klikněte na **součásti ValueButtonLib**. Dvakrát klikněte na **ValueButton**.

     Ve formuláři se zobrazí **ValueButton** .

3. Klikněte pravým tlačítkem na **ValueButton** a v místní nabídce vyberte **vlastnosti** .

4. V okně **vlastnosti** prověřte vlastnosti tohoto ovládacího prvku. Všimněte si, že jsou stejné jako vlastnosti zveřejněné standardním tlačítkem, s výjimkou toho, že existuje další vlastnost `ButtonValue`,.

5. Nastavte `ButtonValue` vlastnost `5`.

6. Na kartě **Všechny model Windows Forms** **panelu nástrojů**přidejte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře dvojitým kliknutím na položku **popisek** .

7. Přemístěte popisek na střed formuláře.

8. Poklikejte na `valueButton1`.

     Otevře se **Editor kódu** pro `valueButton1_Click` událost.

9. Vložte následující řádek kódu.

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

11. V nabídce **ladění** vyberte **Spustit ladění**.

     `Form1`uvedeny.

12. Klikněte `valueButton1`na.

     Číslice "5" se zobrazí `label1`v, `ButtonValue` což demonstruje, že vlastnost zděděného `label1` ovládacího prvku byla předána prostřednictvím `valueButton1_Click` metody. Proto váš `ValueButton` ovládací prvek zdědí všechny funkce standardního model Windows Formsho tlačítka, ale zpřístupňuje další vlastní vlastnost.

## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
