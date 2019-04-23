---
title: 'Postupy: Vytvoření páru veřejného a privátního klíče'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71eaaa85b8bd287c37f59116e75cf99b030d63ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297834"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Postupy: Vytvoření páru veřejného a privátního klíče

K podepsání sestavení silným názvem, potřebujete pár veřejného a privátního klíče. Tento pár veřejného a privátního kryptografických klíčů se používá během kompilace k vytvoření sestavení se silným názvem. Můžete vytvořit, pomocí páru klíčů [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md). Soubory párů klíčů mají obvykle .snk rozšíření.

> [!NOTE]
> V sadě Visual Studio zahrnují stránky vlastností projektu jazyka C# a Visual Basic **podepisování** kartu, která umožňuje vybrat existující soubory klíčů nebo generování nových klíčů souborů bez použití Sn.exe. V jazyce Visual C++ můžete zadat umístění existujícího souboru s klíčem v **Upřesnit** stránku vlastností v **Linkeru** část **vlastnosti konfigurace** část **Stránky vlastností** okna. Použití <xref:System.Reflection.AssemblyKeyFileAttribute> atribut k identifikaci souboru klíče dvojice provedl zastaralé od verze Visual Studio 2005.

## <a name="to-create-a-key-pair"></a>K vytvoření páru klíčů

1. V příkazovém řádku zadejte následující příkaz:

     **sériové číslo – k** \< *název souboru*>

     V tomto příkazu *název_souboru* je název výstupního souboru, který obsahuje pár klíčů.

 Následující příklad vytvoří pár klíčů nazvaný `sgKey.snk`.

```
sn -k sgKey.snk
```

 Pokud máte v úmyslu zpoždění podepsání sestavení a řídit celý pár klíčů (což je pravděpodobně mimo scénáře testování), můžete použít následující příkazy ke generování dvojice klíčů a potom z něj extrahovat veřejný klíč do samostatného souboru. Vytvoření páru klíčů:

```
sn -k keypair.snk
```

 V dalším kroku extrahujte veřejný klíč z páru klíčů a zkopírujte ho do samostatného souboru:

```
sn -p keypair.snk public.snk
```

 Po vytvoření páru klíčů je nutné umístit tam, kde podepisování silným názvem můžete najít soubor.

 Při podepisování sestavení silným názvem, [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) hledá klíče souboru relativní k aktuálnímu adresáři a do výstupního adresáře. Při použití kompilátorů příkazového řádku, můžete jednoduše zkopírovat klíč do aktuálního adresáře, který obsahuje moduly kódu.

 Pokud používáte starší verzi sady Visual Studio, který nemá **podepisování** karty ve vlastnostech projektu je soubor klíče se doporučené umístění adresáře projektu s atributem souboru zadaný následujícím způsobem:

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a>Viz také:

- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
