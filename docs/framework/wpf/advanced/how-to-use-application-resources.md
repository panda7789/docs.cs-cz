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
# <a name="how-to-use-application-resources"></a><span data-ttu-id="0b1d7-102">Postupy: Použití zdrojů aplikace</span><span class="sxs-lookup"><span data-stu-id="0b1d7-102">How to: Use Application Resources</span></span>
<span data-ttu-id="0b1d7-103">Tento příklad ukazuje, jak použít prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b1d7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b1d7-104">Example</span></span>  
 <span data-ttu-id="0b1d7-105">Následující příklad ukazuje definiční soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-105">The following example shows an application definition file.</span></span> <span data-ttu-id="0b1d7-106">Definiční soubor aplikace definuje oddíl prostředků (hodnota vlastnosti <xref:System.Windows.Application.Resources%2A>).</span><span class="sxs-lookup"><span data-stu-id="0b1d7-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="0b1d7-107">Prostředky definované na úrovni aplikace jsou k dispozici pro všechny ostatní stránky, které jsou součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="0b1d7-108">V tomto případě je prostředek deklarovaným stylem.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="0b1d7-109">Vzhledem k tomu, že kompletní styl, který obsahuje šablonu ovládacího prvku, může být zdlouhavý, tento příklad vynechává šablonu ovládacího prvku, která je definována v rámci nastavení <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastností stylu.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="0b1d7-110">Následující příklad ukazuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku, která odkazuje na prostředek na úrovni aplikace, který je v předchozím příkladu definován.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="0b1d7-111">Na prostředek se odkazuje pomocí [rozšíření značek StaticResource](staticresource-markup-extension.md) , které určuje jedinečný klíč prostředku pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="0b1d7-112">Na aktuální stránce se nenašel žádný prostředek s klíčem "GelButton", takže rozsah vyhledávání prostředků pro požadovaný prostředek pokračuje nad rámec aktuální stránky a do definovaných prostředků na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b1d7-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="0b1d7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b1d7-113">See also</span></span>

- [<span data-ttu-id="0b1d7-114">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="0b1d7-114">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="0b1d7-115">Přehled správy aplikací</span><span class="sxs-lookup"><span data-stu-id="0b1d7-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="0b1d7-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0b1d7-116">How-to Topics</span></span>](resources-how-to-topics.md)
