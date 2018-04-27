---
title: 'Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99ed6b7232dd80733fea3c9f36722b0722dc1525
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator
Nástupem <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku Windows Forms umožňuje vývojářům poskytnout koncovým uživatelům s jednoduché datové navigaci a manipulace s uživatelským rozhraním ve formulářích jejich vytvoření.  
  
 <xref:System.Windows.Forms.BindingNavigator> Ovládacího prvku <xref:System.Windows.Forms.ToolStrip> předkonfigurované ovládacího prvku pomocí tlačítka pro navigaci na první, poslední, další a předchozí záznam v datových sad, jakož i tlačítka pro přidání a odstranění záznamů. Přidání tlačítek do <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je snadné, protože je <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  Viz také [postupy: Přidání načíst, uložit, a tlačítka Storno do ovládacího prvku Windows Forms BindingNavigator](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Pro každé tlačítko na <xref:System.Windows.Forms.BindingNavigator> řídit, není členem příslušné skupiny <xref:System.Windows.Forms.BindingSource> komponenty, která umožňuje prostřednictvím kódu programu stejné funkce. Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> součásti, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda a tak dále. V důsledku toho povolení <xref:System.Windows.Forms.BindingNavigator> řízení přejděte záznamů dat je jednoduchý jako nastavení jeho <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost na příslušné <xref:System.Windows.Forms.BindingSource> součásti na formuláři.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Nastavit BindingNavigator – ovládací prvek  
  
1.  Přidat <xref:System.Windows.Forms.BindingSource> součást s názvem `bindingSource1` a dvě <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `textBox1` a `textBox2`.  
  
2.  Vytvoření vazby `bindingSource1` k datům a ovládací prvky textbox `bindingSource1`. Chcete-li to provést, vložte následující kód do formuláře a volání `LoadData` z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metoda zpracování událostí.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Přidat <xref:System.Windows.Forms.BindingNavigator> ovládací prvek s názvem `bindingNavigator1` do svého formuláře.  
  
4.  Nastavte <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost pro `bindingNavigator1` k `bindingSource1`. Můžete to provést pomocí návrháře nebo v kódu.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je na kompletní příklad dříve uvedených kroků.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing, System.Windows.Forms a System.Xml sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Ovládací prvek BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
