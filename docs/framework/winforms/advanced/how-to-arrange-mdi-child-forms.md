---
title: 'Postupy: Uspořádání podřízených formulářů MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955107"
---
# <a name="how-to-arrange-mdi-child-forms"></a>Postupy: Uspořádání podřízených formulářů MDI
Aplikace budou často obsahovat příkazy nabídky pro akce, jako je například dlaždice, kaskády a uspořádání, které řídí rozložení otevřených podřízených formulářů MDI. Můžete použít <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodu s jednou <xref:System.Windows.Forms.MdiLayout> z hodnot výčtu pro změnu uspořádání podřízených formulářů v nadřazeném formuláři MDI.  
  
 Hodnoty <xref:System.Windows.Forms.MdiLayout> výčtu zobrazují podřízené formuláře jako kaskádové, jak vodorovně nebo svisle vedle sebe, nebo jako ikony podřízeného formuláře uspořádané podél dolní části formuláře MDI. Tyto hodnoty mají stejný účinek jako příkazy Windows na sebe, zobrazují okna **vedle**sebe, **zobrazují okna skládané**a **zobrazují plochu**, v uvedeném pořadí.  
  
 Tyto metody jsou často používány jako obslužné rutiny událostí volané <xref:System.Windows.Forms.Control.Click> událostmi položky nabídky. Tímto způsobem může mít položka nabídky s textem "kaskádová okna" v podřízených oknech MDI požadovaný vliv.  
  
### <a name="to-arrange-child-forms"></a>Uspořádání podřízených formulářů  
  
1. V metodě použijte <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodu k <xref:System.Windows.Forms.MdiLayout> nastavení výčtu nadřazeného formuláře MDI. V následujícím příkladu je použita <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> hodnota výčtu pro podřízená okna nadřazeného formuláře MDI (`Form1`). Výčet se používá v kódu během obslužné rutiny události pro <xref:System.Windows.Forms.Control.Click> událost položky nabídky oken na **sebe** .  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    > Můžete také uspořádat okna a uspořádat okna jako ikony změnou <xref:System.Windows.Forms.MdiLayout> použité hodnoty výčtu.  
  
2. Pokud používáte vizuál C#, vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytvoření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytvořit podřízené formuláře MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Zjistit aktivní podřízenou položku MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odeslat data do aktivního podřízeného rozhraní MDI](how-to-send-data-to-the-active-mdi-child.md)
