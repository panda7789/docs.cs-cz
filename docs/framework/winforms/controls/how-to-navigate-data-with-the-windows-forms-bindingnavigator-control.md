---
title: Navigace v datech pomocí ovládacího prvku BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736010"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator
Nástupem ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> v model Windows Forms umožňuje vývojářům poskytnout koncovým uživatelům jednoduchou navigaci v datech a manipulaci s uživatelským rozhraním formulářů, které vytvoří.  
  
 <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je <xref:System.Windows.Forms.ToolStrip> ovládací prvek s tlačítky předem nakonfigurovanými pro navigaci na první, poslední, další a předchozí záznam v sadě dat a také na tlačítka pro přidávání a odstraňování záznamů. Přidávání tlačítek do ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> je snadné, protože se jedná o ovládací prvek <xref:System.Windows.Forms.ToolStrip>. Příklady naleznete v tématu [Postupy: Přidání tlačítek Load, Save a Cancel do ovládacího prvku BindingNavigator model Windows Forms](load-save-and-cancel-bindingnavigator.md).  
  
 Pro každé tlačítko ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> existuje odpovídající člen <xref:System.Windows.Forms.BindingSource> komponenty, který programově umožňuje stejné funkce. Například tlačítko <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> odpovídá metodě <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko, které odpovídá metodě <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, a tak dále. Výsledkem je, že povolení ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> pro navigaci datových záznamů je jednoduché jako nastavení vlastnosti <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> na příslušnou <xref:System.Windows.Forms.BindingSource> komponentu na formuláři.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Nastavení ovládacího prvku BindingNavigator  
  
1. Přidejte komponentu <xref:System.Windows.Forms.BindingSource> s názvem `bindingSource1` a dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `textBox1` a `textBox2`.  
  
2. Navažte `bindingSource1` na data a ovládací prvky TextBox `bindingSource1`. Chcete-li to provést, vložte do formuláře následující kód a zavolejte `LoadData` z konstruktoru formuláře nebo metody zpracování událostí <xref:System.Windows.Forms.Form.Load>.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Do formuláře přidejte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> s názvem `bindingNavigator1`.  
  
4. Pro `bindingNavigator1` `bindingSource1`nastavte vlastnost <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>. Můžete to provést pomocí návrháře nebo v kódu.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je kompletní příklad pro výše uvedené kroky.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing, System. Windows. Forms a System. XML.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.BindingNavigator>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
