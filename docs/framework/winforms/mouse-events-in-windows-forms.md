---
title: Události myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 671e37c7d6dc40046d6d717d7785b03b6b545c7e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333675"
---
# <a name="mouse-events-in-windows-forms"></a>Události myši ve Windows Forms
Při zpracování vstup z myši obvykle chtít znát umístění myši ukazatele a stav tlačítka myši. Toto téma obsahuje podrobné informace o tom, jak získat tyto informace z událostí myši a vysvětluje, pořadí, ve které kliknutí myší jsou vyvolány události v ovládacích prvcích Windows Forms. Seznam a popis všech událostí myši najdete v tématu [jak funguje myši vstup ve Windows Forms](how-mouse-input-works-in-windows-forms.md).  Viz také [Přehled obslužných rutin událostí (Windows Forms)](event-handlers-overview-windows-forms.md) a [Přehled událostí (Windows Forms)](events-overview-windows-forms.md).  
  
## <a name="mouse-information"></a>Informace o myši  
 A <xref:System.Windows.Forms.MouseEventArgs> posílá obslužné rutiny událostí myši týkající se sledování pohybu myši a kliknutím na tlačítko myši. <xref:System.Windows.Forms.MouseEventArgs> poskytuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, které jsou stisknutí tlačítka myši, a určuje, zda se posunul kolečko myši. Několik událostí myši, jako jsou ty, které jednoduše upozornění při umístění ukazatele myši má zadaný nebo ponechat hranice ovládacího prvku, odeslání <xref:System.EventArgs> obslužné rutiny události s žádné další informace.  
  
 Pokud chcete zjistit aktuální stav tlačítka myši nebo na umístění ukazatele myši a chcete se vyhnout zpracování události myši, můžete použít také <xref:System.Windows.Forms.Control.MouseButtons%2A> a <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnosti <xref:System.Windows.Forms.Control> třídy. <xref:System.Windows.Forms.Control.MouseButtons%2A> Vrátí informace o tom, které jsou aktuálně stisknutí tlačítka myši. <xref:System.Windows.Forms.Control.MousePosition%2A> Vrací souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě vrácené <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Převod mezi obrazovky a klient koordinuje  
 Protože se některé informace o umístění myši v souřadnicích klienta a některé jsou v souřadnicovém systému obrazovky, budete muset změnit bod v jednom systému souřadnice. Můžete to provést jednoduše pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici na <xref:System.Windows.Forms.Control> třídy.  
  
## <a name="standard-click-event-behavior"></a>Standardní chování události klikněte na tlačítko.  
 Pokud chcete zpracovávat události ve správném pořadí kliknutí myší, je potřeba vědět pořadí, ve které kliknutím jsou vyvolány události v ovládacích prvcích Windows Forms. Po stisknutí tlačítka myši a vydány (bez ohledu na které tlačítko myši), v následujícím seznamu pro jednotlivé ovládací prvky, klikněte na všechny formuláře Windows, které vyvolávají události ve stejném pořadí. Následující seznam zobrazuje pořadí událostí vyvolaných pro klikněte na jediné tlačítko myši:  
  
1. <xref:System.Windows.Forms.Control.MouseDown> události.  
  
2. <xref:System.Windows.Forms.Control.Click> události.  
  
3. <xref:System.Windows.Forms.Control.MouseClick> události.  
  
4. <xref:System.Windows.Forms.Control.MouseUp> události.  
  
 Toto je pořadí událostí vyvolaných pro tlačítko myši dvojité kliknutí:  
  
1. <xref:System.Windows.Forms.Control.MouseDown> události.  
  
2. <xref:System.Windows.Forms.Control.Click> události.  
  
3. <xref:System.Windows.Forms.Control.MouseClick> události.  
  
4. <xref:System.Windows.Forms.Control.MouseUp> události.  
  
5. <xref:System.Windows.Forms.Control.MouseDown> události.  
  
6. <xref:System.Windows.Forms.Control.DoubleClick> události. (To se může lišit v závislosti na tom, zda má ovládací prvek dotyčný <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> na sadu bitů stylu `true`. Další informace o tom, jak nastavit <xref:System.Windows.Forms.ControlStyles> bit, najdete v článku <xref:System.Windows.Forms.Control.SetStyle%2A> metoda.)  
  
