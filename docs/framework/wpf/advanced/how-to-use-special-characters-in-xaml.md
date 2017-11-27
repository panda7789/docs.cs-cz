---
title: "Postupy: Použití speciálních znaků v kódu XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 308b2152f98286ba532a15e5491b5d1a25aa66dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="aaee1-102">Postupy: Použití speciálních znaků v kódu XAML</span><span class="sxs-lookup"><span data-stu-id="aaee1-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="aaee1-103">Souborech značek, které jsou vytvořeny v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] v automaticky uloží [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formát souboru ve formátu UTF-8, což znamená, že jsou správně kódovaný žádné speciální znaky, jako je například značky zvýraznění.</span><span class="sxs-lookup"><span data-stu-id="aaee1-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="aaee1-104">Je však sadu běžně používané speciální znaky, které jsou zpracovány jinak.</span><span class="sxs-lookup"><span data-stu-id="aaee1-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="aaee1-105">Postupujte podle těchto speciálních znaků [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard pro kódování.</span><span class="sxs-lookup"><span data-stu-id="aaee1-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="aaee1-106">Následující tabulka ukazuje syntaxi pro kódování speciální znaky:</span><span class="sxs-lookup"><span data-stu-id="aaee1-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="aaee1-107">Znak</span><span class="sxs-lookup"><span data-stu-id="aaee1-107">Character</span></span>|<span data-ttu-id="aaee1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaee1-108">Syntax</span></span>|<span data-ttu-id="aaee1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="aaee1-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="aaee1-110">Menší než symbol.</span><span class="sxs-lookup"><span data-stu-id="aaee1-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="aaee1-111">Znak větší než.</span><span class="sxs-lookup"><span data-stu-id="aaee1-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="aaee1-112">Symbol ampersandu.</span><span class="sxs-lookup"><span data-stu-id="aaee1-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="aaee1-113">"</span><span class="sxs-lookup"><span data-stu-id="aaee1-113">"</span></span>|`"`|<span data-ttu-id="aaee1-114">Symbol dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="aaee1-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="aaee1-115">Pokud vytvoříte značek soubor pomocí textového editoru, jako například [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Poznámkový blok, musí uložte soubor do [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kódovaný soubor formát UTF-8, abyste zachovali žádné speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="aaee1-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="aaee1-116">Následující příklad ukazuje, jak můžete použít speciální znaky v textu při vytváření značek.</span><span class="sxs-lookup"><span data-stu-id="aaee1-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaee1-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="aaee1-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
