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
ms.openlocfilehash: 61239d9b547be73a14618d41feeb9aeea9f8ded6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529698"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Návod: Demonstrace vizuálního dědění
Dědičnost vizuálních prvků umožňuje zobrazíte ovládacích prvků na formuláři základní a přidejte nové ovládací prvky. V tomto návodu vytvoříte základní formulář a kompilována knihovny tříd. Bude tato knihovna tříd importovat do jiného projektu a vytvořte nový formulář, který dědí ze základní formulář. Během tohoto návodu se dozvíte, jak:  
  
-   Vytvoření projektu knihovny tříd obsahující základní formulář.  
  
-   Přidáte lze upravit tlačítko s vlastnostmi, které odvozené třídy základní formulář.  
  
-   Přidání tlačítka, které nelze změnit pomocí dědice základní formulář.  
  
-   Vytvoření projektu obsahující formulář, který dědí z `BaseForm`.  
  
 Nakonec tento návod popisuje rozdíl mezi privátním a chráněné ovládacích prvků na zděděné formuláře.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!CAUTION]
>  Ne všechny ovládací prvky podporují vizuálního dědění ze základní formulář. Ovládací prvky nepodporují podle scénáře popsaného v tomto průvodci:  
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
 Prvním krokem je vytvoření základní formulář.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Vytvoření projektu knihovny tříd obsahující základní formulář  
  
1.  Z **soubor** nabídce zvolte **nový**a potom **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  Vytvoření aplikace Windows Forms s názvem `BaseFormLibrary`.  
  
3.  K vytvoření knihovny tříd místo u standardní aplikace Windows Forms v **Průzkumníku řešení**, klikněte pravým tlačítkem myši **BaseFormLibrary** uzel projektu a potom vyberte **vlastnosti**.  
  
4.  Ve vlastnostech projektu, změňte **výstupní typ** z **aplikace Windows** k **knihovny tříd**.  
  
5.  Z **soubor** nabídce zvolte **Uložit vše** uložte projekt a soubory do výchozího umístění.  
  
 Následující dva postupy přidání tlačítka do základní formulář. K předvedení dědičnost vizuálních prvků, kterým pojmenujete tlačítka různé úrovně přístupu nastavením jejich `Modifiers` vlastnosti.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Chcete-li přidat tlačítko, které můžete upravit dědice základní formulář  
  
1.  Otevřete **Form1** v návrháři.  
  
2.  Na **všechny formuláře Windows** kartě **sada nástrojů**, dvakrát klikněte na **tlačítko** přidání tlačítka do formuláře. Umístění a změna velikosti tlačítko pomocí myši.  
  
3.  V okně vlastností nastavte následující vlastnosti tlačítka:  
  
    -   Nastavte **Text** vlastnost **Hello indikované**.  
  
    -   Nastavte **(název)** vlastnost **btnProtected**.  
  
    -   Nastavte**modifikátory** vlastnost **chráněné**. Díky tomu může pro formuláře, které dědí od **Form1** k úpravě vlastností **btnProtected**.  
  
4.  Dvakrát klikněte na **Hello indikované** tlačítko pro přidání obslužné rutiny události pro **klikněte na tlačítko** událostí.  
  
5.  Přidejte následující kód do obslužné rutiny události:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Chcete-li přidat tlačítko, které nelze změnit pomocí dědice základní formulář  
  
1.  Přepnout na zobrazení návrhu kliknutím **Form1.vb [Design], Form1.cs [Design] nebo [návrhu] Form1.jsl** kartě nad editoru kódu nebo stisknutím klávesy F7.  
  
2.  Druhý tlačítko Přidat a nastavit jeho vlastnosti následujícím způsobem:  
  
    -   Nastavte **Text** vlastnost **dát sbohem všem indikované**.  
  
    -   Nastavte **(název)** vlastnost **btnPrivate**.  
  
    -   Nastavte **modifikátory** vlastnost **privátní**. To znemožňuje pro formuláře, které dědí od **Form1** k úpravě vlastností **btnPrivate**.  
  
