---
title: 'Postupy: Použití speciálních znaků v kódu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: c593ca094487e8f7016b02870026321fbcb9a7c3
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256183"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="c4e50-102">Postupy: Použití speciálních znaků v kódu XAML</span><span class="sxs-lookup"><span data-stu-id="c4e50-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="c4e50-103">Souborech značek, které jsou vytvořeny v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] v automaticky uloží [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formát souboru ve formátu UTF-8, což znamená, že jsou správně kódovaný žádné speciální znaky, jako je například značky zvýraznění.</span><span class="sxs-lookup"><span data-stu-id="c4e50-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="c4e50-104">Je však sadu běžně používané speciální znaky, které jsou zpracovány jinak.</span><span class="sxs-lookup"><span data-stu-id="c4e50-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="c4e50-105">Postupujte podle těchto speciálních znaků [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard pro kódování.</span><span class="sxs-lookup"><span data-stu-id="c4e50-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="c4e50-106">Následující tabulka ukazuje syntaxi pro kódování speciální znaky:</span><span class="sxs-lookup"><span data-stu-id="c4e50-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="c4e50-107">Znak</span><span class="sxs-lookup"><span data-stu-id="c4e50-107">Character</span></span>|<span data-ttu-id="c4e50-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4e50-108">Syntax</span></span>|<span data-ttu-id="c4e50-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c4e50-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="c4e50-110">Menší než symbol.</span><span class="sxs-lookup"><span data-stu-id="c4e50-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="c4e50-111">Znak větší než.</span><span class="sxs-lookup"><span data-stu-id="c4e50-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="c4e50-112">Symbol ampersandu.</span><span class="sxs-lookup"><span data-stu-id="c4e50-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="c4e50-113">"</span><span class="sxs-lookup"><span data-stu-id="c4e50-113">"</span></span>|`&quot;`|<span data-ttu-id="c4e50-114">Symbol dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="c4e50-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c4e50-115">Pokud vytvoříte značek soubor pomocí textového editoru, jako například [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Poznámkový blok, musí uložte soubor do [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kódovaný soubor formát UTF-8, abyste zachovali žádné speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="c4e50-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="c4e50-116">Následující příklad ukazuje, jak můžete použít speciální znaky v textu při vytváření značek.</span><span class="sxs-lookup"><span data-stu-id="c4e50-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e50-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4e50-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
