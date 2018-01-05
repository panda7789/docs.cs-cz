---
title: "Dynamické vytváření a kompilování zdrojového kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a74d25372b83c848621a44f6ea32a455a0f18ccf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dynamické vytváření a kompilování zdrojového kódu
Mechanismus volat Code Document Object Model (CodeDOM), která umožňuje vývojářům programy, které emitování zdrojového kódu ke generování zdrojového kódu ve více programovacích jazyků v době běhu na základě jednoho modelu, který představuje kód zahrnuje rozhraní .NET Framework k vykreslení.  
  
 Představují zdrojového kódu, CodeDOM elementy propojené s druhým k formuláři Datová struktura známé jako grafu modelu CodeDOM, který modelů strukturu některé zdrojového kódu.  
  
 `System.CodeDom` Obor názvů definuje typy, které může představovat logické struktury zdrojového kódu nezávislé na konkrétní programovací jazyk. `System.CodeDom.Compiler` Obor názvů definuje typy pro generování zdrojového kódu z grafů CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích. Dodavatelé kompilátoru a vývojářům můžete rozšířit sadu podporovaných jazyků.  
  
 Modelování nezávislé na jazyku zdrojového kódu může být užitečné, když program potřebuje ke generování zdrojového kódu pro model program v několika jazycích nebo neví cílový jazyk. Například některé návrháři používají modelu CodeDOM jako jazyk abstrakce rozhraní k vytvoření zdrojového kódu ve správné programovací jazyk, pokud je k dispozici podpora CodeDOM pro jazyk.  
  
 Rozhraní .NET Framework zahrnuje generátory kódu a kompilátory kódu pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, a <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 Popisuje běžná použití a ukazuje vytvoření jednoduchého objektu graf pomocí modelu CodeDOM.  
  
 [Generování zdrojového kódu a kompilace programu z grafu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Popisuje, jak generovat zdrojový kód a kompilace generovaného kódu s externí kompilátoru pomocí třídy definované v `System.CodeDom.Compiler` oboru názvů.  
  
 [Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 Popisuje postup generování kódu s XML – dokumentační komentáře a kompilace generovaného kódu tak, aby vytvoří výstupní dokumentace XML pomocí modelu CodeDOM.  
  
 [Postupy: Vytváření třídy pomocí modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 Popisuje, jak můžete vygenerovat třída obsahující pole, vlastností, metoda, konstruktor a vstupního bodu pomocí modelu CodeDOM.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.CodeDom>  
 Definuje prvky, které představují elementy kódu v programovací jazyky cílených modul common language runtime.  
  
 <xref:System.CodeDom.Compiler>  
 Definuje rozhraní pro generování a kompilace kódu v době běhu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Stručná referenční příručka modelu codeDOM](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Poskytuje rychlý způsob pro vývojáře k vyhledání CodeDOM prvky, které představují elementy zdrojového kódu.
