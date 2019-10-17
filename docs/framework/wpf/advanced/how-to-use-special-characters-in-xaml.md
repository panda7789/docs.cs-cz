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
ms.openlocfilehash: 27f2b18593d075b54eb8c3351bbb84415700cfd4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395807"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="7abcf-102">Postupy: Použití speciálních znaků v kódu XAML</span><span class="sxs-lookup"><span data-stu-id="7abcf-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="7abcf-103">Soubory značek, které jsou vytvořeny v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], jsou automaticky uloženy ve formátu Unicode UTF-8, což znamená, že většina speciálních znaků, jako jsou znaky akcentů, jsou správně kódovány.</span><span class="sxs-lookup"><span data-stu-id="7abcf-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="7abcf-104">Nicméně existuje sada běžně používaných speciálních znaků, které jsou zpracovávány jinak.</span><span class="sxs-lookup"><span data-stu-id="7abcf-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="7abcf-105">Tyto speciální znaky následují Standard [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] pro kódování.</span><span class="sxs-lookup"><span data-stu-id="7abcf-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="7abcf-106">V následující tabulce je uvedena syntaxe pro kódování této sady speciálních znaků:</span><span class="sxs-lookup"><span data-stu-id="7abcf-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="7abcf-107">Znak</span><span class="sxs-lookup"><span data-stu-id="7abcf-107">Character</span></span>|<span data-ttu-id="7abcf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7abcf-108">Syntax</span></span>|<span data-ttu-id="7abcf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7abcf-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="7abcf-110">Symbol menší než.</span><span class="sxs-lookup"><span data-stu-id="7abcf-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="7abcf-111">Větší než znaménko.</span><span class="sxs-lookup"><span data-stu-id="7abcf-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="7abcf-112">Ampersand – symbol</span><span class="sxs-lookup"><span data-stu-id="7abcf-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="7abcf-113">"</span><span class="sxs-lookup"><span data-stu-id="7abcf-113">"</span></span>|`&quot;`|<span data-ttu-id="7abcf-114">Symbol dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="7abcf-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="7abcf-115">Pokud vytvoříte soubor s označením pomocí textového editoru, jako je například Poznámkový blok systému Windows, je nutné uložit soubor ve formátu Unicode UTF-8, aby bylo možné zachovat všechny zakódované speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="7abcf-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="7abcf-116">Následující příklad ukazuje, jak lze při vytváření značek použít speciální znaky v textu.</span><span class="sxs-lookup"><span data-stu-id="7abcf-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7abcf-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="7abcf-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
