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
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918434"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Postupy: Použití speciálních znaků v kódu XAML
Soubory značek, které jsou vytvořeny [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] v, jsou automaticky uloženy [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] ve formátu UTF-8, což znamená, že většina speciálních znaků, například značek akcentů, je správně kódována. Nicméně existuje sada běžně používaných speciálních znaků, které jsou zpracovávány jinak. Tyto speciální znaky následují [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard pro kódování.  
  
 V následující tabulce je uvedena syntaxe pro kódování této sady speciálních znaků:  
  
|Znak|Syntaxe|Popis|  
|---------------|------------|-----------------|  
|<|`&lt;`|Symbol menší než.|  
|>|`&gt;`|Větší než znaménko.|  
|&|`&amp;`|Ampersand – symbol|  
|"|`&quot;`|Symbol dvojité uvozovky.|  
  
> [!NOTE]
> Vytvoříte-li soubor s označením pomocí textového editoru, jako je například Poznámkový blok systému Windows, je nutné [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] uložit soubor ve formátu UTF-8, aby bylo možné zachovat jakékoli kódované speciální znaky.  
  
 Následující příklad ukazuje, jak lze při vytváření značek použít speciální znaky v textu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
