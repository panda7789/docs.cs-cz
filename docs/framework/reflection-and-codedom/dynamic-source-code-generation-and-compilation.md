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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90b4214e244bc1f9c5f8e71782e604bd6c7b619
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619078"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dynamické vytváření a kompilování zdrojového kódu
Rozhraní .NET Framework obsahuje mechanismus volá se, kód modelu objektu dokumentu (CodeDOM), který umožňuje vývojářům aplikací, které generují zdrojový kód ke generování zdrojového kódu ve více programovacích jazyků v době běhu na základě jednoho modelu, který představuje kód k vykreslení.  
  
 K reprezentaci zdrojový kód, prvky CodeDOM jsou vzájemně propojit a k vytvoření datová struktura, označované jako graf CodeDOM, který modeluje struktura určitý zdrojový kód.  
  
 `System.CodeDom` Obor názvů definuje typy, které mohou představovat logické struktury zdrojového kódu, nezávisle na konkrétní programovací jazyk. `System.CodeDom.Compiler` Obor názvů definuje typy pro generování zdrojového kódu z grafu modelu CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích. Kompilátor dodavatelů nebo vývojáři rozšířit sadu podporované jazyky.  
  
 Modelování nezávislým na jazyku zdrojového kódu může být důležité, když program potřebuje ke generování zdrojového kódu pro model program v několika jazycích nebo neurčité cílový jazyk. Například některé návrháře pomocí CodeDOM jako jazyk abstrakce rozhraní pro vytvoření zdrojového kódu ve správném programovacím jazyce, pokud je k dispozici podpora CodeDOM pro jazyk.  
  
 Rozhraní .NET Framework obsahuje generátory kódu a kódu kompilátory pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, a <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 Popisuje běžné použití a ukazuje vytvoření jednoduchého objektu grafu pomocí CodeDOM.  
  
 [Generování zdrojového kódu a kompilace programu grafu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Popisuje, jak generovat zdrojového kódu a kompilace generovaného kódu s externí kompilátoru pomocí tříd definovaných v `System.CodeDom.Compiler` oboru názvů.  
  
 [Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 Popisuje, jak generovat kód, který se dokumentační komentáře XML a kompilace generovaného kódu tak, aby vytvořil výstupní dokumentace XML pomocí modelu CodeDOM.  
  
 [Postupy: Vytváření třídy pomocí modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 Popisuje, jak vygenerovat třídu obsahující pole, vlastnosti, metody, konstruktor a vstupního bodu pomocí CodeDOM.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.CodeDom>  
 Definuje prvky, které představují prvky kódu v programovacích jazycích, které se zaměřují modul common language runtime.  
  
 <xref:System.CodeDom.Compiler>  
 Definuje rozhraní pro generování a kompilace kódu za běhu.  
  
## <a name="related-sections"></a>Související oddíly  
 [CodeDOM – Stručná referenční příručka](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Poskytuje rychlý způsob, jak vývojářům usnadnit hledání prvky CodeDOM, které představují prvků zdrojového kódu.
