---
title: Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 9183aecdc47d54aef26d5cdca8ea11d8398be732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226505"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="3e2b4-102">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e2b4-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="3e2b4-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3e2b4-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="3e2b4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3e2b4-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vložení textu do pole jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="3e2b4-106">Alternativní metoda pro více řádků a funkčně bohaté textových ovládacích prvků neposkytujeme kde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se nedá použít.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="3e2b4-107">Pro účely porovnání v příkladu také ukazuje, jak dosáhnout stejných výsledků pomocí metod Win32.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e2b4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e2b4-108">Example</span></span>  
 <span data-ttu-id="3e2b4-109">Následující příklad vás provede sekvenci textových ovládacích prvků v cílové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="3e2b4-110">Každý ovládací prvek text je testován a zjistěte, jestli <xref:System.Windows.Automation.ValuePattern> objektu můžete získat pomocí <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="3e2b4-111">Pokud ovládací prvek textu nepodporuje <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda se používá k vložení do textu ovládacího prvku uživatelem definovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="3e2b4-112">V opačném případě <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="3e2b4-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="3e2b4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e2b4-113">See also</span></span>

- <span data-ttu-id="3e2b4-114">[Ukázka vložení prvku TextPattern textu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3e2b4-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
