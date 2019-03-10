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
ms.openlocfilehash: 3d67da6330cdceaf975c62b474c1580b853a2676
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711895"
---
# <a name="how-to-arrange-mdi-child-forms"></a>Postupy: Uspořádání podřízených formulářů MDI
Aplikace se mají často, příkazy nabídky pro akce, například dlaždice, Cascade a uspořádat, které řídit rozložení otevřít podřízené formuláře MDI. Můžete použít <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody s jedním z <xref:System.Windows.Forms.MdiLayout> hodnot výčtu, chcete-li uspořádat podřízené formuláře MDI na nadřazený formulář.  
  
 <xref:System.Windows.Forms.MdiLayout> Hodnot výčtu zobrazit podřízené formuláře jako CSS, protože vodorovně nebo svisle vedle sebe, nebo jako podřízené formuláře ikony uspořádané podél dolní části formuláře MDI. Tyto hodnoty mají stejný účinek jako příkazy Windows **sebe**, **zobrazit okna vedle sebe**, **zobrazit okna skládaný**, a **zobrazení plochy** v uvedeném pořadí.  
  
 Tyto metody se často používají jako obslužné rutiny událostí, které jsou volány položku nabídky <xref:System.Windows.Forms.Control.Click> událostí. Tímto způsobem může mít položku nabídky s textem "Cascade Windows" požadovaný účinek na podřízených oken MDI.  
  
### <a name="to-arrange-child-forms"></a>Chcete-li uspořádat podřízené formuláře  
  
1.  V metodě, použijte <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody nastavte <xref:System.Windows.Forms.MdiLayout> výčtu pro nadřazený formulář MDI. V následujícím příkladu <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> hodnotu výčtu pro okny podřízenými nadřazený formulář MDI (`Form1`). Výčet se používá v kódu během obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost **Cascade Windows** položky nabídky.  
  
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
    >  Můžete také uspořádat windows a uspořádáním windows jako ikony tak, že změníte <xref:System.Windows.Forms.MdiLayout> použít hodnotu výčtu.  
  
2.  Pokud používáte Visual C#, umístěte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
