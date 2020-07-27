---
title: Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní
description: Podívejte se na příklad, jak přidat obsah do jednořádkového textového pole pomocí automatizace uživatelského rozhraní Microsoft v .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 4136d460de7091a515580cade16f06e54699727a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166916"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="5382b-103">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5382b-103">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="5382b-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5382b-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5382b-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5382b-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5382b-106">Toto téma obsahuje příklad kódu, který ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pro vložení textu do jednořádkového textového pole.</span><span class="sxs-lookup"><span data-stu-id="5382b-106">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="5382b-107">K dispozici je alternativní metoda pro víceřádkové a formátované textové ovládací prvky, kde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nelze použít.</span><span class="sxs-lookup"><span data-stu-id="5382b-107">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="5382b-108">Pro účely porovnání příklad také ukazuje, jak použít metody Win32 k dosažení stejných výsledků.</span><span class="sxs-lookup"><span data-stu-id="5382b-108">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5382b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5382b-109">Example</span></span>  
 <span data-ttu-id="5382b-110">Následující příklad postupuje pomocí sekvence textových ovládacích prvků v cílové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5382b-110">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="5382b-111">Každý ovládací prvek textu je testován, aby bylo možné zjistit, zda <xref:System.Windows.Automation.ValuePattern> objekt lze z něj získat pomocí <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5382b-111">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="5382b-112">Pokud ovládací prvek text podporuje <xref:System.Windows.Automation.ValuePattern> , <xref:System.Windows.Automation.ValuePattern.SetValue%2A> Metoda slouží k vložení uživatelsky definovaného řetězce do textového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5382b-112">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="5382b-113">V opačném případě <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> je použita metoda.</span><span class="sxs-lookup"><span data-stu-id="5382b-113">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="5382b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5382b-114">See also</span></span>

- <span data-ttu-id="5382b-115">[Ukázka vložení textu TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5382b-115">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
