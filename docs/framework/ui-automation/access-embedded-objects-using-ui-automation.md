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
ms.openlocfilehash: 07223b9e48905b0952e37a6acdb703f584d166d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131245"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="fbb72-102">Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb72-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="fbb72-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fbb72-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fbb72-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="fbb72-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fbb72-105">Toto téma ukazuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] lze použít ke zveřejnění objekty vložené v obsahu prvku textu.</span><span class="sxs-lookup"><span data-stu-id="fbb72-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbb72-106">Vložené objekty mohou obsahovat obrázky, hypertextové odkazy, tlačítka, tabulek nebo ovládací prvky ActiveX.</span><span class="sxs-lookup"><span data-stu-id="fbb72-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="fbb72-107">Vložené objekty jsou považovány za podřízené objekty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu.</span><span class="sxs-lookup"><span data-stu-id="fbb72-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="fbb72-108">To jim zpřístupní prostřednictvím stejnou strukturu stromu automatizace uživatelského rozhraní jako všechny ostatní umožňuje [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy.</span><span class="sxs-lookup"><span data-stu-id="fbb72-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="fbb72-109">Funkce, pak je k dispozici prostřednictvím vzorů ovládacích prvků, které jsou obvykle vyžaduje vložené objekty – typ ovládacího prvku (například protože hypertextové odkazy jsou založeny na text se bude podporovat <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="fbb72-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="fbb72-110">![Vložené objekty v zásobník textu. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="fbb72-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="fbb72-111">Ukázkový dokument s textový obsah ("Věděli jste?" ...) a dvě vložené objekty (obrázek velryba a text hypertextového odkazu), použít jako cíl pro příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="fbb72-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbb72-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbb72-112">Example</span></span>  
 <span data-ttu-id="fbb72-113">Následující příklad kódu ukazuje, jak načíst kolekce vložené objekty v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu.</span><span class="sxs-lookup"><span data-stu-id="fbb72-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="fbb72-114">Pro ukázkový dokument v úvodu k dispozici bude vrácen dva objekty (image element a textový element).</span><span class="sxs-lookup"><span data-stu-id="fbb72-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbb72-115">Elementu obrázku by měl mít některé vnitřní text související s tím, který popisuje bitovou kopii, obvykle v jeho <xref:System.Windows.Automation.AutomationElement.NameProperty> (například "modrá velryba.").</span><span class="sxs-lookup"><span data-stu-id="fbb72-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="fbb72-116">Ale při se získá rozsah textu pokrývání uzlů objektu image, image ani tento popisný text se vrací do toku textu.</span><span class="sxs-lookup"><span data-stu-id="fbb72-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="fbb72-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbb72-117">Example</span></span>  
 <span data-ttu-id="fbb72-118">Následující příklad kódu ukazuje, jak získat rozsah textu z vloženého objektu v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu.</span><span class="sxs-lookup"><span data-stu-id="fbb72-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="fbb72-119">Rozsah textu, načíst je prázdného rozsahu, kde výchozí koncový bod odpovídá "...</span><span class="sxs-lookup"><span data-stu-id="fbb72-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="fbb72-120">na oceánských. (místo) "a koncové koncový bod předchází uzavírací". "představující embedded hypertextový odkaz (jak je uvedeno na obrázku v úvodu k dispozici).</span><span class="sxs-lookup"><span data-stu-id="fbb72-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="fbb72-121">I když je to prázdný rozsah, to se nepovažuje za degenerovanou rozsah vzhledem k tomu, že má nenulovou rozpětí.</span><span class="sxs-lookup"><span data-stu-id="fbb72-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbb72-122"><xref:System.Windows.Automation.TextPattern> můžete načíst textový vložený objekt například hypertextový odkaz. ale sekundární <xref:System.Windows.Automation.TextPattern> muset získat z vloženého objektu vystavit plnou funkčnost.</span><span class="sxs-lookup"><span data-stu-id="fbb72-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="fbb72-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbb72-123">See also</span></span>

- [<span data-ttu-id="fbb72-124">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb72-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="fbb72-125">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb72-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="fbb72-126">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="fbb72-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="fbb72-127">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb72-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="fbb72-128">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb72-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
