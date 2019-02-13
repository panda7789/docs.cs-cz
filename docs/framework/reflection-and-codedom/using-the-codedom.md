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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73810330c1ec44aa3a5edf47b3062bc2df267008
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219591"
---
# <a name="using-the-codedom"></a>Použití modelu CodeDOM
CodeDOM obsahuje typy, které představují běžné typy prvků zdrojového kódu. Můžete navrhnout program, který vytváří model zdrojového kódu pomocí prvků CodeDOM k sestavení grafu objektu. Tento graf objektu lze vykreslit jako zdrojový kód pomocí generátoru kódu CodeDOM pro podporovaný programovací jazyk. CodeDOM lze použít také ke kompilaci zdrojového kódu do binárního sestavení.  
  
 Mezi běžné použití CodeDOM patří:  
  
-   Generování kódu z šablon: generování kódu pro ASP.NET, proxy klienta služby XML webových, průvodci kódem, návrháře nebo další mechanismy vytvářející kód.  
  
-   Dynamická kompilace: podpora kompilace kódu v jednom nebo více jazyků.  
  
## <a name="building-a-codedom-graph"></a>Vytváření grafu CodeDOM  
 <xref:System.CodeDom> Obor názvů poskytuje třídám pro reprezentaci logické struktury zdrojového kódu, nezávisle na syntaxi jazyka.  
  
### <a name="the-structure-of-a-codedom-graph"></a>Struktura grafu CodeDOM  
 Struktura grafu CodeDOM je jako strom kontejnerů. Úplně nahoře, nebo kořenový, kontejner každého kompilovatelného grafu CodeDOM je <xref:System.CodeDom.CodeCompileUnit>. Každý prvek modelu zdrojového kódu musí být spojen s grafem pomocí vlastnosti <xref:System.CodeDom.CodeObject> v grafu.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Sestavení modelu zdrojového kódu pro vzorový Program Hello World  
 Následující návod znázorňuje, jak vytvořit graf objektu CodeDOM, který představuje kód pro jednoduchou aplikaci Hello World. Úplný zdrojový kód pro tento příklad kódu, najdete v článku <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tématu.  
  
#### <a name="creating-a-compile-unit"></a>Vytvoří jednotku kompilace  
 CodeDOM definuje objekt zvaný <xref:System.CodeDom.CodeCompileUnit>, který může odkazovat na graf objektu CodeDOM, který modeluje zdrojový kód pro kompilaci. A **CodeCompileUnit** má vlastnosti pro ukládání odkazů na atributy, obory názvů a sestavení.  
  
 Poskytovatelé CodeDom, které jsou odvozeny z <xref:System.CodeDom.Compiler.CodeDomProvider> třída obsahuje metody, které zpracovávají graf objektu odkazovaný **CodeCompileUnit**.  
  
 Chcete-li vytvořit grafu objektů pro jednoduchou aplikaci, musíte sestavit model zdrojového kódu a odkazovat na něj z **CodeCompileUnit**.  
  
 Novou jednotku sestavení můžete vytvořit pomocí syntaxe předvedené v tomto příkladu:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 A <xref:System.CodeDom.CodeSnippetCompileUnit> může obsahovat část zdrojového kódu, který je již v cílovém jazyce, ale nelze ji vykreslit do jiného jazyka.  
  
#### <a name="defining-a-namespace"></a>Definování oboru názvů  
 Chcete-li definovat obor názvů, vytvořte <xref:System.CodeDom.CodeNamespace> a přiřaďte název pomocí odpovídajícího konstruktoru nebo nastavením jeho **název** vlastnost.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Import oboru názvů  
 Chcete-li přidat direktivu import oboru názvů do oboru názvů, přidejte <xref:System.CodeDom.CodeNamespaceImport> , která určuje obor názvů pro import do **CodeNamespace.Imports** kolekce.  
  
 Následující kód přidává import pro **systému** obor názvů, aby **importy** kolekce **CodeNamespace** s názvem `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Propojování prvků kódu do grafu objektu  
 Všechny prvky kódu, které tvoří graf CodeDOM musí být propojen <xref:System.CodeDom.CodeCompileUnit> , který je kořenovým prvkem stromu, řadou odkazů mezi prvky přímo odkazovanými z vlastností kořenového objektu grafu. Nastavte objekt na vlastnost objektu kontejneru pro vytvoření odkazu z objektu kontejneru.  
  
 Následující příkaz přidá `samples` **CodeNamespace** k **obory názvů** vlastnost kolekce kořenové **CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Definování typu  
 Chcete-li deklarovat třídu, strukturu, rozhraní nebo výčet pomocí CodeDOM, vytvořte nový <xref:System.CodeDom.CodeTypeDeclaration>a přiřaďte jí název. Následující příklad to ukazuje pomocí přetížení konstruktoru k nastavení **název** vlastnost:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Chcete-li přidat typ do oboru názvů, přidejte <xref:System.CodeDom.CodeTypeDeclaration> , který představuje typ, který chcete přidat do oboru názvů **typy** kolekce **CodeNamespace**.  
  
 Následující příklad ukazuje, jak přidat třídu s názvem `class1` k **CodeNamespace** s názvem `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Přidání členů třídy do třídy  
 <xref:System.CodeDom> Obor názvů poskytuje celou řadu prvků, které lze použít k reprezentaci členů třídy. Každý člen třídy mohou být přidány do **členy** kolekce <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Definování kódu metody vstupního bodu pro spustitelný soubor  
 Pokud vytváříte kód spustitelného programu, je nezbytné uvést vstupní bod programu vytvořením <xref:System.CodeDom.CodeEntryPointMethod> pro reprezentaci metody, který program spustit provádění.  
  
 Následující příklad ukazuje, jak definovat metodu vstupního bodu, který obsahuje <xref:System.CodeDom.CodeMethodInvokeExpression> , která volá **System.Console.WriteLine** tisknout "Hello World!":  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Následující příkaz přidá metodu vstupního bodu s názvem `Start` k **členy** kolekce `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Nyní <xref:System.CodeDom.CodeCompileUnit> s názvem `compileUnit` obsahuje graf CodeDOM pro jednoduchý program Hello World. Informace o generování a kompilaci kódu z grafu CodeDOM naleznete v tématu [generování zdrojového kódu a kompilace programu grafu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>Další informace o vytváření grafu CodeDOM  
 CodeDOM podporuje mnoho běžných typů prvků kódu v programovacích jazycích, které podporují modul common language runtime. CodeDOM nebyl navržen, aby poskytoval prvky představující všechny možné funkce programovacího jazyka. Kód, který nelze snadno reprezentovat prvky CodeDOM lze zapouzdřit <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, nebo <xref:System.CodeDom.CodeSnippetCompileUnit>. Nicméně fragmenty kódu nelze přeložit do jiných jazyků automaticky pomocí CodeDOM.  
  
 Dokumentace pro každý z typů CodeDOM naleznete v tématu v referenční dokumentaci <xref:System.CodeDom> oboru názvů.  
  
 Rychlý graf pro nalezení prvku CodeDOM, který představuje určitý typ prvku kódu, najdete v článku [CodeDOM – Stručná referenční příručka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).
