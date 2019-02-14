---
title: 'Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator'
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
ms.openlocfilehash: ac4470e8570d82bfd35b8da5e5a087f591ccccad
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261295"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator
Nástup <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku Windows Forms vývojářům umožňuje poskytovat koncovým uživatelům s jednoduchou datovou navigaci a manipulaci s uživatelským rozhraním ve formulářích vytvářejí.  
  
 <xref:System.Windows.Forms.BindingNavigator> Je ovládací prvek <xref:System.Windows.Forms.ToolStrip> předkonfigurované ovládacím prvkem tlačítka pro přechod na první, poslední, další a předchozí záznam v datové sady, jakož i tlačítka můžete přidávat a odstraňovat záznamy. Přidání tlačítek do <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je snadné, protože se jedná <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Příklady najdete v tématu [jak: Přidat načíst, uložit, a tlačítka Storno pro Windows Forms BindingNavigator – ovládací prvek](load-save-and-cancel-bindingnavigator.md).  
  
 Pro každé tlačítko na <xref:System.Windows.Forms.BindingNavigator> řídit, neexistuje odpovídající člen <xref:System.Windows.Forms.BindingSource> komponenta, která umožňuje programově stejné funkce. Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metody a tak dále. V důsledku toho povolení <xref:System.Windows.Forms.BindingNavigator> ovládací prvek pro procházení záznamů dat je jednoduše nastavení jeho <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnosti na příslušné <xref:System.Windows.Forms.BindingSource> komponenty ve formuláři.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>K nastavení ovládacího prvku BindingNavigator  
  
1.  Přidat <xref:System.Windows.Forms.BindingSource> součást s názvem `bindingSource1` a dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `textBox1` a `textBox2`.  
  
2.  Vytvoření vazby `bindingSource1` k datům a ovládací prvky textbox `bindingSource1`. Chcete-li to provést, vložte následující kód do formuláře a volání `LoadData` z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metody zpracování událostí.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Přidat <xref:System.Windows.Forms.BindingNavigator> ovládací prvek s názvem `bindingNavigator1` do formuláře.  
  
4.  Nastavte <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost `bindingNavigator1` k `bindingSource1`. Můžete to provést pomocí návrháře nebo v kódu.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je kompletní příklad pro kroků uvedených dříve v tomto.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Drawing, System.Windows.Forms a System.Xml.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.BindingNavigator>
- [Ovládací prvek BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
- [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
