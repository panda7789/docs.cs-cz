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
ms.openlocfilehash: bc91e3bde54eedb4d9dbcfcb9f7faa0ccc98e397
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398690"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Návod: Demonstrace vizuálního dědění
Vizuální dědění vám umožní zobrazit ovládací prvky ve formuláři základní a přidání nových ovládacích prvků. V tomto návodu vytvoříte základní formulář a zkompilovat ji do knihovny tříd. Bude import této knihovně tříd do jiného projektu a vytvoření nového formuláře, která dědí ze základního formuláře. V tomto návodu se dozvíte, jak:  
  
-   Vytvořte projekt knihovny tříd obsahující základní formulář.  
  
-   Přidejte tlačítko s vlastnostmi, které odvozené třídy základní formulář můžete upravit.  
  
-   Přidejte tlačítko, které nemůže upravit dědice základní formulář.  
  
-   Vytvořit projekt obsahující formulář, který dědí z `BaseForm`.  
  
 Nakonec tento návod vám ukáže rozdíl mezi soukromým a chráněným ovládacích prvků na zděděný formulář.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!CAUTION]
>  Ne všechny ovládací prvky podporují vizuální dědění ze základního formuláře. Následující ovládací prvky podle scénáře popsaného v tomto názorném postupu nepodporují:  
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
>  Tyto ovládací prvky ve formuláři zděděné jsou vždy jen pro čtení bez ohledu na to modifikátory použijete (`private`, `protected`, nebo `public`).  
  
## <a name="scenario-steps"></a>Kroky scénáře  
 Prvním krokem je vytvoření základního formuláře.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Chcete-li vytvořit projekt knihovny tříd obsahující základního formuláře  
  
1.  Z **souboru** nabídce zvolte **nový**a potom **projektu** otevřít **nový projekt** dialogové okno.  
  
2.  Vytvoření aplikace Windows Forms s názvem `BaseFormLibrary`.  
  
3.  K vytvoření knihovny tříd místo standardní aplikace Windows Forms v **Průzkumníka řešení**, klikněte pravým tlačítkem myši **BaseFormLibrary** uzel projektu a pak vyberte **vlastnosti**.  
  
4.  Ve vlastnostech projektu změnit **typ výstupu** z **aplikace Windows** k **knihovny tříd**.  
  
5.  Z **souboru** nabídce zvolte **Uložit vše** uložte projekt a soubory do výchozího umístění.  
  
 Následující dva postupy přidání tlačítek do základního formuláře. Abychom si předvedli vizuálního dědění, kterým pojmenujete tlačítka různé úrovně přístupu tak, že nastavíte jejich `Modifiers` vlastnosti.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Chcete-li přidat tlačítko, které můžete upravit dědice základního formuláře  
  
1.  Otevřít **Form1** v návrháři.  
  
2.  Na **všechny formuláře Windows** karty **nástrojů**, dvakrát klikněte na panel **tlačítko** přidáte tlačítka do formuláře. Pro nastavení pozice a změňte velikost tlačítka pomocí myši.  
  
3.  V okně Vlastnosti nastavte následující vlastnosti tlačítka:  
  
    -   Nastavte **Text** vlastnost **Say Hello**.  
  
    -   Nastavte **(název)** vlastnost **btnProtected**.  
  
    -   Nastavte**modifikátory** vlastnost **chráněné**. To umožňuje pro formuláře, které dědí **Form1** k úpravě vlastností **btnProtected**.  
  
4.  Dvakrát klikněte **Say Hello** tlačítko pro přidání obslužné rutiny události pro **klikněte na tlačítko** událostí.  
  
5.  Přidejte následující řádek kódu obslužné rutiny události:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Chcete-li přidat tlačítko, které nemůže upravit dědice základního formuláře  
  
1.  Přepnutí do návrhového zobrazení po kliknutí **Form1.vb [Design], Form1.cs [Design] nebo [Design] Form1.jsl** kartu nad editoru kódu nebo stisknutím klávesy F7.  
  
