---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic'
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
ms.openlocfilehash: a6b1e78d17d952590510bdda80bf802ccc094285
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541434"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic
V jazyce Visual Basic, můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*. Prostřednictvím dědičnosti budete moci vytvořit ovládací prvky, které nezachovají vyplývajících funkce standardní ovládací prvky Windows Forms, ale také obsahovat vlastní funkce. V tomto návodu vytvoříte jednoduchý zděděné ovládací prvek názvem `ValueButton`. Toto tlačítko bude funkce dědit ze standardní Windows Forms <xref:System.Windows.Forms.Button> řízení a zveřejní vlastní vlastnost s názvem `ButtonValue`.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Když vytvoříte nový projekt, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že součást výchozí bude ve správném oboru názvů zadejte její název.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>K vytvoření knihovny řízení ValueButtonLib a ValueButton ovládací prvek  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  Vyberte **knihovny ovládacích prvků Windows Forms** šablona projektu ze seznamu Projekty Visual Basic a typ `ValueButtonLib` v **název** pole.  
  
     Název projektu `ValueButtonLib`, je také přiřazený k oboru názvů root ve výchozím nastavení. Kořenový obor názvů se použijí pro kvalifikaci názvy součásti v sestavení. Například, pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete zadat vaše `ValueButton` pomocí součásti `ValueButtonLib.ValueButton`. Další informace najdete v tématu [obory názvů v jazyce Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **UserControl1.vb**, zvolte **přejmenovat** z místní nabídky. Změňte název souboru `ValueButton.vb`. Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu 'UserControl1'.  
  
4.  V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko.  
  
5.  Otevřete **ValueButton.vb** uzel k zobrazení souboru generovaném kódu **ValueButton.Designer.vb**. Otevřete tento soubor **Editor kódu**.  
  
6.  Vyhledejte `Class` příkaz `Partial Public Class ValueButton`a změnit typ, ze kterého tento ovládací prvek dědí z <xref:System.Windows.Forms.UserControl> k <xref:System.Windows.Forms.Button>. To umožňuje vaší zděděné řídit dědění všechny funkce <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
7.  Vyhledejte `InitializeComponent` metoda a odebrat řádek, který přiřazuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnost. Tato vlastnost neexistuje v <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
8.  Z **soubor** nabídce zvolte **Uložit vše** k uložení projektu.  
  
     Všimněte si, že vizuálního návrháře již není k dispozici. Protože <xref:System.Windows.Forms.Button> ovládací prvek provádí vlastní Malování, nebudete moci upravit její vzhled v návrháři. Jeho vizuální znázornění budou přesně stejné jako příkaz, který dědí z třídy (tedy <xref:System.Windows.Forms.Button>) není-li upravit v kódu.  
  
> [!NOTE]
>  Součásti, které mají žádné elementy uživatelského rozhraní, můžete přesto přidat na plochu návrháře.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Přidání vlastnosti do vlastního zděděné ovládacího prvku  
 Je možné použití zděděné ovládacích prvků Windows Forms vytváření ovládacích prvků, které jsou stejné jako v vzhled a chování (vzhled a chování) standardní ovládací prvky Windows Forms, ale vystavit vlastní vlastnosti. V této části přidáte vlastnost s názvem `ButtonValue` do vašeho ovládacího prvku.  
  
#### <a name="to-add-the-value-property"></a>Chcete-li přidat hodnota vlastnosti  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ValueButton.vb**a potom klikněte na **kód zobrazení** z místní nabídky.  
  
2.  Vyhledejte `Public Class ValueButton` příkaz. Bezprostředně pod tohoto prohlášení, zadejte následující kód:  
  
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
  
     Tento kód nastaví metody, pomocí kterého `ButtonValue` vlastnost uložena a následně načtena. `Get` Příkaz nastaví hodnotu, vrátí hodnotu, která v soukromé proměnné je uloženo `varValue`a `Set` příkaz nastaví hodnotu soukromé proměnné pomocí `Value` – klíčové slovo.  
  
3.  Z **soubor** nabídce zvolte **Uložit vše** k uložení projektu.  
  
## <a name="testing-your-control"></a>Testování vlastního ovládacího prvku  
 Ovládací prvky nejsou samostatné projekty; musí být hostované v kontejneru. Chcete-li otestovat vlastní ovládací prvek, je nutné zadat pro něj spustit v testovacího projektu. Je nutné provést kontrolu nad přístupné pro projekt test podle budovy (kompilace) ho. V této části bude sestavovat vlastní ovládací prvek a otestovat ve formuláři Windows.  
  
#### <a name="to-build-your-control"></a>K vytvoření vlastního ovládacího prvku  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Sestavení by měl být úspěšné bez chyb kompilátoru a upozornění.  
  
#### <a name="to-create-a-test-project"></a>K vytvoření projektu testů  
  
1.  Na **soubor** nabídky, přejděte na příkaz **přidat** a pak klikněte na **nový projekt** otevřete **přidat nový projekt** dialogové okno.  
  
2.  Vyberte uzel projektů jazyka Visual Basic a klikněte na tlačítko **formulářové aplikace Windows**.  
  
3.  V **název** zadejte `Test`.  
  
4.  V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko.  
  
5.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** vyberte uzel pro váš projekt test **přidat odkaz na** z místní nabídky k zobrazení  **Přidat odkaz** dialogové okno.  
  
6.  Klikněte **projekty** kartě.  
  
7.  Klikněte na kartu s názvem bez přípony **projekty**. Vaše `ValueButtonLib` projektu, zobrazí se v části **název projektu**. Dvakrát klikněte na projekt se přidat odkaz na projekt test.  
  
8.  V **Průzkumníku řešení** klikněte pravým tlačítkem na **Test** a vyberte **sestavení**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Chcete-li přidat vlastní ovládací prvek formuláře  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.vb** a zvolte **Návrhář zobrazení** z místní nabídky.  
  
2.  V **sada nástrojů**, klikněte na tlačítko **ValueButtonLib součásti**. Klikněte dvakrát na **ValueButton**.  
  
     A **ValueButton** se zobrazí na formuláři.  
  
3.  Klikněte pravým tlačítkem myši **ValueButton** a vyberte **vlastnosti** z místní nabídky.  
  
4.  V **vlastnosti** okno, podívejte se na vlastnosti tohoto ovládacího prvku. Všimněte si, jestli se shodují na vlastnosti vystavené standardní tlačítko s tím rozdílem, že další vlastnost, `ButtonValue`.  
  
5.  Nastavte `ButtonValue` vlastnost `5`.  
  
6.  Na **všechny formuláře Windows** kartě **sada nástrojů**, dvakrát klikněte na **popisek** přidat <xref:System.Windows.Forms.Label> ovládacího prvku do svého formuláře.  
  
7.  Popisek přemístěte na střed tvaru.  
  
8.  Klikněte dvakrát na `ValueButton1`.  
  
     **Editor kódu** se otevře `ValueButton1_Click` událostí.  
  
9. Zadejte následující řádek kódu.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Test**a zvolte **nastavit jako spouštěný projekt** z místní nabídky.  
  
11. Z **ladění** nabídce vyberte možnost **spustit ladění**.  
  
     `Form1` Zobrazí se.  
  
12. Klikněte na tlačítko `Valuebutton1`.  
  
     Číslo "5" se zobrazí v `Label1`, představujících, `ButtonValue` byla předána vlastnost zděděné ovládacího prvku `Label1` prostřednictvím `ValueButton1_Click` metoda. Proto vaše `ValueButton` řízení dědí všechny funkce standardní tlačítka Windows Forms, ale zveřejňuje o další, vlastní vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Základní informace o dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Součást pro vytváření obsahu návody](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
