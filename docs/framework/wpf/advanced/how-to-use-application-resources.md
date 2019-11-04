---
title: 'Postupy: Použití zdrojů aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460265"
---
# <a name="how-to-use-application-resources"></a>Postupy: Použití zdrojů aplikace
Tento příklad ukazuje, jak použít prostředky aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definiční soubor aplikace. Definiční soubor aplikace definuje oddíl prostředků (hodnota vlastnosti <xref:System.Windows.Application.Resources%2A>). Prostředky definované na úrovni aplikace jsou k dispozici pro všechny ostatní stránky, které jsou součástí aplikace. V tomto případě je prostředek deklarovaným stylem. Vzhledem k tomu, že kompletní styl, který obsahuje šablonu ovládacího prvku, může být zdlouhavý, tento příklad vynechává šablonu ovládacího prvku, která je definována v rámci nastavení <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastností stylu.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 Následující příklad ukazuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku, která odkazuje na prostředek na úrovni aplikace, který je v předchozím příkladu definován. Na prostředek se odkazuje pomocí [rozšíření značek StaticResource](staticresource-markup-extension.md) , které určuje jedinečný klíč prostředku pro požadovaný prostředek. Na aktuální stránce se nenašel žádný prostředek s klíčem "GelButton", takže rozsah vyhledávání prostředků pro požadovaný prostředek pokračuje nad rámec aktuální stránky a do definovaných prostředků na úrovni aplikace.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Přehled správy aplikací](../app-development/application-management-overview.md)
- [Témata s postupy](resources-how-to-topics.md)
