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
ms.openlocfilehash: a61f4eedde611cfb7598d55465103924516e06c6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834599"
---
# <a name="mouse-events-in-windows-forms"></a>Události myši ve Windows Forms

Při zpracování vstupu myši obvykle chcete znát polohu ukazatele myši a stavu tlačítek myši. Toto téma obsahuje podrobné informace o tom, jak tyto informace z událostí myši získat a vysvětluje pořadí, ve kterém jsou události kliknutí myší vyvolány v ovládacích prvcích model Windows Forms. Seznam a popis všech událostí myši najdete [v tématu Jak funguje vstup myši v model Windows Forms](how-mouse-input-works-in-windows-forms.md).  Viz také přehled [obslužných rutin událostí (model Windows Forms)](event-handlers-overview-windows-forms.md) a [přehled událostí (model Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informace o myši

@No__t-0 se pošle obslužným rutinám událostí myši souvisejících s kliknutím na tlačítko myši a sledováním pohybu myši. <xref:System.Windows.Forms.MouseEventArgs> poskytuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, vylisovaných tlačítek myši a o tom, zda kolečko myši bylo posunuto. Několik událostí myši, například ty, které jednoduše upozorňují na zadání nebo levé hranice ovládacího prvku, odesílají <xref:System.EventArgs> do obslužné rutiny události bez dalších informací.

Pokud chcete zjistit aktuální stav tlačítek myši nebo umístění ukazatele myši a chcete se vyhnout manipulaci s událostí myši, můžete použít také vlastnosti <xref:System.Windows.Forms.Control.MouseButtons%2A> a <xref:System.Windows.Forms.Control.MousePosition%2A> třídy <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.MouseButtons%2A> vrátí informace o tom, která tlačítka myši jsou právě stisknutá. @No__t-0 vrátí souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě vrácené <xref:System.Windows.Forms.Cursor.Position%2A>.

## <a name="converting-between-screen-and-client-coordinates"></a>Převod mezi souřadnicemi obrazovky a klienta

Vzhledem k tomu, že některé informace o umístění myši jsou v souřadnicích klienta a některé jsou v souřadnicích obrazovky, možná budete muset převést bod z jednoho systému souřadnic na druhý. To lze provést snadno pomocí metod @no__t 0 a <xref:System.Windows.Forms.Control.PointToScreen%2A> dostupných ve třídě <xref:System.Windows.Forms.Control>.

## <a name="standard-click-event-behavior"></a>Standardní chování události kliknutí

Pokud chcete zpracovávat události kliknutí myší ve správném pořadí, musíte znát pořadí, ve kterém jsou události kliknutí vyvolány v ovládacích prvcích model Windows Forms. Všechny model Windows Forms ovládací prvky vyvolávají události Click ve stejném pořadí při stisknutí a uvolnění tlačítka myši (bez ohledu na to, které tlačítko myši), s výjimkou těch, které jsou uvedeny v následujícím seznamu pro jednotlivé ovládací prvky. Následující seznam zobrazuje pořadí událostí vyvolaných jedním kliknutím myši na tlačítko:

1. událost <xref:System.Windows.Forms.Control.MouseDown>

2. událost <xref:System.Windows.Forms.Control.Click>

3. událost <xref:System.Windows.Forms.Control.MouseClick>

4. událost <xref:System.Windows.Forms.Control.MouseUp>

Následuje pořadí událostí vyvolaných pro dvojité kliknutí myší:

1. událost <xref:System.Windows.Forms.Control.MouseDown>

2. událost <xref:System.Windows.Forms.Control.Click>

3. událost <xref:System.Windows.Forms.Control.MouseClick>

4. událost <xref:System.Windows.Forms.Control.MouseUp>

5. událost <xref:System.Windows.Forms.Control.MouseDown>

6. událost <xref:System.Windows.Forms.Control.DoubleClick> (To se může lišit v závislosti na tom, jestli má daný ovládací prvek nastaven bit stylu <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> na `true`. Další informace o tom, jak nastavit bit <xref:System.Windows.Forms.ControlStyles>, naleznete v metodě <xref:System.Windows.Forms.Control.SetStyle%2A>.)

7. událost <xref:System.Windows.Forms.Control.MouseDoubleClick>

8. událost <xref:System.Windows.Forms.Control.MouseUp>

Příklad kódu, který ukazuje pořadí událostí kliknutí myší, naleznete v tématu [How to: Handler User Input events in model Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).

### <a name="individual-controls"></a>Jednotlivé ovládací prvky

Následující ovládací prvky neodpovídají standardnímu chování události kliknutí myší:

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > V případě ovládacího prvku <xref:System.Windows.Forms.ComboBox> dojde k podrobnému chování události, pokud uživatel klikne na pole upravit, tlačítko nebo na položku v seznamu.

  - Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknutí pravým tlačítkem: neaktivována událost kliknutí na události

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Dvakrát klikněte pravým tlačítkem myši na událost žádné události kliknutí.

- <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> a <xref:System.Windows.Forms.CheckedListBox> ovládací prvky

  > [!NOTE]
  > K chování události později dojde, když uživatel klikne kamkoli v rámci těchto ovládacích prvků.

  - Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknutí pravým tlačítkem: neaktivována událost kliknutí na události

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>.

  - Dvakrát klikněte pravým tlačítkem myši na událost žádné události kliknutí.

- ovládací prvek <xref:System.Windows.Forms.ListView>

  > [!NOTE]
  > K chování události později dojde pouze v případě, že uživatel klikne na položky v ovládacím prvku <xref:System.Windows.Forms.ListView>. Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události. Kromě událostí popsaných dále existují události <xref:System.Windows.Forms.ListView.BeforeLabelEdit> a <xref:System.Windows.Forms.ListView.AfterLabelEdit>, které vás mohou zajímat, pokud chcete použít ověřování pomocí ovládacího prvku <xref:System.Windows.Forms.ListView>.

  - Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte pravým tlačítkem na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>.

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

- ovládací prvek <xref:System.Windows.Forms.TreeView>

  > [!NOTE]
  > K chování události později dochází pouze v případě, že uživatel klikne na samotné položky nebo napravo od položek v ovládacím prvku <xref:System.Windows.Forms.TreeView>. Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události. Kromě těch popsaných později jsou k dispozici <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> a <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, které vás mohou zajímat, pokud chcete použít ověřování s ovládacím prvkem <xref:System.Windows.Forms.TreeView>.

  - Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Klikněte pravým tlačítkem na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>.

  - Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Chování při malování pro přepínací ovládací prvky

Přepínací ovládací prvky, jako jsou například ovládací prvky odvozené od třídy <xref:System.Windows.Forms.ButtonBase>, mají následující chování při rozkreslení v kombinaci s událostmi kliknutí myší:

1. Uživatel stiskne tlačítko myši.

2. Ovládací prvky vykreslí ve stisknutém stavu.

3. Vyvolá se událost <xref:System.Windows.Forms.Control.MouseDown>.

4. Uživatel uvolní tlačítko myši.

5. Ovládací prvky se vykreslí do vystouplého stavu.

6. Vyvolá se událost <xref:System.Windows.Forms.Control.Click>.

7. Vyvolá se událost <xref:System.Windows.Forms.Control.MouseClick>.

8. Vyvolá se událost <xref:System.Windows.Forms.Control.MouseUp>.

    > [!NOTE]
    > Pokud uživatel přesune ukazatel myši na ovládací prvek přepínacího tlačítka, když je stisknuto tlačítko myši (například přesunutím ukazatele myši nad ovládací prvek <xref:System.Windows.Forms.Button>, když je spuštěný), přepínací ovládací prvek se vykreslí do vystouplého stavu a dojde k pouze události <xref:System.Windows.Forms.Control.MouseUp>. V této situaci se neobjeví události <xref:System.Windows.Forms.Control.Click> nebo <xref:System.Windows.Forms.Control.MouseClick>.

## <a name="see-also"></a>Viz také:

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
