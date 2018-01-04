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
ms.workload: dotnet
ms.openlocfilehash: 79df87d716224cb8681c1688d94fe56077452c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a>Postupy: Použití speciálních znaků v kódu XAML
Souborech značek, které jsou vytvořeny v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] v automaticky uloží [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formát souboru ve formátu UTF-8, což znamená, že jsou správně kódovaný žádné speciální znaky, jako je například značky zvýraznění. Je však sadu běžně používané speciální znaky, které jsou zpracovány jinak. Postupujte podle těchto speciálních znaků [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard pro kódování.  
  
 Následující tabulka ukazuje syntaxi pro kódování speciální znaky:  
  
|Znak|Syntaxe|Popis|  
|---------------|------------|-----------------|  
|<|`<`|Menší než symbol.|  
|>|`>`|Znak větší než.|  
|&|`&`|Symbol ampersandu.|  
|"|`"`|Symbol dvojitých uvozovek.|  
  
> [!NOTE]
>  Pokud vytvoříte značek soubor pomocí textového editoru, jako například [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Poznámkový blok, musí uložte soubor do [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kódovaný soubor formát UTF-8, abyste zachovali žádné speciální znaky.  
  
 Následující příklad ukazuje, jak můžete použít speciální znaky v textu při vytváření značek.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