7. <xref:System.Windows.Forms.Control.MouseDoubleClick> události.  
  
8. <xref:System.Windows.Forms.Control.MouseUp> události.  
  
 Příklad kódu, který ukazuje pořadí myši klikněte na události, najdete v článku [jak: Zpracování uživatelského vstupu událostí ve Windows Forms ovládací prvky](how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Jednotlivých ovládacích prvků  
 Následující ovládací prvky není v souladu s Standardní zkratky myši klikněte na tlačítko chování události:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, a <xref:System.Windows.Forms.RadioButton> ovládacích prvků  
  
    > [!NOTE]
    >  Pro <xref:System.Windows.Forms.ComboBox> vyvolá chování události, které jsou podrobně popsané ovládací prvek, pokud uživatel klepne na pole, tlačítko, nebo na položku v seznamu.  
  
    -   Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem myši na: Žádné události kliknutí na vyvolána  
  
    -   Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Vpravo klikněte dvakrát na: Žádné události kliknutí na vyvolána  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, a <xref:System.Windows.Forms.CheckedListBox> ovládacích prvků  
  
    > [!NOTE]
    >  Chování události, které jsou podrobně popsané nastane, pokud uživatel klikne na tlačítko kdekoli v rámci těchto ovládacích prvků.  
  
    -   Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem myši na: Žádné události kliknutí na vyvolána  
  
    -   Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Vpravo klikněte dvakrát na: Žádné události kliknutí na vyvolána  
  
-   <xref:System.Windows.Forms.ListView>  – ovládací prvek  
  
    > [!NOTE]
    >  Chování události, které jsou podrobně popsané dochází, pouze když uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacího prvku. Žádné události se generují pro kliknutí na ovládací prvek někde jinde. Kromě události je popsáno dále, jsou k dispozici <xref:System.Windows.Forms.ListView.BeforeLabelEdit> a <xref:System.Windows.Forms.ListView.AfterLabelEdit> události, které mohou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
    -   Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem myši na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Vpravo klikněte dvakrát na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView>  – ovládací prvek  
  
    > [!NOTE]
    >  Chování události, které jsou podrobně popsané dochází, pouze pokud uživatel klikne na samotných položkách nebo napravo od položky <xref:System.Windows.Forms.TreeView> ovládacího prvku. Žádné události se generují pro kliknutí na ovládací prvek někde jinde. Kromě těch popsaných dále, jsou k dispozici <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, a <xref:System.Windows.Forms.TreeView.AfterLabelEdit> události, které mohou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.TreeView> ovládacího prvku .  
  
    -   Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem myši na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Vpravo klikněte dvakrát na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>Malování chování ovládacích prvků přepínání  
 Přepnout ovládací prvky, jako je například ovládací prvky odvozený od <xref:System.Windows.Forms.ButtonBase> třídy, mají následující zvláštní Malování chování v kombinaci s myši klikněte na tlačítko události:  
  
1. Uživatel stiskne tlačítko myši.  
  
2. Při stisknutí stavu Vymaluje ovládací prvek.  
  
3. <xref:System.Windows.Forms.Control.MouseDown> Událost se vyvolá.  
  
4. Uživatel uvolní tlačítko myši.  
  
5. Vymaluje ovládací prvek v vyvolanou stavu.  
  
6. <xref:System.Windows.Forms.Control.Click> Událost se vyvolá.  
  
7. <xref:System.Windows.Forms.Control.MouseClick> Událost se vyvolá.  
  
8. <xref:System.Windows.Forms.Control.MouseUp> Událost se vyvolá.  
  
    > [!NOTE]
    >  Pokud se uživatel přesune ukazatel myši mimo ovládací prvek přepínací tlačítko, zatímco je stisknuto levé tlačítko myši (jako je například hýbání myší <xref:System.Windows.Forms.Button> ovládací prvek je stisknutí), bude malovat vyvolanou ovládacím prvku přepínací tlačítko stavu a pouze <xref:System.Windows.Forms.Control.MouseUp> dojde k události. <xref:System.Windows.Forms.Control.Click> Nebo <xref:System.Windows.Forms.Control.MouseClick> nebude v této situaci dojde k událostem.  
  
## <a name="see-also"></a>Viz také:

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
