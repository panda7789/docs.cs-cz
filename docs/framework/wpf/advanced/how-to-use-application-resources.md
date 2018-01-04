---
title: "Postupy: Použití zdrojů aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac1fa1576e684a4b10f00310c08e4e7101a5df0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="f4e05-102">Postupy: Použití zdrojů aplikace</span><span class="sxs-lookup"><span data-stu-id="f4e05-102">How to: Use Application Resources</span></span>
<span data-ttu-id="f4e05-103">Tento příklad ukazuje, jak používat prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4e05-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4e05-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4e05-104">Example</span></span>  
 <span data-ttu-id="f4e05-105">Následující příklad ukazuje soubor definice aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4e05-105">The following example shows an application definition file.</span></span> <span data-ttu-id="f4e05-106">Definiční soubor aplikace definuje oddíl prostředků (hodnotu <xref:System.Windows.Application.Resources%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="f4e05-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="f4e05-107">Všechny ostatní stránky, které jsou součástí aplikace může být přístup k prostředkům, které jsou definované na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4e05-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="f4e05-108">V takovém případě je prostředek deklarované stylu.</span><span class="sxs-lookup"><span data-stu-id="f4e05-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="f4e05-109">Vzhledem k tomu, že dokončení styl, který obsahuje šablonu řízení může být náročná, v tomto příkladu vynechá řízení šablonu, která je definována v rámci <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Metoda setter vlastnosti stylu.</span><span class="sxs-lookup"><span data-stu-id="f4e05-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="f4e05-110">Následující příklad ukazuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky, která odkazuje na úrovni aplikace prostředek, který je definován v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f4e05-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="f4e05-111">Prostředek se odkazuje pomocí [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) určující prostředků jedinečný klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="f4e05-111">The resource is referenced by using a     [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="f4e05-112">Žádný prostředek s klíčem "GelButton" nachází na aktuální stránce, takže oboru vyhledávání prostředků pro požadovaný prostředek pokračuje mimo aktuální stránku a do definované prostředků na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4e05-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="f4e05-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4e05-113">See Also</span></span>  
 [<span data-ttu-id="f4e05-114">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="f4e05-114">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="f4e05-115">Přehled správy aplikací</span><span class="sxs-lookup"><span data-stu-id="f4e05-115">Application Management Overview</span></span>](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [<span data-ttu-id="f4e05-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="f4e05-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
