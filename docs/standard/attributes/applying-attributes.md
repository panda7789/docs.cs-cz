---
title: Použití atributů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 14cd6fef80ff9ae3a9d78531785edab0da7cc6b9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130919"
---
# <a name="applying-attributes"></a>Použití atributů
Na základě následujícího postupu použijte atribut na prvek kódu.  
  
1. Definujte nový atribut nebo použijte stávající atribut importováním oboru názvů z rozhraní .NET Framework.  
  
2. Použijte atribut na prvek kódu tak, že ho umístíte bezprostředně před prvek.  
  
     Jednotlivé jazyky mají vlastní syntaxi atributů. V jazyce C++ a jazyce C# je atribut ohraničen hranatými závorkami a oddělen od prvku prázdným znakem, který může obsahovat konec řádku. V jazyce Visual Basic je atribut ohraničen ostrými závorkami a musí být umístěn na stejném logickém řádku. Znak pro pokračování řádku lze použít v případě, že je vyžadován konec řádku.
  
3. Zadejte poziční parametry a pojmenované parametry atributu.  
  
     Poziční parametry jsou povinné a musí předcházet jakýmkoli pojmenovaným parametrům – odpovídají parametrům jednoho z konstruktorů atributu. Pojmenované parametry jsou volitelné a odpovídají vlastnostem atributu pro čtení a zápis. V C++a C#zadejte `name`=`value` pro každý volitelný parametr, kde `name` je název vlastnosti. V jazyce Visual Basic zadejte `name`:=`value`.  
  
 Atribut je při kompilaci kódu vložen do metadat a je k dispozici pro modul CLR (Common Language Runtime) a vlastní nástroje nebo aplikace prostřednictvím služeb reflexe runtime.  
  
 Na základě pravidel zadávání názvů končí všechny názvy atributů slovem Attribute. Avšak několik jazyků, které používají modul runtime, jako jsou například Visual Basic a C#, nevyžadují zadávání úplného názvu atributu. Například pokud chcete inicializovat <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, stačí na něj odkazovat jako na **zastaralé**.  
  
## <a name="applying-an-attribute-to-a-method"></a>Použití atributu na metodu  
 Následující příklad kódu ukazuje, jak deklarovat **System. ObsoleteAttribute**, který označuje kód jako zastaralý. Řetězec `"Will be removed in next version"` je předán atributu. Tento atribut vygeneruje upozornění kompilátoru, které zobrazí předaný řetězec, pokud je volán kód popisovaný atributem.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Používání atributů na úrovni sestavení  
 Chcete-li použít atribut na úrovni sestavení, použijte klíčové slovo **Assembly** (`Assembly` in Visual Basic). Následující kód ukazuje **AssemblyTitleAttribute** použitou na úrovni sestavení.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Pokud použijete tento atribut, bude řetězec `"My Assembly"` umístěn v manifestu sestavení v části souboru s metadaty. Atribut můžete zobrazit buď pomocí [jazyka MSIL Disassembler (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) , nebo vytvořením vlastního programu pro načtení atributu.  
  
## <a name="see-also"></a>Viz také:

- [Atributy](../../../docs/standard/attributes/index.md)
- [Načítání informací uložených v atributech](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)
- [Charakteristiky](/cpp/windows/attributed-programming-concepts)
- [Atributy (C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [Přehled atributů (Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)
