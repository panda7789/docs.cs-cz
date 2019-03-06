---
title: 'Postupy: Použití zdrojů aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 8712f7c9c60d43cf3d0348b7c3f2f4cbee0b93b1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378879"
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="e81fa-102">Postupy: Použití zdrojů aplikace</span><span class="sxs-lookup"><span data-stu-id="e81fa-102">How to: Use Application Resources</span></span>
<span data-ttu-id="e81fa-103">Tento příklad ukazuje způsob použití zdrojů aplikace.</span><span class="sxs-lookup"><span data-stu-id="e81fa-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e81fa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e81fa-104">Example</span></span>  
 <span data-ttu-id="e81fa-105">Následující příklad ukazuje soubor definice aplikace.</span><span class="sxs-lookup"><span data-stu-id="e81fa-105">The following example shows an application definition file.</span></span> <span data-ttu-id="e81fa-106">Soubor definice aplikace definuje oddíl prostředků (hodnotu <xref:System.Windows.Application.Resources%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="e81fa-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="e81fa-107">Prostředky, které jsou definované na úrovni aplikace je přístupný všechny ostatní stránky, které jsou součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="e81fa-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="e81fa-108">Prostředek v tomto případě je deklarovaný style.</span><span class="sxs-lookup"><span data-stu-id="e81fa-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="e81fa-109">Protože kompletní styl, který obsahuje šablonu ovládacího prvku může být zdlouhavé, v tomto příkladu vynechá, který je definován v šabloně ovládacího prvku <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> setter vlastnosti stylu.</span><span class="sxs-lookup"><span data-stu-id="e81fa-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="e81fa-110">Následující příklad ukazuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka, která odkazuje na úrovni aplikace prostředek, který definované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e81fa-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="e81fa-111">Prostředek se odkazuje pomocí [– rozšíření značek StaticResource](staticresource-markup-extension.md) , který určuje klíč jedinečný prostředek pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="e81fa-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="e81fa-112">Žádný prostředek s klíčem "GelButton" nenajde na aktuální stránce, takže obor vyhledávání prostředků pro požadovaný prostředek pokračuje mimo aktuální stránku a do definovaných prostředků na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="e81fa-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="e81fa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e81fa-113">See also</span></span>
- [<span data-ttu-id="e81fa-114">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="e81fa-114">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="e81fa-115">Přehled správy aplikací</span><span class="sxs-lookup"><span data-stu-id="e81fa-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="e81fa-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e81fa-116">How-to Topics</span></span>](resources-how-to-topics.md)
