---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cdf472776fc293bc5dfa1db940d23c6a297767e7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C# #
S [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*. Prostřednictvím dědičnosti budete moci vytvořit ovládací prvky, které nezachovají vyplývajících funkce standardní ovládací prvky Windows Forms, ale také obsahovat vlastní funkce. V tomto návodu vytvoříte jednoduchý zděděné ovládací prvek názvem `ValueButton`. Toto tlačítko bude funkce dědit ze standardní Windows Forms <xref:System.Windows.Forms.Button> řízení a zveřejní vlastní vlastnost s názvem `ButtonValue`.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Když vytvoříte nový projekt, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že součást výchozí bude ve správném oboru názvů zadejte její název.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>K vytvoření knihovny řízení ValueButtonLib a ValueButton ovládací prvek  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  Vyberte **knihovny ovládacích prvků Windows Forms** šablona projektu ze seznamu Projekty Visual C# a typ `ValueButtonLib` v **název** pole.  
  
     Název projektu `ValueButtonLib`, je také přiřazený k oboru názvů root ve výchozím nastavení. Kořenový obor názvů se použijí pro kvalifikaci názvy součásti v sestavení. Například, pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete zadat vaše `ValueButton` pomocí součásti `ValueButtonLib.ValueButton`. Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).  
  
3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **UserControl1.cs**, zvolte **přejmenovat** z místní nabídky. Změňte název souboru `ValueButton.cs`. Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu '`UserControl1`'.  
  
4.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **kód zobrazení**.  
  
5.  Vyhledejte `class` řádku příkaz `public partial class ValueButton`a změnit typ, ze kterého tento ovládací prvek dědí z <xref:System.Windows.Forms.UserControl> k <xref:System.Windows.Forms.Button>. To umožňuje vaší zděděné řídit dědění všechny funkce <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
6.  V **Průzkumníku řešení**, otevřete **ValueButton.cs** uzel k zobrazení souboru generovaném kódu **ValueButton.Designer.cs**. Otevřete tento soubor **Editor kódu**.  
  
7.  Vyhledejte `InitializeComponent` metoda a odebrat řádek, který přiřazuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnost. Tato vlastnost neexistuje v <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
8.  Z **soubor** nabídce zvolte **Uložit vše** k uložení projektu.  
  
    > [!NOTE]
    >  Vizuální návrhář již není k dispozici. Protože <xref:System.Windows.Forms.Button> ovládací prvek provádí vlastní Malování, nebudete moci upravit její vzhled v návrháři. Jeho vizuální znázornění budou přesně stejné jako příkaz, který dědí z třídy (tedy <xref:System.Windows.Forms.Button>) není-li upravit v kódu. Součásti, které mají žádné elementy uživatelského rozhraní, můžete přesto přidat na plochu návrháře.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Přidání vlastnosti do vlastního zděděné ovládacího prvku  
 Je možné použití zděděné ovládacích prvků Windows Forms vytváření ovládacích prvků, které jsou identické v vzhledu a chování standardní ovládací prvky Windows Forms, ale vystavit vlastní vlastnosti. V této části přidáte vlastnost s názvem `ButtonValue` do vašeho ovládacího prvku.  
  
#### <a name="to-add-the-value-property"></a>Chcete-li přidat hodnota vlastnosti  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na **kód zobrazení** z místní nabídky.  
  
2.  Vyhledejte `class` příkaz. Ihned po `{`, zadejte následující kód:  
  
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
  
     Tento kód nastaví metody, pomocí kterého `ButtonValue` vlastnost uložena a následně načtena. `get` Příkaz nastaví hodnotu, vrátí hodnotu, která v soukromé proměnné je uloženo `varValue`a `set` příkaz nastaví hodnotu soukromé proměnné pomocí `value` – klíčové slovo.  
  
3.  Z **soubor** nabídce zvolte **Uložit vše** k uložení projektu.  
  
## <a name="testing-your-control"></a>Testování vlastního ovládacího prvku  
 Ovládací prvky nejsou samostatné projekty; musí být hostované v kontejneru. Chcete-li otestovat vlastní ovládací prvek, je nutné zadat pro něj spustit v testovacího projektu. Je nutné provést kontrolu nad přístupné pro projekt test podle budovy (kompilace) ho. V této části bude sestavovat vlastní ovládací prvek a otestovat ve formuláři Windows.  
  
#### <a name="to-build-your-control"></a>K vytvoření vlastního ovládacího prvku  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Sestavení by měl být úspěšné bez chyb kompilátoru a upozornění.  
  
#### <a name="to-create-a-test-project"></a>K vytvoření projektu testů  
  
1.  Na **soubor** nabídky, přejděte na příkaz **přidat** a pak klikněte na **nový projekt** otevřete **přidat nový projekt** dialogové okno.  
  
2.  Vyberte **Windows** uzlu, ybrat **Visual C#** uzel a klikněte na tlačítko **formulářové aplikace Windows**.  
  
3.  V **název** zadejte `Test`.  
  
4.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** vyberte uzel pro váš projekt test **přidat odkaz na** z místní nabídky k zobrazení  **Přidat odkaz** dialogové okno.  
  
5.  Klikněte na kartu s názvem bez přípony **projekty**. Vaše `ValueButtonLib` projektu, zobrazí se v části **název projektu**. Dvakrát klikněte na projekt se přidat odkaz na projekt test.  
  
6.  V **Průzkumníku řešení** klikněte pravým tlačítkem na **Test** a vyberte **sestavení**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Chcete-li přidat vlastní ovládací prvek formuláře  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.cs** a zvolte **Návrhář zobrazení** z místní nabídky.  
  
2.  V **sada nástrojů**, klikněte na tlačítko **ValueButtonLib součásti**. Klikněte dvakrát na **ValueButton**.  
  
     A **ValueButton** se zobrazí na formuláři.  
  
3.  Klikněte pravým tlačítkem myši **ValueButton** a vyberte **vlastnosti** z místní nabídky.  
  
4.  V **vlastnosti** okno, podívejte se na vlastnosti tohoto ovládacího prvku. Všimněte si, jestli se shodují na vlastnosti vystavené standardní tlačítko s tím rozdílem, že další vlastnost, `ButtonValue`.  
  
5.  Nastavte `ButtonValue` vlastnost `5`.  
  
6.  V **všechny formuláře Windows** kartě **sada nástrojů**, dvakrát klikněte na **popisek** přidat <xref:System.Windows.Forms.Label> ovládacího prvku do svého formuláře.  
  
7.  Popisek přemístěte na střed tvaru.  
  
8.  Klikněte dvakrát na `valueButton1`.  
  
     **Editor kódu** se otevře `valueButton1_Click` událostí.  
  
9. Vložte následující kód.  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Test**a zvolte **nastavit jako spouštěný projekt** z místní nabídky.  
  
11. Z **ladění** nabídce vyberte možnost **spustit ladění**.  
  
     `Form1` Zobrazí se.  
  
12. Klikněte na tlačítko `valueButton1`.  
  
     Číslo "5" se zobrazí v `label1`, představujících, `ButtonValue` byla předána vlastnost zděděné ovládacího prvku `label1` prostřednictvím `valueButton1_Click` metoda. Proto vaše `ValueButton` řízení dědí všechny funkce standardní tlačítka Windows Forms, ale zveřejňuje o další, vlastní vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Programování s komponentami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Součást pro vytváření obsahu návody](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
