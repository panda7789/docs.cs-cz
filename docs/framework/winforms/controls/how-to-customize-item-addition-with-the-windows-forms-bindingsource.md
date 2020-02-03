---
title: Přizpůsobení přidání položky pomocí komponenty BindingSource
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
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738313"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource
Použijete-li <xref:System.Windows.Forms.BindingSource> komponentu k navázání ovládacího prvku model Windows Forms na zdroj dat, může být nutné pro přizpůsobení vytváření nových položek. Komponenta <xref:System.Windows.Forms.BindingSource> to dělá tak, že poskytuje událost <xref:System.Windows.Forms.BindingSource.AddingNew>, která je obvykle vyvolána, když ovládací prvek musí vytvořit novou položku. Vaše obslužná rutina události může poskytnout jakékoli vlastní chování (například volání metody webové služby nebo získání nového objektu z továrny tříd).  
  
> [!NOTE]
> Při přidání položky pomocí zpracování události <xref:System.Windows.Forms.BindingSource.AddingNew> nelze sčítání zrušit.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> s objektem pro vytváření tříd pomocí komponenty <xref:System.Windows.Forms.BindingSource>. Když uživatel klikne na nový řádek ovládacího prvku <xref:System.Windows.Forms.DataGridView>, vyvolá se událost <xref:System.Windows.Forms.BindingSource.AddingNew>. Obslužná rutina události vytvoří nový objekt `DemoCustomer`, který je přiřazen vlastnosti <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType>. Tím dojde k přidání nového objektu `DemoCustomer` do seznamu <xref:System.Windows.Forms.BindingSource> součásti a jeho zobrazení na novém řádku ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
