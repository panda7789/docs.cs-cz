---
title: "Generování a kompilace zdrojového kódu z grafu modelu CodeDOM"
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
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56e2effec282900101fc0cbe489c76b523184ab2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>Generování a kompilace zdrojového kódu z grafu modelu CodeDOM
<xref:System.CodeDom.Compiler> Obor názvů poskytuje rozhraní pro generování zdrojového kódu z objektu grafů CodeDOM a pro správu kompilace pomocí podporovaných kompilátory. Zprostředkovatel kódu může vytvářet zdrojový kód v konkrétní programovací jazyk podle grafu modelu CodeDOM. Třída odvozená z <xref:System.CodeDom.Compiler.CodeDomProvider> obvykle poskytne metody pro generování a kompilace kódu pro jazyk zprostředkovatel podporuje.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Generování zdrojového kódu pomocí zprostředkovatele kódu modelu CodeDOM  
 Generování zdrojového kódu v určitém jazyce, je nutné představující strukturu zdrojového kódu ke generování grafu modelu CodeDOM.  
  
 Následující příklad ukazují, jak vytvořit instanci <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Graf pro generování kódu je obvykle součástí <xref:System.CodeDom.CodeCompileUnit>. Generovat kód pro **vlastnosti CodeCompileUnit** obsahující grafu modelu CodeDOM, volejte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda zprostředkovatele kódu. Tato metoda má parametr pro <xref:System.IO.TextWriter> používající ke generování zdrojového kódu, proto je někdy nutné nejprve vytvořit **TextWriter** je možné zapsat do. Následující příklad ukazuje generování kódu z **vlastnosti CodeCompileUnit** a zápis do souboru s názvem HelloWorld.cs generovaný zdrojový kód.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Pomocí kódu zprostředkovatele CodeDOM kompilace sestavení  
 **Vyvolání kompilace**  
  
 Kompilace sestavení pomocí zprostředkovatele CodeDom, musí mít buď zdrojový kód v jazyce, pro které máte kompilátor zkompilovat nebo CodeDOM graf tento zdroj z lze vytvořit kód mohl zkompilovat.  
  
 Pokud jsou kompilaci z grafu modelu CodeDOM, předat <xref:System.CodeDom.CodeCompileUnit> obsahující graf tak, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metoda zprostředkovatele kódu. Pokud máte souboru zdrojového kódu v jazyce, který funguje s technologií kompilátor, předat název souboru, který obsahuje zdrojový kód, který <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metoda zprostředkovatele CodeDom. Můžete také předat řetězec obsahující zdrojového kódu v jazyce, který kompilátor rozumí k <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metoda zprostředkovatele CodeDom.  
  
 **Konfigurace parametrů kompilace**  
  
 Všechny standardní metody vyvolání kompilace zprostředkovatele CodeDom mít parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> určující možnosti sloužící ke kompilaci.  
  
 Můžete zadat název souboru pro sestavení výstupu v <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> vlastnost **CompilerParameters**. Jinak bude potřeba použít výchozí název výstupního souboru.  
  
 Ve výchozím nastavení nový **CompilerParameters** inicializován s jeho <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> vlastnost nastavena na hodnotu **false**. Pokud jsou kompilování spustitelný program, je nutné nastavit **GenerateExecutable** vlastnost **true**. Když **GenerateExecutable** je nastaven na **false**, vygeneruje kompilátor knihovny tříd.  
  
 Pokud jsou kompilování spustitelného souboru z grafu modelu CodeDOM, <xref:System.CodeDom.CodeEntryPointMethod> musí být definován v grafu. Pokud existují více vstupních bodů kódu, může být potřeba nastavit <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> vlastnost **CompilerParameters** na název třídy, která definuje vstupní bod používat.  
  
 Chcete-li zahrnout informace o ladění generovaného spustitelný soubor, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> vlastnost, která má **true**.  
  
 Pokud váš projekt odkazuje žádné sestavení, je nutné zadat názvy sestavení jako položky v <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> vlastnost **CompilerParameters** použijete při vyvolání kompilace.  
  
 Zkompilujete sestavení, které je zapsán do paměť a místo na disku podle nastavení <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> vlastnost **true**. Generování sestavení v paměti kódu můžete získat odkaz na generovaného sestavení z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> vlastnost <xref:System.CodeDom.Compiler.CompilerResults>. Pokud sestavení je zapsán do disku, můžete získat cestu vygenerované sestavení z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> vlastnost **CompilerResults**.  
  
 Chcete-li zadat vlastní argumenty příkazového řádku řetězec pro použití při vyvolání kompilaci proces, nastavte řetězec v <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnost.  
  
 Pokud token zabezpečení Win32 je vyžadovaná k vyvolání proces kompilátoru, zadejte token v <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> vlastnost.  
  
 Odkaz zdrojového souboru Win32 do kompilované sestavení, zadejte název zdrojového souboru Win32 ve <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> vlastnost.  
  
 Chcete-li zadat úroveň pro upozornění, kdy má být zastavení kompilace, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> vlastnost na celé číslo, které představuje úroveň pro upozornění, kdy má být zastavení kompilace. Můžete také nakonfigurovat kompilátoru zastavit kompilace, pokud jsou zjištěna upozornění nastavením <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> vlastnost **true**.  
  
 Následující příklad kódu ukazuje kompilování zdrojového souboru pomocí zprostředkovatele CodeDom odvozené z <xref:System.CodeDom.Compiler.CodeDomProvider> třídy.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Jazyky, základem je podpora  
 Rozhraní .NET Framework poskytuje kompilátory kódu a generátory kódu pro následující jazyky: C#, Visual Basic, C++ a JScript. Podpora codeDOM lze rozšířit do jiných jazyků implementací generátory kódu jazyka a kompilátory kódu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [Dynamické vytváření a kompilování zdrojového kódu](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [Stručná referenční příručka modelu codeDOM](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
