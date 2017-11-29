---
title: "Použití modelu CodeDOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 939a64919e9982232f6e8bd99070fe96e242b9bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-codedom"></a>Použití modelu CodeDOM
Modelu CodeDOM obsahuje typy, které představují mnoho běžných typů elementy zdrojového kódu. Můžete navrhnout program, který vytvoří model zdrojového kódu pomocí modelu CodeDOM elementů ke kompilaci grafu objektu. Tento objekt graf lze vykreslit jako zdrojový kód pomocí modelu CodeDOM generátor kódu pro podporované programovací jazyk. Modelu CodeDOM můžete použít také ke kompilaci zdrojového kódu do binární sestavení.  
  
 Některé běžné použití modelu CodeDOM patří:  
  
-   Generování kódu s použitím šablon: generování kódu pro ASP.NET, XML webové proxy servery služeb klienta, průvodců kódem, Designer nebo další mechanismy pro generování kódu.  
  
-   Dynamická kompilace: podpora kompilace kódu v jedné nebo více jazyků.  
  
## <a name="building-a-codedom-graph"></a>Vytvoření grafu modelu CodeDOM  
 <xref:System.CodeDom> Obor názvů obsahuje třídy představující logické struktury zdrojového kódu nezávislé na syntaxi jazyka.  
  
### <a name="the-structure-of-a-codedom-graph"></a>Struktura grafu modelu CodeDOM  
 Struktura grafu modelu CodeDOM je jako stromu kontejnerů. Nejvyšší, nebo je kontejner každý kompilační grafu modelu CodeDOM kořenový adresář, <xref:System.CodeDom.CodeCompileUnit>. Každý element, zdrojový kód modelu musí být propojena na graf prostřednictvím vlastnosti <xref:System.CodeDom.CodeObject> v grafu.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Vytváření Model zdrojového kódu pro ukázka programu Hello World  
 Následující postup poskytuje příklad k vytvoření grafu modelu CodeDOM objekt, který představuje kód pro jednoduchou aplikaci Hello World. Úplný zdrojový kód pro tento příklad kódu, najdete v článku <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tématu.  
  
#### <a name="creating-a-compile-unit"></a>Vytváření jednotka kompilace  
 Modelu CodeDOM definuje objektu s názvem <xref:System.CodeDom.CodeCompileUnit>, který může odkazovat grafu modelu CodeDOM objekt modelů zdrojového kódu ke kompilaci. A **vlastnosti CodeCompileUnit** má vlastnosti pro ukládání odkazů na sestavení, atributy a obory názvů.  
  
 Zprostředkovatele CodeDom, které jsou odvozeny od <xref:System.CodeDom.Compiler.CodeDomProvider> třída obsahuje metody, které zpracovávají grafu objektu odkazuje **vlastnosti CodeCompileUnit**.  
  
 K vytvoření grafu objektu pro jednoduchou aplikaci, sestavte kód modelu zdroje a odkazovat z **vlastnosti CodeCompileUnit**.  
  
 Můžete vytvořit novou jednotku kompilace pomocí syntaxe ukázáno v tomto příkladu:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 A <xref:System.CodeDom.CodeSnippetCompileUnit> může obsahovat části zdrojový kód, který je již v jazyce target, ale nemůže být vykreslen na jiný jazyk.  
  
#### <a name="defining-a-namespace"></a>Definování oboru názvů  
 Definici oboru názvů, vytvoření <xref:System.CodeDom.CodeNamespace> a přiřadit název pro pomocí vhodný konstruktor nebo nastavením jeho **název** vlastnost.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Import oboru názvů  
 Chcete-li přidat direktivu import oboru názvů do oboru názvů, přidejte <xref:System.CodeDom.CodeNamespaceImport> určující importovat do oboru názvů **CodeNamespace.Imports** kolekce.  
  
 Následující kód přidá importu pro **systému** názvů **importy** kolekce **CodeNamespace** s názvem `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Propojování elementy kódu do grafu objektů  
 Všechny elementy kódu, které vytvářejí grafu modelu CodeDOM musí být propojena s <xref:System.CodeDom.CodeCompileUnit> tedy kořenový prvek stromu pomocí řady odkazů mezi elementy přímo na něj odkazovat z vlastnosti kořenový objekt grafu. Nastavení objektu na vlastnost objektu kontejneru vytvořit odkaz z objektu kontejneru.  
  
 Následující příkaz přidá `samples` **CodeNamespace** k **obory názvů** vlastnost kolekce kořenové **vlastnosti CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Definování typu  
 Deklarace třídy, struktury, rozhraní nebo pomocí modelu CodeDOM – výčet, vytvořte novou <xref:System.CodeDom.CodeTypeDeclaration>a přiřaďte ho název. Následující příklad ukazuje to pomocí přetížení konstruktoru, chcete-li nastavit **název** vlastnost:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Přidání typu do oboru názvů, přidejte <xref:System.CodeDom.CodeTypeDeclaration> , která představuje typ pro přidání do oboru názvů **typy** kolekce **CodeNamespace**.  
  
 Následující příklad ukazuje, jak přidat třídu s názvem `class1` k **CodeNamespace** s názvem `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Přidávání do třídy členy třídy  
 <xref:System.CodeDom> Obor názvů obsahuje různé elementy, které můžete použít k reprezentování členy třídy. Každý člen třídy mohou být přidány do **členy** kolekce <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Definování metodu kód vstupní bod pro spustitelný soubor  
 Pokud vytváříte kód pro spustitelný program, je nezbytné k označení vstupní bod programu tak, že vytvoříte <xref:System.CodeDom.CodeEntryPointMethod> představují metodu na program, který by měl začínat provádění.  
  
 Následující příklad ukazuje, jak definovat metodu vstupního bodu, která obsahuje <xref:System.CodeDom.CodeMethodInvokeExpression> , který volá **System.Console.WriteLine** tisknout "Hello, World!":  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Následující příkaz přidá metoda s názvem `Start` k **členy** kolekce `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Nyní <xref:System.CodeDom.CodeCompileUnit> s názvem `compileUnit` obsahuje grafu modelu CodeDOM jednoduché programu Hello World. Informace o generování a kompilace kódu z grafu modelu CodeDOM najdete v tématu [zdrojový kód generování a kompilace programu z grafu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>Další informace o vytváření grafu modelu CodeDOM  
 Modelu CodeDOM podporuje mnoho běžných typů elementy kódu v programovacích jazyků, které podporují modul common language runtime nalezen. Modelu CodeDOM nebyla určená k poskytnutí prvky představující všechny možné programovací jazyk funkce. Kód, který nelze snadno pomocí modelu CodeDOM elementy můžete zapouzdřené v <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, nebo <xref:System.CodeDom.CodeSnippetCompileUnit>. Ale fragmenty nelze přeložit na ostatních jazyků automaticky pomocí modelu CodeDOM.  
  
 Dokumentace pro každou z typů CodeDOM, najdete v referenční dokumentaci k nástroji pro <xref:System.CodeDom> oboru názvů.  
  
 V rychlé grafu najít CodeDOM elementu, který představuje konkrétní typ elementu kód, najdete v článku [Stručná referenční příručka CodeDOM](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524).
