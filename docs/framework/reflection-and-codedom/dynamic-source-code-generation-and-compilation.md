---
title: Dynamické vytváření a kompilování zdrojového kódu
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
ms.openlocfilehash: 7379bac07de9b78369d3742fa3288f6fea6a573f
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544986"
---
# <a name="compile-and-generate-dynamic-source-code"></a>Kompilovat a generovat dynamický zdrojový kód

.NET Framework obsahuje mechanismus nazvaný Code Document Object Model (CodeDOM), který umožňuje vývojářům programu generovat zdrojový kód pro generování zdrojového kódu v několika programovacích jazycích za běhu na základě jednoho modelu, který představuje kód pro vykreslení.  
  
Aby představoval zdrojový kód, prvky CodeDOM jsou vzájemně propojeny, aby tvořily datovou strukturu známou jako graf CodeDOM, který modeluje strukturu nějakého zdrojového kódu.  
  
<xref:System.CodeDom?displayProperty=fullName> Obor názvů definuje typy, které mohou představovat logickou strukturu zdrojového kódu, nezávisle na konkrétním programovacím jazyce. <xref:System.CodeDom.Compiler?displayProperty=fullName> Obor názvů definuje typy pro generování zdrojového kódu z grafů CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích. Dodavatelé a vývojáři kompilátoru můžou sadu podporovaných jazyků zvětšit.  
  
Modelování zdrojového kódu nezávislého na jazyce může být užitečné, když program potřebuje vygenerovat zdrojový kód pro model programu v několika jazycích nebo v neurčitém cílovém jazyce. Například někteří návrháři používají rozhraní CodeDOM jako rozhraní pro abstrakci jazyka k vytvoření zdrojového kódu ve správném programovacím jazyce, pokud je k dispozici podpora CodeDOM pro daný jazyk.  
  
.NET Framework obsahuje generátory kódu a kompilátory kódu pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>a <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>V tomto oddílu

- [Použití modelu CodeDOM](using-the-codedom.md)

  Popisuje běžné použití a ukazuje vytvoření jednoduchého grafu objektů pomocí CodeDOM.  
  
- [Generování zdrojového kódu a kompilace programu z grafu CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md)  

  Popisuje, jak generovat zdrojový kód a zkompilovat generovaný kód s externím kompilátorem pomocí tříd definovaných v `System.CodeDom.Compiler` oboru názvů.  
  
- [Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM](how-to-create-an-xml-documentation-file-using-codedom.md)  

  Popisuje, jak použít CodeDOM k vygenerování kódu s dokumentačními komentáři XML a zkompilovat generovaný kód tak, aby vytvořil výstup dokumentace XML.  
  
- [Postupy: Vytváření třídy pomocí modelu CodeDOM](how-to-create-a-class-using-codedom.md)  

  Popisuje, jak použít CodeDOM k vygenerování třídy obsahující pole, vlastnosti, metodu, konstruktor a vstupní bod.  
  
## <a name="reference"></a>Referenční informace  

- <xref:System.CodeDom>  

  Definuje prvky, které reprezentují prvky kódu v programovacích jazycích, které cílí na modul common language runtime.  
  
- <xref:System.CodeDom.Compiler>  

  Definuje rozhraní pro generování a kompilaci kódu v době běhu.  
  
## <a name="related-sections"></a>Související oddíly  

- [Stručný odkaz na CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) poskytuje vývojářům rychlý způsob, jak najít prvky CodeDOM, které představují prvky zdrojového kódu.
