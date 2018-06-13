---
title: Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: dc6426276d354dc3334013235cda45df8e7bb383
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408730"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="1ea17-102">Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ea17-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="1ea17-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1ea17-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1ea17-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1ea17-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1ea17-105">Toto téma ukazuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] můžete použít k vystavení objektů vloženým do ovládacího prvku typu textový obsah.</span><span class="sxs-lookup"><span data-stu-id="1ea17-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ea17-106">Vložené objekty mohou obsahovat bitové kopie, hypertextové odkazy, tlačítka, tabulky nebo ovládací prvky ActiveX.</span><span class="sxs-lookup"><span data-stu-id="1ea17-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="1ea17-107">Vložené objekty se považují za podřízené objekty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="1ea17-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="1ea17-108">To umožňuje, aby zpřístupnit prostřednictvím stejná struktura stromu automatizace uživatelského rozhraní jako všechny ostatní [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy.</span><span class="sxs-lookup"><span data-stu-id="1ea17-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="1ea17-109">Funkce, pak je k dispozici prostřednictvím vzory ovládacích prvků, který je obvykle vyžaduje typ ovládacího prvku vložené objekty (například vzhledem k tomu, že jsou hypertextové odkazy založený na textu se podporují <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="1ea17-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="1ea17-110">![Vložené objekty v zásobníku textu. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="1ea17-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="1ea17-111">Ukázka dokument s textový obsah, ("Věděli jste,?" ...) a dvě vložené objekty (obrázek velryba a hypertextový odkaz text), používá jako cíl pro příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="1ea17-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ea17-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ea17-112">Example</span></span>  
 <span data-ttu-id="1ea17-113">Následující příklad kódu ukazuje, jak načíst prostřednictvím kolekce vložené objekty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="1ea17-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="1ea17-114">Dva objekty pro ukázkové dokumentu součástí zavedení by být vrácen (element bitové kopie a textový element).</span><span class="sxs-lookup"><span data-stu-id="1ea17-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ea17-115">Element obrázku by měl mít některé vnitřní text související s ním, který popisuje bitovou kopii, obvykle v jeho <xref:System.Windows.Automation.AutomationElement.NameProperty> (například "blue velryba.").</span><span class="sxs-lookup"><span data-stu-id="1ea17-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="1ea17-116">Ale když se získávají rozsah textu pokrývání uzlů objekt bitovou kopii, bitovou kopii, ani tento popisný text se vrátí do proudu textu.</span><span class="sxs-lookup"><span data-stu-id="1ea17-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="1ea17-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ea17-117">Example</span></span>  
 <span data-ttu-id="1ea17-118">Následující příklad kódu ukazuje, jak získat rozsah textu z vložený objekt v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="1ea17-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="1ea17-119">Rozsah text načíst je prázdného rozsahu kde výchozí koncový bod odpovídá "...</span><span class="sxs-lookup"><span data-stu-id="1ea17-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="1ea17-120">oceánu. (místo) "a koncová koncový bod předchází ukončovací". "představující embedded hypertextový odkaz (jak je uvedeno image poskytnutou v úvodu).</span><span class="sxs-lookup"><span data-stu-id="1ea17-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="1ea17-121">I když je to prázdného rozsahu, degenerovanou rozsah se nepovažuje, protože obsahuje nenulovou rozpětí.</span><span class="sxs-lookup"><span data-stu-id="1ea17-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ea17-122"><xref:System.Windows.Automation.TextPattern> můžete načíst založený na textu vložený objekt například hypertextový odkaz; ale sekundární <xref:System.Windows.Automation.TextPattern> bude mít ho získat od vložený objekt vystavit plnou funkčnost.</span><span class="sxs-lookup"><span data-stu-id="1ea17-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="1ea17-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ea17-123">See Also</span></span>  
 [<span data-ttu-id="1ea17-124">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ea17-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="1ea17-125">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ea17-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="1ea17-126">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="1ea17-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="1ea17-127">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ea17-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="1ea17-128">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ea17-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
