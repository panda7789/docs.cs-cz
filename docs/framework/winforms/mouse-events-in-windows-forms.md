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
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949915"
---
# <a name="mouse-events-in-windows-forms"></a>Události myši ve Windows Forms

Při zpracování vstupu myši obvykle chcete znát polohu ukazatele myši a stavu tlačítek myši. Toto téma obsahuje podrobné informace o tom, jak tyto informace z událostí myši získat a vysvětluje pořadí, ve kterém jsou události kliknutí myší vyvolány v ovládacích prvcích model Windows Forms. Seznam a popis všech událostí myši najdete [v tématu Jak funguje vstup myši v model Windows Forms](how-mouse-input-works-in-windows-forms.md).  Viz také přehled [obslužných rutin událostí (model Windows Forms)](event-handlers-overview-windows-forms.md) a [přehled událostí (model Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informace o myši

A <xref:System.Windows.Forms.MouseEventArgs> se pošle obslužným rutinám událostí myši souvisejících s kliknutím na tlačítko myši a sledováním pohybu myši. <xref:System.Windows.Forms.MouseEventArgs>obsahuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, stisknutých tlačítek myši a o tom, zda bylo kolečko myši posunuto. Několik událostí myši, jako jsou například ty, které jednoduše upozorňují, když ukazatel myši zadáte nebo opustí hranice ovládacího prvku, pošle <xref:System.EventArgs> obslužné rutině události žádné další informace.

Chcete-li znát aktuální stav tlačítek myši nebo umístění ukazatele myši a chcete se vyhnout manipulaci s událostí myši, můžete také použít <xref:System.Windows.Forms.Control.MouseButtons%2A> vlastnosti <xref:System.Windows.Forms.Control> a <xref:System.Windows.Forms.Control.MousePosition%2A> třídy. <xref:System.Windows.Forms.Control.MouseButtons%2A>Vrátí informace o tom, která tlačítka myši jsou právě stisknutá. Vrátí souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě <xref:System.Windows.Forms.Cursor.Position%2A>vrácené hodnotou. <xref:System.Windows.Forms.Control.MousePosition%2A>

## <a name="converting-between-screen-and-client-coordinates"></a>Převod mezi souřadnicemi obrazovky a klienta

Vzhledem k tomu, že některé informace o umístění myši jsou v souřadnicích klienta a některé jsou v souřadnicích obrazovky, možná budete muset převést bod z jednoho systému souřadnic na druhý. To lze provést snadno pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> metod a <xref:System.Windows.Forms.Control.PointToScreen%2A> dostupných ve <xref:System.Windows.Forms.Control> třídě.

## <a name="standard-click-event-behavior"></a>Standardní chování události kliknutí

Pokud chcete zpracovávat události kliknutí myší ve správném pořadí, musíte znát pořadí, ve kterém jsou události kliknutí vyvolány v ovládacích prvcích model Windows Forms. Všechny model Windows Forms ovládací prvky vyvolávají události Click ve stejném pořadí při stisknutí a uvolnění tlačítka myši (bez ohledu na to, které tlačítko myši), s výjimkou těch, které jsou uvedeny v následujícím seznamu pro jednotlivé ovládací prvky. Následující seznam zobrazuje pořadí událostí vyvolaných jedním kliknutím myši na tlačítko:

1. <xref:System.Windows.Forms.Control.MouseDown>událostí.

2. <xref:System.Windows.Forms.Control.Click>událostí.

3. <xref:System.Windows.Forms.Control.MouseClick>událostí.

4. <xref:System.Windows.Forms.Control.MouseUp>událostí.

Následuje pořadí událostí vyvolaných pro dvojité kliknutí myší:

1. <xref:System.Windows.Forms.Control.MouseDown>událostí.

2. <xref:System.Windows.Forms.Control.Click>událostí.

3. <xref:System.Windows.Forms.Control.MouseClick>událostí.

4. <xref:System.Windows.Forms.Control.MouseUp>událostí.

5. <xref:System.Windows.Forms.Control.MouseDown>událostí.

6. <xref:System.Windows.Forms.Control.DoubleClick>událostí. (To se může lišit v závislosti na tom, zda má <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> ovládací prvek nastaven bit stylu na. `true` Další informace o nastavení <xref:System.Windows.Forms.ControlStyles> bitu <xref:System.Windows.Forms.Control.SetStyle%2A> naleznete v metodě.)

7. <xref:System.Windows.Forms.Control.MouseDoubleClick>událostí.

8. <xref:System.Windows.Forms.Control.MouseUp>událostí.

Příklad kódu, který ukazuje pořadí událostí kliknutí myší, naleznete v tématu [How to: Zpracování událostí vstupu uživatele v ovládacích prvcích](how-to-handle-user-input-events-in-windows-forms-controls.md)model Windows Forms.

### <a name="individual-controls"></a>Jednotlivé ovládací prvky

Následující ovládací prvky neodpovídají standardnímu chování události kliknutí myší:

- <xref:System.Windows.Forms.Button>ovládací <xref:System.Windows.Forms.CheckBox>prvky <xref:System.Windows.Forms.ComboBox>,, <xref:System.Windows.Forms.RadioButton> a

  > [!NOTE]
  > V případě <xref:System.Windows.Forms.ComboBox> ovládacího prvku se k chování události podrobná později dojde, když uživatel klikne na pole upravit, tlačítko nebo na položku v seznamu.

  - Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte pravým tlačítkem myši: Nebyly vyvolány žádné události kliknutí.

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte dvakrát na tlačítko: Nebyly vyvolány žádné události kliknutí.

- <xref:System.Windows.Forms.TextBox>ovládací <xref:System.Windows.Forms.RichTextBox>prvky <xref:System.Windows.Forms.ListBox>, ,<xref:System.Windows.Forms.MaskedTextBox>, a<xref:System.Windows.Forms.CheckedListBox>

  > [!NOTE]
  > K chování události později dojde, když uživatel klikne kamkoli v rámci těchto ovládacích prvků.

  - Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte pravým tlačítkem myši: Nebyly vyvolány žádné události kliknutí.

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Klikněte dvakrát na tlačítko: Nebyly vyvolány žádné události kliknutí.

- <xref:System.Windows.Forms.ListView>nad

  > [!NOTE]
  > K chování události později dochází pouze v případě, že uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacím prvku. Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události. Kromě událostí popsaných dále jsou <xref:System.Windows.Forms.ListView.BeforeLabelEdit> k dispozici události a <xref:System.Windows.Forms.ListView.AfterLabelEdit> , které vás mohou zajímat, pokud chcete použít ověřování s <xref:System.Windows.Forms.ListView> ovládacím prvkem.

  - Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte pravým <xref:System.Windows.Forms.Control.Click>tlačítkem myši:,<xref:System.Windows.Forms.Control.MouseClick>

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

- <xref:System.Windows.Forms.TreeView>nad

  > [!NOTE]
  > K chování události později dochází pouze v případě, že uživatel klikne na samotné položky nebo napravo od položek v <xref:System.Windows.Forms.TreeView> ovládacím prvku. Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události. Kromě těch, které jsou <xref:System.Windows.Forms.TreeView.BeforeCheck>popsány později, existují <xref:System.Windows.Forms.TreeView.BeforeSelect> <xref:System.Windows.Forms.TreeView.AfterCheck> <xref:System.Windows.Forms.TreeView.AfterLabelEdit> <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> události,<xref:System.Windows.Forms.TreeView.AfterSelect>,,, a, které vás mohou zajímat, pokud chcete použít ověřování s ovládacímprvkem<xref:System.Windows.Forms.TreeView> .

  - Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte pravým <xref:System.Windows.Forms.Control.Click>tlačítkem myši:,<xref:System.Windows.Forms.Control.MouseClick>

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Chování při malování pro přepínací ovládací prvky

Přepínací ovládací prvky, jako jsou například ovládací prvky odvozené <xref:System.Windows.Forms.ButtonBase> od třídy, mají následující chování při malování v kombinaci s událostmi kliknutí myší:

1. Uživatel stiskne tlačítko myši.

2. Ovládací prvky vykreslí ve stisknutém stavu.

3. <xref:System.Windows.Forms.Control.MouseDown> Událost je vyvolána.

4. Uživatel uvolní tlačítko myši.

5. Ovládací prvky se vykreslí do vystouplého stavu.

6. <xref:System.Windows.Forms.Control.Click> Událost je vyvolána.

7. <xref:System.Windows.Forms.Control.MouseClick> Událost je vyvolána.

8. <xref:System.Windows.Forms.Control.MouseUp> Událost je vyvolána.

    > [!NOTE]
    > Pokud uživatel přesune ukazatel myši na ovládací prvek přepínacího tlačítka, když je tlačítko myši vypnuté (například přesunutí myši <xref:System.Windows.Forms.Button> nad ovládací prvek během jeho stisknutí), ovládací prvek přepínacího tlačítka se vykreslí ve vystouplém stavu a dojde k výskytu <xref:System.Windows.Forms.Control.MouseUp> pouze události. Události <xref:System.Windows.Forms.Control.Click> nebo<xref:System.Windows.Forms.Control.MouseClick> se v této situaci neobjeví.

## <a name="see-also"></a>Viz také:

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
