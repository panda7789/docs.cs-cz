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
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935353"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource
Použijete-li <xref:System.Windows.Forms.BindingSource> komponentu k navázání model Windows Formsho ovládacího prvku na zdroj dat, může být nutné pro přizpůsobení vytváření nových položek. Komponenta to dělá tak, že <xref:System.Windows.Forms.BindingSource.AddingNew> poskytne událost, která je obvykle vyvolána, když ovládací prvek musí vytvořit novou položku. <xref:System.Windows.Forms.BindingSource> Vaše obslužná rutina události může poskytnout jakékoli vlastní chování (například volání metody webové služby nebo získání nového objektu z továrny tříd).  
  
> [!NOTE]
> Při přidání položky pomocí zpracování <xref:System.Windows.Forms.BindingSource.AddingNew> události nelze sčítání zrušit.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku s objektem pro vytváření tříd <xref:System.Windows.Forms.BindingSource> pomocí komponenty. Když uživatel klikne na <xref:System.Windows.Forms.DataGridView> nový řádek ovládacího prvku <xref:System.Windows.Forms.BindingSource.AddingNew> , vyvolá se událost. Obslužná rutina události vytvoří nový `DemoCustomer` objekt, který je přiřazen <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> vlastnosti. Tím dojde k přidání `DemoCustomer` nového objektu <xref:System.Windows.Forms.BindingSource> do seznamu komponent a k zobrazení v novém řádku <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Svázání ovládacího prvku model Windows Forms s typem](how-to-bind-a-windows-forms-control-to-a-type.md)
