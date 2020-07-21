---
title: Generování a kompilace zdrojového kódu z grafu modelu CodeDOM
description: Vygenerujte a zkompilujte zdrojový kód z grafu CodeDOM v rozhraní .NET. Pro generování zdrojového kódu a kompilování sestavení použijte poskytovatele kódu CodeDOM.
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
ms.openlocfilehash: 85654fe961f01ad7b8fb886d59a3de9ab0efe7aa
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474043"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>Generování a kompilace zdrojového kódu z grafu modelu CodeDOM
<xref:System.CodeDom.Compiler>Obor názvů poskytuje rozhraní pro generování zdrojového kódu z grafů objektů CodeDOM a pro správu kompilace s podporovanými kompilátory. Poskytovatel kódu může vytvořit zdrojový kód v konkrétním programovacím jazyce podle grafu CodeDOM. Třída, která je odvozena z, <xref:System.CodeDom.Compiler.CodeDomProvider> může obvykle poskytovat metody pro generování a kompilování kódu pro jazyk, který poskytovatel podporuje.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Použití poskytovatele kódu CodeDOM ke generování zdrojového kódu  
 Chcete-li generovat zdrojový kód v konkrétním jazyce, potřebujete graf CodeDOM, který představuje strukturu zdrojového kódu, který má být vygenerován.  
  
 Následující příklad ukazuje, jak vytvořit instanci třídy <xref:Microsoft.CSharp.CSharpCodeProvider> :  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Graf pro generování kódu je obvykle obsažen v <xref:System.CodeDom.CodeCompileUnit> . Chcete-li vygenerovat kód pro **CodeCompileUnit** , který obsahuje graf CodeDOM, zavolejte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu poskytovatele kódu. Tato metoda má parametr pro <xref:System.IO.TextWriter> , který používá ke generování zdrojového kódu, takže je někdy nutné nejprve vytvořit modul **TextWriter** , do kterého lze zapisovat. Následující příklad ukazuje vygenerování kódu z **CodeCompileUnit** a zápis generovaného zdrojového kódu do souboru s názvem HelloWorld.cs.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Použití poskytovatele kódu CodeDOM ke kompilaci sestavení  
 **Vyvolání kompilace**  
  
 Chcete-li zkompilovat sestavení pomocí poskytovatele CodeDom, je nutné mít buď zdrojový kód pro zkompilování v jazyce, pro který máte kompilátor, nebo graf CodeDOM, ze kterého lze zdrojový kód kompilovat, vytvořit.  
  
 Pokud kompilujete z grafu CodeDOM, předejte seznam <xref:System.CodeDom.CodeCompileUnit> obsahující graf <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metodě poskytovatele kódu. Máte-li soubor zdrojového kódu v jazyce, který zná kompilátor, předejte název souboru obsahujícího zdrojový kód do <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metody poskytovatele CodeDom. Můžete také předat řetězec obsahující zdrojový kód v jazyce, který kompilátor rozumí <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metodě poskytovatele CodeDom.  
  
 **Konfigurace parametrů kompilace**  
  
 Všechny metody standardního volání kompilace zprostředkovatele CodeDom mají parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> , který určuje možnosti, které se mají použít pro kompilaci.  
  
 Můžete zadat název souboru pro výstupní sestavení ve <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> vlastnosti **CompilerParameters**. V opačném případě se použije výchozí název výstupního souboru.  
  
 Ve výchozím nastavení je nová **CompilerParameters** inicializována s <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> vlastností nastavenou na **hodnotu false**. Pokud kompilujete spustitelný program, je nutné nastavit vlastnost **GenerateExecutable** na **hodnotu true**. Pokud je **GenerateExecutable** nastaveno na **false**, kompilátor vygeneruje knihovnu tříd.  
  
 Pokud kompilujete spustitelný soubor z grafu CodeDOM, <xref:System.CodeDom.CodeEntryPointMethod> musí být definován v grafu. Pokud existuje více vstupních bodů kódu, může být nutné nastavit <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> vlastnost **CompilerParameters** na název třídy definující vstupní bod, který má být použit.  
  
 Chcete-li zahrnout informace o ladění do generovaného spustitelného souboru, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> vlastnost na **hodnotu true**.  
  
 Pokud váš projekt odkazuje na jakákoli sestavení, je nutné zadat názvy sestavení jako položky v <xref:System.Collections.Specialized.StringCollection> podobě <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> vlastnosti **CompilerParameters** , kterou použijete při volání kompilace.  
  
 Můžete zkompilovat sestavení, které je zapsáno do paměti, nikoli na disk nastavením <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> vlastnosti na **hodnotu true**. Když je sestavení generované v paměti, váš kód může získat odkaz na vygenerované sestavení z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> vlastnosti třídy <xref:System.CodeDom.Compiler.CompilerResults> . Pokud je sestavení zapisováno na disk, můžete získat cestu k generovanému sestavení z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> vlastnosti **CompilerResults**.  
  
 Chcete-li zadat vlastní řetězec argumentů příkazového řádku, který má být použit při volání procesu kompilace, nastavte řetězec ve <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> Vlastnosti.  
  
 Pokud je k vyvolání procesu kompilátoru vyžadován token zabezpečení Win32, zadejte token do <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> Vlastnosti.  
  
 Chcete-li propojit soubor prostředků Win32 s kompilovaným sestavením, zadejte název souboru prostředků Win32 do <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> Vlastnosti.  
  
 Chcete-li určit úroveň upozornění, při které má být kompilace zastavena, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> vlastnost na celé číslo, které představuje úroveň upozornění, při které má být kompilace zastavena. Můžete také nakonfigurovat kompilátor pro zastavení kompilace, pokud jsou zjištěna upozornění, nastavením <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> vlastnosti na **hodnotu true**.  
  
 Následující příklad kódu ukazuje, jak zkompilovat zdrojový soubor pomocí poskytovatele CodeDom odvozeného z <xref:System.CodeDom.Compiler.CodeDomProvider> třídy.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Jazyky s počáteční podporou  
 .NET Framework poskytuje kompilátory kódu a generátory kódu pro následující jazyky: C#, Visual Basic, C++ a JScript. Podporu CodeDOM lze rozšířit i na jiné jazyky implementací generátorů kódu specifických pro jazyk a kompilátorů kódu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [Generování a kompilace dynamického zdrojového kódu](dynamic-source-code-generation-and-compilation.md)
- [Rychlá referenční příručka CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))
