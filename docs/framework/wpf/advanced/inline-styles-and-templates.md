---
title: Vložené styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091431"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="ddd2a-102">Vložené styly a šablony</span><span class="sxs-lookup"><span data-stu-id="ddd2a-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ddd2a-103">poskytuje <xref:System.Windows.Style> objekty a objekty šablony (<xref:System.Windows.FrameworkTemplate> podtřídy) jako způsob, jak definovat vzhled elementu v prostředky, takže je možné použít víc než jednou.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="ddd2a-104">Z tohoto důvodu atributů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , která přijímá typy <xref:System.Windows.Style> a <xref:System.Windows.FrameworkTemplate> téměř vždy ujistěte se, odkazy na prostředky na stávající – styly a šablony spíše než definovat nové značky vložené.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="ddd2a-105">Omezení vložené styly a šablony</span><span class="sxs-lookup"><span data-stu-id="ddd2a-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="ddd2a-106">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], styl a šablony vlastnosti lze nastavit technicky v jednom ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="ddd2a-107">Syntaxe atributu slouží k odkazování styl, který byl definován v rámci prostředku, třeba `<` *objekt*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="ddd2a-108">Nebo syntax prvku vlastnosti můžete použít k definování vložených styl, například:</span><span class="sxs-lookup"><span data-stu-id="ddd2a-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 `<` *<span data-ttu-id="ddd2a-109">odkazy objektů</span><span class="sxs-lookup"><span data-stu-id="ddd2a-109">object</span></span>* `>`  
  
 `<` *<span data-ttu-id="ddd2a-110">odkazy objektů</span><span class="sxs-lookup"><span data-stu-id="ddd2a-110">object</span></span>* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *<span data-ttu-id="ddd2a-111">odkazy objektů</span><span class="sxs-lookup"><span data-stu-id="ddd2a-111">object</span></span>* `.Style>`  
  
 `</` *<span data-ttu-id="ddd2a-112">odkazy objektů</span><span class="sxs-lookup"><span data-stu-id="ddd2a-112">object</span></span>* `>`  
  
 <span data-ttu-id="ddd2a-113">Použití atributu je mnohem častější.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-113">The attribute usage is much more common.</span></span> <span data-ttu-id="ddd2a-114">Styl, který je definována vložením a není definováno v prostředků nutně působí na nadřazeného elementu a nejde znovu použít, stejně snadno, protože nemá klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-114">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="ddd2a-115">Obecně definován prostředek stylu je univerzální a užitečné a další podle obecného [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programovací model Princip oddělení logiku programu v kódu z návrhu v kódu.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-115">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="ddd2a-116">Obvykle neexistuje žádný důvod nastavit styl nebo šablona vložené, i v případě, že chcete použít tento styl nebo šablona v dané oblasti.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-116">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="ddd2a-117">Většinu prvků, které mohou provádět styl nebo šablona také podporují vlastnost obsahu a obsahu modelu.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-117">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="ddd2a-118">Pokud používáte pouze libovolné Logická stromová struktura jednou vytvořit pomocí stylu nebo šablony, by bylo ještě jednodušší právě vyplníte vlastnost tohoto obsahu ekvivalentní podřízené elementy v kódu s přímým přístupem.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-118">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="ddd2a-119">To by úplně obejít mechanismy věnovaný stylu a šablon.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-119">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="ddd2a-120">Styly a šablony existují také jiné syntaxe ve – rozšíření značek, které vracejí objekt povolené.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-120">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="ddd2a-121">Dva taková rozšíření, kterých je možné scénáře zahrnují [TemplateBinding](templatebinding-markup-extension.md) a <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="ddd2a-121">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd2a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddd2a-122">See also</span></span>

- [<span data-ttu-id="ddd2a-123">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="ddd2a-123">Styling and Templating</span></span>](../controls/styling-and-templating.md)
