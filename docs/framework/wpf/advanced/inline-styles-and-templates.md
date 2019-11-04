---
title: Vložené styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460002"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="f2b84-102">Vložené styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f2b84-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="f2b84-103">poskytuje objekty <xref:System.Windows.Style> a objekty šablon (<xref:System.Windows.FrameworkTemplate> podtříd) jako způsob, jak definovat vizuální vzhled prvku v prostředcích, aby je bylo možné použít několikrát.</span><span class="sxs-lookup"><span data-stu-id="f2b84-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="f2b84-104">Z tohoto důvodu atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], které přebírají typy <xref:System.Windows.Style> a <xref:System.Windows.FrameworkTemplate> téměř vždy provádějí odkazy na existující styly a šablony namísto definování nových vložených.</span><span class="sxs-lookup"><span data-stu-id="f2b84-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="f2b84-105">Omezení vložených stylů a šablon</span><span class="sxs-lookup"><span data-stu-id="f2b84-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="f2b84-106">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]lze vlastnosti stylu a šablony technicky nastavit jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="f2b84-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="f2b84-107">Můžete použít syntaxi atributu pro odkazování na styl, který byl definován v rámci prostředku, například `<`*objekt*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="f2b84-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="f2b84-108">Nebo můžete použít syntaxi elementu vlastnosti k definování vloženého stylu pro instanci:</span><span class="sxs-lookup"><span data-stu-id="f2b84-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="f2b84-109">*objekt* `<` `>`</span><span class="sxs-lookup"><span data-stu-id="f2b84-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="f2b84-110">*objekt* `<` `.Style>`</span><span class="sxs-lookup"><span data-stu-id="f2b84-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="f2b84-111">`<` `Style``.../>`</span><span class="sxs-lookup"><span data-stu-id="f2b84-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="f2b84-112">*objekt* `</` `.Style>`</span><span class="sxs-lookup"><span data-stu-id="f2b84-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="f2b84-113">*objekt* `</` `>`</span><span class="sxs-lookup"><span data-stu-id="f2b84-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="f2b84-114">Použití atributů je mnohem běžnější.</span><span class="sxs-lookup"><span data-stu-id="f2b84-114">The attribute usage is much more common.</span></span> <span data-ttu-id="f2b84-115">Styl, který je definován jako vložený a není definován v prostředcích, je nutně vymezen pouze na obsahující prvek a nelze jej znovu použít stejně snadno, protože nemá žádný klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="f2b84-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="f2b84-116">Obecně platí, že uživatelsky definované styly jsou všestrannější a užitečnější a je více v souladu s obecným principem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programovacího modelu oddělení logiky programu v kódu z návrhu v označení.</span><span class="sxs-lookup"><span data-stu-id="f2b84-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="f2b84-117">Obvykle neexistuje důvod k nastavení vloženého stylu nebo šablony, a to i v případě, že v tomto umístění chcete použít pouze tento styl nebo šablonu.</span><span class="sxs-lookup"><span data-stu-id="f2b84-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="f2b84-118">Většina prvků, které mohou mít styl nebo šablonu, také podporují vlastnost obsahu a obsahový model.</span><span class="sxs-lookup"><span data-stu-id="f2b84-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="f2b84-119">Pokud používáte pouze jakýkoli logický strom, který vytvoříte pomocí stylů nebo šablonování jednou, bylo by ještě snazší vyplnit tuto vlastnost obsahu ekvivalentními podřízenými elementy v přímém kódu.</span><span class="sxs-lookup"><span data-stu-id="f2b84-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="f2b84-120">To by mělo zcela obejít mechanismy stylu a šablony.</span><span class="sxs-lookup"><span data-stu-id="f2b84-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="f2b84-121">Jiné syntaxe, které jsou povoleny rozšířeními značek, které vracejí objekt, jsou také možné pro styly a šablony.</span><span class="sxs-lookup"><span data-stu-id="f2b84-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="f2b84-122">Mezi dvě taková rozšíření, která mají možné scénáře, patří [TemplateBinding](templatebinding-markup-extension.md) a <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="f2b84-122">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b84-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2b84-123">See also</span></span>

- [<span data-ttu-id="f2b84-124">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f2b84-124">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
