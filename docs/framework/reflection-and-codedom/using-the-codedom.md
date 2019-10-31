---
title: Použití modelu CodeDOM
ms.date: 03/30/2017
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
ms.openlocfilehash: c4cab79976acae236de5a8eaad5a42cdba7d04f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129999"
---
# <a name="using-the-codedom"></a>Použití modelu CodeDOM
CodeDOM poskytuje typy, které představují mnoho běžných typů prvků zdrojového kódu. Můžete navrhnout program, který vytvoří model zdrojového kódu pomocí elementů CodeDOM pro sestavení grafu objektu. Tento graf objektů lze vykreslit jako zdrojový kód pomocí generátoru kódu CodeDOM pro podporovaný programovací jazyk. CodeDOM lze také použít ke kompilaci zdrojového kódu do binárního sestavení.  
  
 Mezi běžné použití pro CodeDOM patří:  
  
- Generování kódu v šablonách: generuje se kód pro ASP.NET, proxy klientské webové služby XML, průvodce kódem, návrháře nebo jiné mechanismy generování kódu.  
  
- Dynamická kompilace: podpora kompilace kódu v jednom nebo několika jazycích.  
  
## <a name="building-a-codedom-graph"></a>Sestavení grafu CodeDOM  
 Obor názvů <xref:System.CodeDom> poskytuje třídy pro reprezentaci logické struktury zdrojového kódu, nezávisle na syntaxi jazyka.  
  
### <a name="the-structure-of-a-codedom-graph"></a>Struktura grafu CodeDOM  
 Struktura grafu CodeDOM je jako strom kontejnerů. Horní nebo kořenový kontejner každého kompilovatelnýového grafu CodeDOM je <xref:System.CodeDom.CodeCompileUnit>. Každý prvek modelu zdrojového kódu musí být propojen do grafu prostřednictvím vlastnosti <xref:System.CodeDom.CodeObject> v grafu.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Vytvoření modelu zdrojového kódu pro ukázkový Hello World program  
 Následující návod obsahuje příklad, jak vytvořit graf objektu CodeDOM, který představuje kód pro jednoduchou Hello World aplikaci. Úplný zdrojový kód pro tento příklad kódu naleznete v tématu <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.  
  
#### <a name="creating-a-compile-unit"></a>Vytváření jednotky kompilace  
 CodeDOM definuje objekt nazvaný <xref:System.CodeDom.CodeCompileUnit>, který může odkazovat na graf objektu CodeDOM, který modeluje zdrojový kód ke kompilaci. **CodeCompileUnit** má vlastnosti pro ukládání odkazů na atributy, obory názvů a sestavení.  
  
 Zprostředkovatelé CodeDom odvozené od třídy <xref:System.CodeDom.Compiler.CodeDomProvider> obsahují metody, které zpracovávají graf objektu, na který odkazuje **CodeCompileUnit**.  
  
 Chcete-li vytvořit graf objektů pro jednoduchou aplikaci, je nutné sestavit model zdrojového kódu a odkazovat na něj z **CodeCompileUnit**.  
  
 Můžete vytvořit novou jednotku kompilace se syntaxí, která je znázorněna v tomto příkladu:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <xref:System.CodeDom.CodeSnippetCompileUnit> může obsahovat oddíl zdrojového kódu, který je již v cílovém jazyce, ale nelze jej vykreslit do jiného jazyka.  
  
#### <a name="defining-a-namespace"></a>Definování oboru názvů  
 Chcete-li definovat obor názvů, vytvořte <xref:System.CodeDom.CodeNamespace> a přiřaďte k němu název pomocí příslušného konstruktoru nebo nastavením jeho vlastnosti **Name** .  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Import oboru názvů  
 Chcete-li přidat do oboru názvů direktivu import oboru názvů, přidejte <xref:System.CodeDom.CodeNamespaceImport>, která určuje obor názvů pro import do kolekce **CodeNamespace. Imports** .  
  
 Následující kód přidá import pro obor názvů **System** do kolekce **Imports** **CodeNamespace** s názvem `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Propojení prvků kódu do grafu objektů  
 Všechny prvky kódu, které tvoří graf CodeDOM, musí být propojeny s <xref:System.CodeDom.CodeCompileUnit>, který je kořenovým prvkem stromu, řadou odkazů mezi prvky přímo odkazovanými z vlastností kořenového objektu grafu. Nastavte objekt na vlastnost objektu kontejneru, aby bylo možné vytvořit odkaz z objektu kontejneru.  
  
 Následující příkaz přidá `samples` **CodeNamespace** do vlastnosti kolekce **obory názvů** kořenového **CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Definování typu  
 Chcete-li deklarovat třídu, strukturu, rozhraní nebo výčet pomocí CodeDOM, vytvořte nový <xref:System.CodeDom.CodeTypeDeclaration>a přiřaďte mu název. Následující příklad ukazuje to pomocí přetížení konstruktoru pro nastavení vlastnosti **Name** :  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Chcete-li přidat typ do oboru názvů, přidejte <xref:System.CodeDom.CodeTypeDeclaration>, který představuje typ, který chcete přidat do oboru názvů do kolekce **typů** **CodeNamespace**.  
  
 Následující příklad ukazuje, jak přidat třídu s názvem `class1` do **CodeNamespace** s názvem `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Přidání členů třídy do třídy  
 Obor názvů <xref:System.CodeDom> poskytuje celou řadu prvků, které lze použít k reprezentaci členů třídy. Každý člen třídy lze přidat do kolekce **členů** <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Definování metody vstupního bodu kódu pro spustitelný soubor  
 Pokud vytváříte kód pro spustitelný program, je nutné označit vstupní bod programu vytvořením <xref:System.CodeDom.CodeEntryPointMethod> pro reprezentaci metody, ve které má být zahájeno spouštění programu.  
  
 Následující příklad ukazuje, jak definovat metodu vstupního bodu obsahující <xref:System.CodeDom.CodeMethodInvokeExpression>, který volá **System. Console. WriteLine** pro tisk "Hello World!":  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Následující příkaz přidá metodu vstupního bodu s názvem `Start` do kolekce **members** `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Nyní <xref:System.CodeDom.CodeCompileUnit> s názvem `compileUnit` obsahuje graf CodeDOM pro jednoduchý Hello World program. Informace o generování a kompilování kódu z grafu CodeDOM naleznete v tématu [generování zdrojového kódu a kompilování programu z grafu CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>Další informace o vytváření grafu CodeDOM  
 CodeDOM podporuje mnoho běžných typů prvků kódu nalezených v programovacích jazycích, které podporují modul CLR (Common Language Runtime). CodeDOM není navržen tak, aby poskytoval prvky, které představují všechny možné funkce programovacího jazyka. Kód, který nelze snadno znázornit pomocí prvků CodeDOM, lze zapouzdřit do <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>nebo <xref:System.CodeDom.CodeSnippetCompileUnit>. Fragmenty kódu však nelze přeložit na jiné jazyky automaticky pomocí CodeDOM.  
  
 Dokumentaci pro každý z typů CodeDOM naleznete v referenční dokumentaci pro obor názvů <xref:System.CodeDom>.  
  
 Rychlý graf pro vyhledání elementu CodeDOM, který představuje konkrétní typ prvku kódu, naleznete v tématu [stručný přehled CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).
