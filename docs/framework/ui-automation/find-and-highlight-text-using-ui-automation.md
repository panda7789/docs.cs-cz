---
title: Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní
description: Vyhledejte a zvýrazněte text pomocí automatizace uživatelského rozhraní. Příklad sekvenční hledání a zvýrazní všechny výskyty řetězce v rámci obsahu ovládacího prvku text.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: e4aca4b5ccdbc429a3d6267afc09b9f8b99cd7e9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164191"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="cea7c-104">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cea7c-104">Find and Highlight Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="cea7c-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cea7c-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cea7c-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cea7c-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cea7c-107">Toto téma ukazuje, jak postupně vyhledat a zvýraznit všechny výskyty řetězce v rámci obsahu ovládacího prvku text pomocí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cea7c-107">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="cea7c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cea7c-108">Example</span></span>  
 <span data-ttu-id="cea7c-109">Následující příklad získá <xref:System.Windows.Automation.TextPattern> objekt z textového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cea7c-109">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="cea7c-110"><xref:System.Windows.Automation.Text.TextPatternRange>Objekt, který představuje textový obsah celého dokumentu, se pak vytvoří pomocí <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> vlastnosti this <xref:System.Windows.Automation.TextPattern> .</span><span class="sxs-lookup"><span data-stu-id="cea7c-110">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="cea7c-111"><xref:System.Windows.Automation.Text.TextPatternRange>Pak se vytvoří dva další objekty pro funkce sekvenčního vyhledávání a zvýrazňování.</span><span class="sxs-lookup"><span data-stu-id="cea7c-111">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="cea7c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cea7c-112">See also</span></span>

- [<span data-ttu-id="cea7c-113">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cea7c-113">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