2.  Přidejte druhé tlačítko a nastavte jeho vlastnosti následujícím způsobem:  
  
    -   Nastavte **Text** vlastnost **Say Goodbye**.  
  
    -   Nastavte **(název)** vlastnost **btnPrivate**.  
  
    -   Nastavte **modifikátory** vlastnost **privátní**. To znemožňuje pro formuláře, které dědí **Form1** k úpravě vlastností **btnPrivate**.  
  
3.  Dvakrát klikněte **Say Goodbye** tlačítko pro přidání obslužné rutiny události pro **klikněte na tlačítko** událostí. Vložte následující řádek kódu do procedury události:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Z **sestavení** nabídce zvolte **sestavení knihovny BaseForm** k vytvoření knihovny tříd.  
  
     Jakmile knihovny je sestavená, můžete vytvořit nový projekt, který dědí z formuláře, který jste právě vytvořili.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Chcete-li vytvořit projekt obsahující formulář, který dědí ze základního formuláře  
  
1.  Z **souboru** nabídce zvolte **přidat** a potom **nový projekt** otevřít **přidat nový projekt** dialogové okno.  
  
2.  Vytvoření aplikace Windows Forms s názvem `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Přidat Zděděný formulář  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projekt, vyberte **přidat**a pak vyberte**nová položka**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **Windows Forms** kategorie (Pokud máte seznam kategorií) a pak vyberte **zděděné formuláře** šablony.  
  
3.  Ponechte výchozí název `Form2` a potom klikněte na tlačítko **přidat**.  
  
4.  V **výběr dědičnosti** dialogu **Form1** z **BaseFormLibrary** projektu jako formulář dědí a klikněte na tlačítko **OK** .  
  
     Tím se vytvoří na formulář v nástrojích **InheritanceTest** projekt, který je odvozen z formuláře v **BaseFormLibrary**.  
  
5.  Otevřete Zděděný formulář (**Form2**) v Návrháři poklepáním, pokud ještě není otevřený.  
  
     V návrháři, zděděné tlačítka mají symbol (![VisualBasicInheritanceSymbol – snímek obrazovky](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) v jejich horním rohu, která se dědí.  
  
6.  Vyberte **Say Hello** tlačítko a podívejte se úchyty pro změnu velikosti. Protože toto tlačítko je chráněný, dědice můžete přesunout, změnit jeho velikost, změnit titulek a provádět další úpravy.  
  
7.  Vyberte privátní **Say Goodbye** tlačítko a Všimněte si, že nemá úchyty pro změnu velikosti. Kromě toho **vlastnosti** v okně Vlastnosti tohoto tlačítka se šedě k označení, nemůže být upraven.  
  
8.  Pokud používáte jazyk Visual C#:  
  
    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1** v **InheritanceTest** projektu a klikněte na tlačítko **odstranit**. V okně se zprávou, která se zobrazí, klikněte na tlačítko **OK** potvrďte odstranění.  
  
    2.  Otevřete soubor Program.cs a změňte řádek `Application.Run(new Form1());` k `Application.Run(new Form2());`.  
  
9. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **nastavit jako spouštěný projekt**.  
  
10. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **vlastnosti**.  
  
11. V **InheritanceTest** stránky vlastností, nastavte **spouštěcí objekt** Zděděný formulář (**Form2**).  
  
12. Stisknutím klávesy F5 spusťte aplikaci a sledovat chování Zděděný formulář.  
  
## <a name="next-steps"></a>Další kroky  
 V podstatě stejným způsobem pracuje dědičnost u uživatelských ovládacích prvků. Otevřete nový projekt knihovny tříd a přidat uživatelský ovládací prvek. Základní ovládací prvky na něj umístit a kompilaci projektu. Otevřete jinou nový projekt knihovny tříd a přidejte odkaz na knihovnu zkompilované třídy. Také se pokuste přidat zděděný ovládací prvek (prostřednictvím **přidat nové položky** dialogové okno) do projektu a použití **výběr dědičnosti**. Přidat uživatelský ovládací prvek a změnit `Inherits` (`:` v jazyce Visual C#) příkaz. Další informace najdete v tématu [postupy: dědění formulářů Windows](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Dědění v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Vizuální dědění modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