3.  Dvakrát klikněte **indikované dát sbohem všem** tlačítko pro přidání obslužné rutiny události pro **klikněte na** událostí. Vložte následující řádek kódu v proceduře události:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Z **sestavení** nabídce zvolte **sestavení knihovny BaseForm** k vytvoření knihovny tříd.  
  
     Po knihovny, můžete vytvořit nový projekt, který dědí z formuláře, který jste právě vytvořili.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Chcete-li vytvořit projekt obsahující formulář, který dědí ze základního formuláře  
  
1.  Z **soubor** nabídce zvolte **přidat** a potom **nový projekt** otevřete **přidat nový projekt** dialogové okno.  
  
2.  Vytvoření aplikace Windows Forms s názvem `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Chcete-li přidat zděděné formuláře  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projekt, vyberte **přidat**a potom vyberte**novou položku**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **Windows Forms** kategorie (Pokud máte seznam kategorií) a potom vyberte **zděděná formuláře** šablony.  
  
3.  Ponechte výchozí název `Form2` a pak klikněte na **přidat**.  
  
4.  V **výběr dědičnosti** dialogové okno, vyberte **Form1** z **BaseFormLibrary** projektu jako formulář dědí a klikněte na tlačítko **OK** .  
  
     Tím se vytvoří do formuláře **InheritanceTest** projekt, který je odvozen z formuláře v **BaseFormLibrary**.  
  
5.  Otevřít formulář zděděné (**Form2**) v Návrháři dvojitým kliknutím na soubor, pokud ještě není otevřené.  
  
     V Návrháři zděděné tlačítka mají symbol (![VisualBasicInheritanceSymbol – snímek obrazovky](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) v jejich horního rohu, která určuje, že zděděná.  
  
6.  Vyberte **Hello indikované** tlačítko a sledovat změny velikosti obslužné rutiny. Protože toto tlačítko je chráněn, dědice můžete přesunout ho, jeho velikost, změnit jeho popisek a provádět další úpravy.  
  
7.  Vyberte privátní **dát sbohem všem indikované** tlačítko a Všimněte si, nemá změny velikosti obslužné rutiny. Kromě toho **vlastnosti** okně Vlastnosti toto tlačítko se šedý k označení je nelze změnit.  
  
8.  Pokud používáte Visual C#:  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1** v **InheritanceTest** projektu a potom zvolte **odstranit**. V dialogovém okně se zobrazí, klikněte na **OK** potvrďte odstranění.  
  
    2.  Otevřete soubor Program.cs a změňte řádek `Application.Run(new Form1());` k `Application.Run(new Form2());`.  
  
9. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **nastavit jako spouštěný projekt**.  
  
10. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **vlastnosti**.  
  
11. V **InheritanceTest** nastavení stránek vlastností **spouštěcí objekt** být zděděné formuláře (**Form2**).  
  
12. Stisknutím klávesy F5 spusťte aplikaci a pozorovat chování zděděné formuláře.  
  
## <a name="next-steps"></a>Další kroky  
 Dědičnost pro uživatelské ovládací prvky funguje stejným způsobem. Otevřete nový projekt knihovny tříd a přidat uživatelský ovládací prvek. Umístěte základních ovládacích prvků na něm a kompilaci projektu. Otevřete jiné nového projektu knihovny tříd a přidejte odkaz na knihovnu zkompilované třídy. Navíc zkuste přidat ovládací prvek zděděné (prostřednictvím **přidat nové položky** dialogové okno) do projektu a pomocí **výběr dědičnosti**. Přidat uživatelský ovládací prvek a změňte `Inherits` (`:` v jazyce Visual C#) příkaz. Další informace najdete v tématu [postupy: dědění Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Dědění v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Vizuální dědění modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
