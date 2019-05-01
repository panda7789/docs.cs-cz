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
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051078"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="def02-102">Postupy: Použití speciálních znaků v kódu XAML</span><span class="sxs-lookup"><span data-stu-id="def02-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="def02-103">Soubory kódu, které jsou vytvořeny v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] se automaticky uloží do [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formát UTF-8 soubor, což znamená, že jsou správně kódovány žádné speciální znaky, jako je například diakritická znaménka.</span><span class="sxs-lookup"><span data-stu-id="def02-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="def02-104">Je však sadu běžně používané speciální znaky, které jsou zpracovávány jinak.</span><span class="sxs-lookup"><span data-stu-id="def02-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="def02-105">Postupujte podle těchto speciálních znaků [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] úrovně standard pro kódování.</span><span class="sxs-lookup"><span data-stu-id="def02-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="def02-106">Následující tabulka ukazuje syntaxi pro kódování tuto sadu speciální znaky:</span><span class="sxs-lookup"><span data-stu-id="def02-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="def02-107">Znak</span><span class="sxs-lookup"><span data-stu-id="def02-107">Character</span></span>|<span data-ttu-id="def02-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="def02-108">Syntax</span></span>|<span data-ttu-id="def02-109">Popis</span><span class="sxs-lookup"><span data-stu-id="def02-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="def02-110">Menší než symbol.</span><span class="sxs-lookup"><span data-stu-id="def02-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="def02-111">Symbol větší než.</span><span class="sxs-lookup"><span data-stu-id="def02-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="def02-112">Odděluje symbol ampersandu.</span><span class="sxs-lookup"><span data-stu-id="def02-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="def02-113">"</span><span class="sxs-lookup"><span data-stu-id="def02-113">"</span></span>|`&quot;`|<span data-ttu-id="def02-114">Symbol dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="def02-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="def02-115">Pokud vytvoříte značky soubor pomocí textového editoru, jako například [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Poznámkový blok, musíte uložit soubor v [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kódování souboru formát UTF-8, aby bylo možné zachovat některé speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="def02-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="def02-116">Následující příklad ukazuje, jak můžete použít speciální znaky v textu při vytváření značek.</span><span class="sxs-lookup"><span data-stu-id="def02-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="def02-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="def02-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
