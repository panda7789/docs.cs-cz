---
title: 'Postupy: Používání prostředků aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 70dff8089c4da70fdc61247a0c604cf7ee85d02b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088196"
---
# <a name="how-to-use-application-resources"></a>Postupy: Používání prostředků aplikace
Tento příklad ukazuje způsob použití zdrojů aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor definice aplikace. Soubor definice aplikace definuje oddíl prostředků (hodnotu <xref:System.Windows.Application.Resources%2A> vlastnost). Prostředky, které jsou definované na úrovni aplikace je přístupný všechny ostatní stránky, které jsou součástí aplikace. Prostředek v tomto případě je deklarovaný style. Protože kompletní styl, který obsahuje šablonu ovládacího prvku může být zdlouhavé, v tomto příkladu vynechá, který je definován v šabloně ovládacího prvku <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> setter vlastnosti stylu.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 Následující příklad ukazuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka, která odkazuje na úrovni aplikace prostředek, který definované v předchozím příkladu. Prostředek se odkazuje pomocí [– rozšíření značek StaticResource](staticresource-markup-extension.md) , který určuje klíč jedinečný prostředek pro požadovaný prostředek. Žádný prostředek s klíčem "GelButton" nenajde na aktuální stránce, takže obor vyhledávání prostředků pro požadovaný prostředek pokračuje mimo aktuální stránku a do definovaných prostředků na úrovni aplikace.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](xaml-resources.md)
- [Přehled správy aplikací](../app-development/application-management-overview.md)
- [Témata s postupy](resources-how-to-topics.md)
