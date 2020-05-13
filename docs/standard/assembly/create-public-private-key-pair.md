---
title: 'Postupy: Vytvoření páru veřejného a soukromého klíče'
description: Naučte se vytvořit veřejný a privátní pár kryptografických klíčů, který se použije při kompilaci k vytvoření sestavení se silným názvem.
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 675871170e7fd4171f0fe09b04d1dbb8906beda4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378553"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Postupy: Vytvoření páru veřejného a soukromého klíče

Pro podepsání sestavení silným názvem musíte mít dvojici veřejného a privátního klíče. Tento pár veřejného a privátního kryptografického klíče se používá během kompilace k vytvoření sestavení se silným názvem. Můžete vytvořit pár klíčů pomocí [nástroje Strong Name (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md). Soubory dvojice klíčů mají obvykle příponu *. snk* .

> [!NOTE]
> V aplikaci Visual Studio stránky vlastností projektu C# a Visual Basic zahrnují kartu **podepisování** , která umožňuje vybrat existující soubory klíčů nebo vygenerovat nové soubory klíčů bez použití *sn. exe*. V Visual C++ můžete zadat umístění existujícího souboru klíče na stránce **Upřesnit** vlastnost v oddílu **linker** v části **Vlastnosti konfigurace** okna **stránky vlastností** . Použití <xref:System.Reflection.AssemblyKeyFileAttribute> atributu k identifikaci párů klíčových souborů bylo od sady Visual Studio 2005 zastaralo.

## <a name="create-a-key-pair"></a>Vytvoření páru klíčů

Pokud chcete vytvořit pár klíčů, zadejte na příkazovém řádku tento příkaz:

**sn – k** \< *název souboru*>

V tomto příkazu *název souboru* je název výstupního souboru obsahujícího dvojici klíčů.

Následující příklad vytvoří dvojici klíčů s názvem *klíči sgKey. snk*.

```cmd
sn -k sgKey.snk
```

Pokud máte v úmyslu zpozdit podpis sestavení a Vy ovládáte celý pár klíčů (což je nepravděpodobné mimo testovací scénáře), můžete pomocí následujících příkazů vygenerovat pár klíčů a potom z něj extrahovat veřejný klíč do samostatného souboru. Nejdřív vytvořte pár klíčů:

```cmd
sn -k keypair.snk
```

Dále z páru klíčů rozbalte veřejný klíč a zkopírujte ho do samostatného souboru:

```cmd
sn -p keypair.snk public.snk
```

Po vytvoření páru klíčů je nutné umístit soubor, ve kterém nástroj pro podepisování silných názvů je může najít.

Při podepisování sestavení silným názvem [linker sestavení (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) vyhledá soubor klíče relativně k aktuálnímu adresáři a výstupnímu adresáři. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat klíč do aktuálního adresáře, který obsahuje moduly kódu.

Pokud používáte starší verzi sady Visual Studio, která nemá kartu **podepisování** ve vlastnostech projektu, doporučené umístění souboru klíče je adresář projektu se zadaným atributem souboru, a to takto:

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Viz také

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
