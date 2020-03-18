---
title: 'Postup: Vytvoření páru klíčů veřejného a soukromého sektoru'
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
ms.openlocfilehash: 8a9845e3cd18ff86ec04216ad0e9c5606186b113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122522"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Postup: Vytvoření páru klíčů veřejného a soukromého sektoru

Chcete-li podepsat sestavení se silným názvem, musíte mít dvojici veřejného a soukromého klíče. Tento veřejný a soukromý pár kryptografických klíčů se používá během kompilace k vytvoření sestavení se silným názvem. Pár klíčů můžete vytvořit pomocí [nástroje Silný název (Sn.exe).](../../framework/tools/sn-exe-strong-name-tool.md) Soubory dvojice klíčů mají obvykle příponu *SNK.*

> [!NOTE]
> V sadě Visual Studio obsahují stránky vlastností projektu jazyka C# a Visual Basic kartu **Podepisování,** která umožňuje vybrat existující klíčové soubory nebo generovat nové soubory klíčů bez použití *programu Sn.exe*. V jazyce Visual C++ můžete určit umístění existujícího souboru klíče na stránce **Vlastností Upřesnit** v části **Propojovací program** v části **Vlastnosti konfigurace** v okně **Stránky vlastností.** Použití atributu <xref:System.Reflection.AssemblyKeyFileAttribute> k identifikaci párů souborů klíčů bylo zastaralé počínaje visual studio 2005.

## <a name="create-a-key-pair"></a>Vytvoření páru klíčů

Chcete-li vytvořit dvojici klíčů, zadejte na příkazovém řádku následující příkaz:

**sn –k** \< *název souboru*>

V tomto příkazu je *název souboru* výstupního souboru obsahujícího dvojici klíčů.

Následující příklad vytvoří dvojici klíčů nazvanou *sgKey.snk*.

```cmd
sn -k sgKey.snk
```

Pokud máte v úmyslu zpozdit podepsat sestavení a řídit celý pár klíčů (což je nepravděpodobné, mimo testovací scénáře), můžete použít následující příkazy ke generování dvojice klíčů a potom extrahovat veřejný klíč z něj do samostatného souboru. Nejprve vytvořte dvojici klíčů:

```cmd
sn -k keypair.snk
```

Dále extrahujte veřejný klíč z dvojice klíčů a zkopírujte jej do samostatného souboru:

```cmd
sn -p keypair.snk public.snk
```

Jakmile vytvoříte dvojici klíčů, musíte soubor umístit tam, kde jej mohou najít nástroje pro podepisování silných názvů.

Při podepisování sestavení se silným názvem hledá [linker sestavení (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) soubor klíče vzhledem k aktuálnímu adresáři a výstupnímu adresáři. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat klíč do aktuálního adresáře obsahujícího moduly kódu.

Pokud používáte starší verzi sady Visual Studio, která nemá kartu **Podepisování** ve vlastnostech projektu, je doporučeným umístěním souboru klíče adresář projektu s atributem souboru určeným následujícím způsobem:

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
