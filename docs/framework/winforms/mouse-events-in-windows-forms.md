---
title: "Události myši ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5bde1c1045849fe5507081171711d5a00e99b0b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-events-in-windows-forms"></a>Události myši ve Windows Forms
Pokud zpracováváte vstup z myši, obvykle chcete znát umístění myši ukazatel a stav tlačítka myši. Toto téma obsahuje podrobné informace o tom, jak získat tyto informace z událostí myši a vysvětluje pořadí, ve které klikněte na tlačítko myši události jsou vyvolány v ovládacích prvcích Windows Forms. Seznam a popis všech událostí myši najdete v tématu [jak funguje vstup myši Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  Viz také [Přehled obslužných rutin událostí (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Přehled událostí (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))  
  
## <a name="mouse-information"></a>Informace o myši  
 A <xref:System.Windows.Forms.MouseEventArgs> posílá obslužných rutin událostí myši související s kliknutím na tlačítko myši a sledováním pohybů myši. <xref:System.Windows.Forms.MouseEventArgs>poskytuje informace o aktuálním stavu myš, včetně umístění ukazatele myši v souřadnicích klienta, které jsou stisknutí tlačítka myši a zda má přešli kolečko myši. Několik myši události, jako jsou ty, které jednoduše Upozornit při zpracování má ukazatel myši zadali nebo ponecháno hranice ovládacího prvku, odeslání <xref:System.EventArgs> k obslužné rutině událostí s žádné další informace.  
  
 Pokud chcete zjistit aktuální stav tlačítka myši nebo umístění ukazatele myši a budete chtít vyhnout zpracování události myši, můžete použít také <xref:System.Windows.Forms.Control.MouseButtons%2A> a <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnosti <xref:System.Windows.Forms.Control> třídy. <xref:System.Windows.Forms.Control.MouseButtons%2A>vrací informace o tom, které jsou aktuálně stisknutí tlačítka myši. <xref:System.Windows.Forms.Control.MousePosition%2A> Vrátí souřadnice obrazovky ukazatele myši a je ekvivalentem hodnoty vrácené <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Převod mezi obrazovky a klienta koordinuje  
 Protože některé informace o umístění myši v souřadnicích klienta a některé v souřadnice obrazovky, musíte převést bod souřadnicový systém. Můžete k tomu snadno pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici na <xref:System.Windows.Forms.Control> třídy.  
  
## <a name="standard-click-event-behavior"></a>Standardní chování události, klikněte na tlačítko  
 Pokud chcete zpracovávat myši klikněte na události ve správném pořadí, je nutné znát pořadí, ve které klikněte na tlačítko akce jsou vyvolány ve Windows Forms – ovládací prvky. Až tlačítko myši po stisknutí a uvolnění (bez ohledu na které tlačítko myši), s výjimkou uvedeno v následujícím seznamu u jednotlivých ovládacích prvků, klikněte na všechny formuláře Windows, které vyvolávají události ve stejném pořadí. V následujícím seznamu jsou pořadí událostí vyvolaných pro klikněte na tlačítko myši v jednom:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown>událost.  
  
2.  <xref:System.Windows.Forms.Control.Click>událost.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick>událost.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp>událost.  
  
 Toto je pořadí událostí vyvolaných pro tlačítko myši dvojité kliknutí:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown>událost.  
  
2.  <xref:System.Windows.Forms.Control.Click>událost.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick>událost.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp>událost.  
  
5.  <xref:System.Windows.Forms.Control.MouseDown>událost.  
  
6.  <xref:System.Windows.Forms.Control.DoubleClick>událost. (To se může lišit, v závislosti na tom, jestli se má ovládací prvek v <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> k nastaven bit stylu `true`. Další informace o tom, jak nastavit <xref:System.Windows.Forms.ControlStyles> bit, najdete v článku <xref:System.Windows.Forms.Control.SetStyle%2A> metoda.)  
  
7.  <xref:System.Windows.Forms.Control.MouseDoubleClick>událost.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp>událost.  
  
 Příklad kódu, který ukazuje pořadí myši klikněte na události, najdete v části [postupy: zpracování událostí vstup uživatele v ovládacích prvcích Windows Forms](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Jednotlivých ovládacích prvků  
 Ovládací prvky nejsou v souladu s standardní myši klikněte na tlačítko chování události:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, a <xref:System.Windows.Forms.RadioButton> ovládací prvky  
  
    > [!NOTE]
    >  Pro <xref:System.Windows.Forms.ComboBox> dojde chování události, které jsou podrobně popsané ovládací prvek, pokud uživatel klikne na pole upravit tlačítko, nebo na položku v seznamu.  
  
    -   Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem: žádné události kliknutí na vyvolána  
  
    -   Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Právo dvakrát klikněte na: žádné události kliknutí na vyvolána  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, a <xref:System.Windows.Forms.CheckedListBox> ovládací prvky  
  
    > [!NOTE]
    >  Chování události, které jsou podrobně popsané nastane, když uživatel klikne kdekoli v rámci těchto ovládacích prvků.  
  
    -   Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem: žádné události kliknutí na vyvolána  
  
    -   Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Právo dvakrát klikněte na: žádné události kliknutí na vyvolána  
  
-   <xref:System.Windows.Forms.ListView>ovládací prvek  
  
    > [!NOTE]
    >  Podrobně popsané chování události dojde, pouze když uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacího prvku. Žádné události jsou vyvolány pro klikne na ovládací prvek někde jinde. Kromě události popsané dál, jsou k dispozici <xref:System.Windows.Forms.ListView.BeforeLabelEdit> a <xref:System.Windows.Forms.ListView.AfterLabelEdit> události, které můžou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
    -   Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Právo dvakrát klikněte na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView>ovládací prvek  
  
    > [!NOTE]
    >  Podrobně popsané chování události dojde, pouze když uživatel klikne na položky sami nebo napravo od položky v <xref:System.Windows.Forms.TreeView> ovládacího prvku. Žádné události jsou vyvolány pro klikne na ovládací prvek někde jinde. Kromě těch, které popsané dál, jsou k dispozici <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, a <xref:System.Windows.Forms.TreeView.AfterLabelEdit> události, které můžou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.TreeView> ovládací prvek .  
  
    -   Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Klikněte pravým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Právo dvakrát klikněte na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>Vykreslování chování ovládacích prvků přepínání  
 Ovládací prvky, jako je například odvozování z ovládacích prvků přepínání <xref:System.Windows.Forms.ButtonBase> třídy, máte následující chování rozlišovací malování v kombinaci s myši, klikněte na události:  
  
1.  Uživatel tlačítka myši.  
  
2.  Ovládací prvek vybarví ve stavu při stisknutí tlačítka.  
  
3.  <xref:System.Windows.Forms.Control.MouseDown> Událost se vyvolá.  
  
4.  Uživatel uvolní tlačítko myši.  
  
5.  Ovládací prvek vybarví v vyvolané stavu.  
  
6.  <xref:System.Windows.Forms.Control.Click> Událost se vyvolá.  
  
7.  <xref:System.Windows.Forms.Control.MouseClick> Událost se vyvolá.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> Událost se vyvolá.  
  
    > [!NOTE]
    >  Pokud se uživatel přesune ukazatel mimo ovládací prvek přepínač, zatímco je tlačítko myši směrem dolů (například pohyb myši <xref:System.Windows.Forms.Button> řízení při stisknutí), bude malovat vyvolané ovládací prvek přepínač stavu a to pouze <xref:System.Windows.Forms.Control.MouseUp> dojde k události. <xref:System.Windows.Forms.Control.Click> Nebo <xref:System.Windows.Forms.Control.MouseClick> nebude v této situaci dojde k událostem.  
  
## <a name="see-also"></a>Viz také  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
