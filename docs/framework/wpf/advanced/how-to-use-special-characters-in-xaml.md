---
title: 'Postupy: Použití speciálních znaků v kódu XAML'
description: Přečtěte si o syntaxi pro kódování speciálních znaků ve formátu Unicode UTF-8 v sadě Visual Studio pro použití v souborech XAML v Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: ac2388fd96aa26ddd99408ac9f847ce517958568
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168352"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="6d0ab-103">Postupy: Použití speciálních znaků v kódu XAML</span><span class="sxs-lookup"><span data-stu-id="6d0ab-103">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="6d0ab-104">Soubory značek, které jsou vytvořeny v sadě Visual Studio, jsou automaticky uloženy ve formátu Unicode UTF-8, což znamená, že většina speciálních znaků, jako jsou znaky akcentů, jsou správně kódovány.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-104">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="6d0ab-105">Nicméně existuje sada běžně používaných speciálních znaků, které jsou zpracovávány jinak.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-105">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="6d0ab-106">Tyto speciální znaky následují při kódování XML standardu W3C (konsorcium World Wide Web).</span><span class="sxs-lookup"><span data-stu-id="6d0ab-106">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="6d0ab-107">V následující tabulce je uvedena syntaxe pro kódování této sady speciálních znaků:</span><span class="sxs-lookup"><span data-stu-id="6d0ab-107">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="6d0ab-108">Znak</span><span class="sxs-lookup"><span data-stu-id="6d0ab-108">Character</span></span>|<span data-ttu-id="6d0ab-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d0ab-109">Syntax</span></span>|<span data-ttu-id="6d0ab-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6d0ab-110">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="6d0ab-111">Symbol menší než.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-111">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="6d0ab-112">Větší než znaménko.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-112">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="6d0ab-113">Ampersand – symbol</span><span class="sxs-lookup"><span data-stu-id="6d0ab-113">Ampersand symbol.</span></span>|  
|<span data-ttu-id="6d0ab-114">"</span><span class="sxs-lookup"><span data-stu-id="6d0ab-114">"</span></span>|`&quot;`|<span data-ttu-id="6d0ab-115">Symbol dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-115">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6d0ab-116">Pokud vytvoříte soubor s označením pomocí textového editoru, jako je například Poznámkový blok systému Windows, je nutné uložit soubor ve formátu Unicode UTF-8, aby bylo možné zachovat všechny zakódované speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-116">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="6d0ab-117">Následující příklad ukazuje, jak lze při vytváření značek použít speciální znaky v textu.</span><span class="sxs-lookup"><span data-stu-id="6d0ab-117">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d0ab-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d0ab-118">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
