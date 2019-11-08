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
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740839"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Postupy: Použití speciálních znaků v kódu XAML
Soubory značek, které jsou vytvořeny v sadě Visual Studio, jsou automaticky uloženy ve formátu Unicode UTF-8, což znamená, že většina speciálních znaků, jako jsou znaky akcentů, jsou správně kódovány. Nicméně existuje sada běžně používaných speciálních znaků, které jsou zpracovávány jinak. Tyto speciální znaky následují při kódování XML standardu W3C (konsorcium World Wide Web).  
  
 V následující tabulce je uvedena syntaxe pro kódování této sady speciálních znaků:  
  
|Znak|Syntaxe|Popis|  
|---------------|------------|-----------------|  
|<|`&lt;`|Symbol menší než.|  
|>|`&gt;`|Větší než znaménko.|  
|&|`&amp;`|Ampersand – symbol|  
|"|`&quot;`|Symbol dvojité uvozovky.|  
  
> [!NOTE]
> Pokud vytvoříte soubor s označením pomocí textového editoru, jako je například Poznámkový blok systému Windows, je nutné uložit soubor ve formátu Unicode UTF-8, aby bylo možné zachovat všechny zakódované speciální znaky.  
  
 Následující příklad ukazuje, jak lze při vytváření značek použít speciální znaky v textu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
