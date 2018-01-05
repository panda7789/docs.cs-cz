---
title: "Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: be0081bc830a2995f7cba9f2a080c6ee33dcc79a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="a0490-102">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0490-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="a0490-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a0490-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a0490-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a0490-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a0490-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vložení textu do jednořádkové textové pole.</span><span class="sxs-lookup"><span data-stu-id="a0490-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="a0490-106">Poskytuje alternativní metoda pro text Víceřádkový a bohaté ovládací prvky kde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se nedá použít.</span><span class="sxs-lookup"><span data-stu-id="a0490-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="a0490-107">Pro účely porovnání příklad také ukazuje, jak používat metody Win32 provedete stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="a0490-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0490-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0490-108">Example</span></span>  
 <span data-ttu-id="a0490-109">Následující příklady kroků pomocí pořadí prvků textu v cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0490-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="a0490-110">Zjistí, zda je testován každý ovládací prvek text <xref:System.Windows.Automation.ValuePattern> objekt můžete získat pomocí <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a0490-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="a0490-111">Pokud ovládací prvek text podporuje <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda slouží k vložení řetězec uživatelem definované do ovládacího prvku text.</span><span class="sxs-lookup"><span data-stu-id="a0490-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="a0490-112">Jinak <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="a0490-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="a0490-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0490-113">See Also</span></span>  
 [<span data-ttu-id="a0490-114">Ukázka TextPattern vložení textu</span><span class="sxs-lookup"><span data-stu-id="a0490-114">TextPattern Insert Text Sample</span></span>](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
