---
title: Generování a kompilace zdrojového kódu z grafu modelu CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bfc915287e579374c69636135c4b049184ef6ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164785"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>Generování a kompilace zdrojového kódu z grafu modelu CodeDOM
<xref:System.CodeDom.Compiler> Obor názvů poskytuje rozhraní pro generování zdrojového kódu z grafu modelu CodeDOM objekt a pro správu kompilace s podporované kompilátory. Zdrojový kód v konkrétním programovacím jazyce podle grafu CodeDOM může vytvořit poskytovatele kódu. Třída, která je odvozena z <xref:System.CodeDom.Compiler.CodeDomProvider> lze obvykle poskytují metody pro generování a kompilace kódu pro jazyk zprostředkovatel podporuje.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Vygenerování zdrojového kódu pomocí zprostředkovatele kódu CodeDOM  
 Vygenerování zdrojového kódu v určitém jazyce, je nutné, která reprezentuje strukturu těchto zdrojový kód pro generování grafu CodeDOM.  
  
 Následující příklad ukazují, jak vytvořit instanci <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Graf pro generování kódu je obvykle součástí <xref:System.CodeDom.CodeCompileUnit>. Pro generování kódu pro **CodeCompileUnit** , která obsahuje graf CodeDOM, zavolejte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda zprostředkovatele kódu. Tato metoda má parametr <xref:System.IO.TextWriter> , který se použije k vygenerování zdrojového kódu, takže někdy je potřeba nejprve vytvořit **TextWriter** , který je možné zapisovat na. Následující příklad ukazuje generování kódu z **CodeCompileUnit** a zápis vygenerované zdrojový kód do souboru s názvem HelloWorld.cs.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Použití zprostředkovatele kódu CodeDOM pro kompilaci sestavení  
 **Vyvolání kompilace**  
  
 Kompilace sestavení pomocí zprostředkovatele CodeDom, musí mít buď zdrojový kód a zkompilovat v jiném jazyce, pro který máte kompilátor nebo grafu CodeDOM tohoto zdroje kód mohl zkompilovat se dá vygenerovat na.  
  
 Pokud kompilujete z grafu modelu CodeDOM, předejte <xref:System.CodeDom.CodeCompileUnit> obsahující graf tak, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metoda zprostředkovatele kódu. Pokud máte soubor zdrojového kódu v jazyce, který kompilátor rozpozná, předejte název souboru, který obsahuje zdrojový kód <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metoda zprostředkovatele CodeDom. Můžete také předat řetězec obsahující zdrojový kód v jazyce, který kompilátor rozpozná na <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metoda zprostředkovatele CodeDom.  
  
 **Konfigurace parametrů kompilace**  
  
 Všechny standardní metody vyvolání kompilace poskytovatele CodeDom mít parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> , který určuje možnosti pro kompilaci.  
  
 Můžete zadat název souboru pro výstupní sestavení v <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> vlastnost **CompilerParameters**. V opačném případě se použije výchozí název výstupního souboru.  
  
 Ve výchozím nastavení nový **CompilerParameters** je inicializován s jeho <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> vlastnost nastavena na hodnotu **false**. Pokud kompilujete spustitelný program, je nutné nastavit **GenerateExecutable** vlastnost **true**. Když **GenerateExecutable** je nastavena na **false**, bude kompilátor generovat knihovnu tříd.  
  
 Pokud kompilujete z grafu modelu CodeDOM, spustitelný soubor <xref:System.CodeDom.CodeEntryPointMethod> musí být definován v grafu. Pokud existuje více vstupních bodů kódu, může být potřeba nastavit <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> vlastnost **CompilerParameters** k názvu třídy, která definuje vstupní bod, který chcete použít.  
  
 Chcete-li zahrnout informace o ladění generované spustitelné soubory, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> vlastnost **true**.  
  
 Pokud váš projekt odkazuje na všechna sestavení, je nutné zadat názvy sestavení jako položky v <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> vlastnost **CompilerParameters** použijete při vyvolání kompilace.  
  
 Kompilujete sestavení, která je napsána na paměť a místo na disku tak, že nastavíte <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> vlastnost **true**. Při generování sestavení v paměti, váš kód lze získat odkaz na vygenerované sestavení z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> vlastnost <xref:System.CodeDom.Compiler.CompilerResults>. Pokud sestavení se zapisují do disku, můžete získat cestu do generovaného sestavení z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> vlastnost **CompilerResults**.  
  
 Pokud chcete zadat vlastní argumenty příkazového řádku řetězec použitý při vyvolání procesu kompilace, nastavte řetězec <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnost.  
  
 Pokud je token Win32 zabezpečení požadované k vyvolání procesu kompilátoru, zadejte token v <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> vlastnost.  
  
 Chcete-li propojit soubor prostředků Win32 do zkompilovaného sestavení, zadejte název souboru prostředků Win32 v <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> vlastnost.  
  
 Chcete-li určit úroveň upozornění, ve kterém se má zastavit kompilace, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> vlastnost na celé číslo představující úroveň pro upozornění, kam chcete zastavit kompilace. Můžete taky nakonfigurovat kompilátor, aby kompilace zastaví, pokud jsou zjištěna upozornění tak, že nastavíte <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> vlastnost **true**.  
  
 Následující příklad kódu ukazuje kompilování zdrojového souboru pomocí odvozený od zprostředkovatele CodeDom <xref:System.CodeDom.Compiler.CodeDomProvider> třídy.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Jazyky, základem je podpora  
 Rozhraní .NET Framework poskytuje kompilátory kódu a generátory kódu pro následující jazyky: C#, Visual Basic, C++ a JScript. Podpora codeDOM je možné rozšířit do jiných jazyků implementací generátory kódu specifické pro jazyk a kompilátory kódu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [Dynamické vytváření a kompilování zdrojového kódu](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
- [CodeDOM – stručná referenční dokumentace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))
