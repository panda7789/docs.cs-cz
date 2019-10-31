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
ms.openlocfilehash: a7e341bb5bfb5b4648a222409951275169a29b79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130244"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dynamické vytváření a kompilování zdrojového kódu
.NET Framework obsahuje mechanismus nazvaný Code Document Object Model (CodeDOM), který umožňuje vývojářům programu generovat zdrojový kód pro generování zdrojového kódu v několika programovacích jazycích za běhu na základě jednoho modelu, který představuje kód. pro vykreslení.  
  
 Aby představoval zdrojový kód, prvky CodeDOM jsou vzájemně propojeny, aby tvořily datovou strukturu známou jako graf CodeDOM, který modeluje strukturu nějakého zdrojového kódu.  
  
 Obor názvů `System.CodeDom` definuje typy, které mohou představovat logickou strukturu zdrojového kódu, nezávisle na konkrétním programovacím jazyce. Obor názvů `System.CodeDom.Compiler` definuje typy pro generování zdrojového kódu z grafů CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích. Dodavatelé a vývojáři kompilátoru můžou sadu podporovaných jazyků zvětšit.  
  
 Modelování zdrojového kódu nezávislého na jazyce může být užitečné, když program potřebuje vygenerovat zdrojový kód pro model programu v několika jazycích nebo v neurčitém cílovém jazyce. Například někteří návrháři používají rozhraní CodeDOM jako rozhraní pro abstrakci jazyka k vytvoření zdrojového kódu ve správném programovacím jazyce, pokud je k dispozici podpora CodeDOM pro daný jazyk.  
  
 .NET Framework obsahuje generátory kódu a kompilátory kódu pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>a <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití modelu CodeDOM](using-the-codedom.md)  
 Popisuje běžné použití a ukazuje vytvoření jednoduchého grafu objektů pomocí CodeDOM.  
  
 [Generování zdrojového kódu a kompilování programu z grafu CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Popisuje, jak generovat zdrojový kód a zkompilovat generovaný kód s externím kompilátorem pomocí tříd definovaných v oboru názvů `System.CodeDom.Compiler`.  
  
 [Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM](how-to-create-an-xml-documentation-file-using-codedom.md)  
 Popisuje, jak použít CodeDOM k vygenerování kódu s dokumentačními komentáři XML a zkompilovat generovaný kód tak, aby vytvořil výstup dokumentace XML.  
  
 [Postupy: Vytváření třídy pomocí modelu CodeDOM](how-to-create-a-class-using-codedom.md)  
 Popisuje, jak použít CodeDOM k vygenerování třídy obsahující pole, vlastnosti, metodu, konstruktor a vstupní bod.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.CodeDom>  
 Definuje prvky, které reprezentují prvky kódu v programovacích jazycích, které cílí na modul common language runtime.  
  
 <xref:System.CodeDom.Compiler>  
 Definuje rozhraní pro generování a kompilaci kódu v době běhu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Rychlá referenční příručka CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))  
 Poskytuje vývojářům rychlý způsob, jak najít prvky CodeDOM, které představují prvky zdrojového kódu.
