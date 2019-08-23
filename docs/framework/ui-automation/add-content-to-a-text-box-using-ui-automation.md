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
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932641"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="bd581-102">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd581-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="bd581-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bd581-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bd581-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd581-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bd581-105">Toto téma obsahuje příklad kódu, který ukazuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] použít pro vložení textu do jednořádkového textového pole.</span><span class="sxs-lookup"><span data-stu-id="bd581-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="bd581-106">K dispozici je alternativní metoda pro víceřádkové a formátované textové ovládací prvky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , kde nelze použít.</span><span class="sxs-lookup"><span data-stu-id="bd581-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="bd581-107">Pro účely porovnání příklad také ukazuje, jak použít metody Win32 k dosažení stejných výsledků.</span><span class="sxs-lookup"><span data-stu-id="bd581-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd581-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd581-108">Example</span></span>  
 <span data-ttu-id="bd581-109">Následující příklad postupuje pomocí sekvence textových ovládacích prvků v cílové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd581-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="bd581-110">Každý ovládací prvek textu je testován, aby bylo <xref:System.Windows.Automation.ValuePattern> možné zjistit, zda objekt lze z něj <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> získat pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="bd581-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="bd581-111">Pokud ovládací prvek text podporuje <xref:System.Windows.Automation.ValuePattern> <xref:System.Windows.Automation.ValuePattern.SetValue%2A> , metoda slouží k vložení uživatelsky definovaného řetězce do textového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd581-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="bd581-112">V opačném případě je použita metoda.<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bd581-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="bd581-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd581-113">See also</span></span>

- <span data-ttu-id="bd581-114">[Ukázka vložení textu TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bd581-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
