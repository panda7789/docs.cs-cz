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
