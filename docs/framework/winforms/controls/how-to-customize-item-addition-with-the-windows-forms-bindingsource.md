---
title: 'Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 0a2f8491d0f027ca834257e2ec3a08d0b8bdb7ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054312"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource
Při použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby ovládacího prvku Windows Forms ke zdroji dat bude možná potřeba k přizpůsobení vytvoření nové položky. <xref:System.Windows.Forms.BindingSource> Komponenta odešle toto jednoduché tím, že poskytuje <xref:System.Windows.Forms.BindingSource.AddingNew> událost, která se obvykle vyvolá, když je potřeba vytvořit novou položku vázaného ovládacího prvku. Vaše obslužná rutina události můžete zadat jakýkoli vlastní chování, je třeba (např. volání metody na webovou službu nebo získání nového objektu z objektu pro vytváření tříd).  
  
> [!NOTE]
>  Při přidání položky pomocí manipulace <xref:System.Windows.Forms.BindingSource.AddingNew> události, přidání nelze zrušit.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládací prvek na objekt pro vytváření tříd pomocí <xref:System.Windows.Forms.BindingSource> komponenty. Pokud uživatel klikne <xref:System.Windows.Forms.DataGridView> ovládacího prvku nový řádek, <xref:System.Windows.Forms.BindingSource.AddingNew> událost se vyvolá. Vytvoří novou obslužnou rutinu události `DemoCustomer` objektu, který je přiřazen <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> vlastnost. To způsobí, že nový `DemoCustomer` objektu, který chcete přidat do <xref:System.Windows.Forms.BindingSource> seznamu komponenty a který se má zobrazit na novém řádku z <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
