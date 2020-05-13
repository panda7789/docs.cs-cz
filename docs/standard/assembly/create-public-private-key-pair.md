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
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="e8f5a-103">Postupy: Vytvoření páru veřejného a soukromého klíče</span><span class="sxs-lookup"><span data-stu-id="e8f5a-103">How to: Create a public-private key pair</span></span>

<span data-ttu-id="e8f5a-104">Pro podepsání sestavení silným názvem musíte mít dvojici veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-104">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="e8f5a-105">Tento pár veřejného a privátního kryptografického klíče se používá během kompilace k vytvoření sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-105">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="e8f5a-106">Můžete vytvořit pár klíčů pomocí [nástroje Strong Name (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e8f5a-106">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="e8f5a-107">Soubory dvojice klíčů mají obvykle příponu *. snk* .</span><span class="sxs-lookup"><span data-stu-id="e8f5a-107">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="e8f5a-108">V aplikaci Visual Studio stránky vlastností projektu C# a Visual Basic zahrnují kartu **podepisování** , která umožňuje vybrat existující soubory klíčů nebo vygenerovat nové soubory klíčů bez použití *sn. exe*.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-108">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="e8f5a-109">V Visual C++ můžete zadat umístění existujícího souboru klíče na stránce **Upřesnit** vlastnost v oddílu **linker** v části **Vlastnosti konfigurace** okna **stránky vlastností** .</span><span class="sxs-lookup"><span data-stu-id="e8f5a-109">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="e8f5a-110">Použití <xref:System.Reflection.AssemblyKeyFileAttribute> atributu k identifikaci párů klíčových souborů bylo od sady Visual Studio 2005 zastaralo.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-110">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="e8f5a-111">Vytvoření páru klíčů</span><span class="sxs-lookup"><span data-stu-id="e8f5a-111">Create a key pair</span></span>

<span data-ttu-id="e8f5a-112">Pokud chcete vytvořit pár klíčů, zadejte na příkazovém řádku tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="e8f5a-112">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="e8f5a-113">**sn – k** \< *název souboru*></span><span class="sxs-lookup"><span data-stu-id="e8f5a-113">**sn –k** \<*file name*></span></span>

<span data-ttu-id="e8f5a-114">V tomto příkazu *název souboru* je název výstupního souboru obsahujícího dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-114">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="e8f5a-115">Následující příklad vytvoří dvojici klíčů s názvem *klíči sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-115">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="e8f5a-116">Pokud máte v úmyslu zpozdit podpis sestavení a Vy ovládáte celý pár klíčů (což je nepravděpodobné mimo testovací scénáře), můžete pomocí následujících příkazů vygenerovat pár klíčů a potom z něj extrahovat veřejný klíč do samostatného souboru.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-116">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="e8f5a-117">Nejdřív vytvořte pár klíčů:</span><span class="sxs-lookup"><span data-stu-id="e8f5a-117">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="e8f5a-118">Dále z páru klíčů rozbalte veřejný klíč a zkopírujte ho do samostatného souboru:</span><span class="sxs-lookup"><span data-stu-id="e8f5a-118">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="e8f5a-119">Po vytvoření páru klíčů je nutné umístit soubor, ve kterém nástroj pro podepisování silných názvů je může najít.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-119">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="e8f5a-120">Při podepisování sestavení silným názvem [linker sestavení (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) vyhledá soubor klíče relativně k aktuálnímu adresáři a výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-120">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="e8f5a-121">Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat klíč do aktuálního adresáře, který obsahuje moduly kódu.</span><span class="sxs-lookup"><span data-stu-id="e8f5a-121">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="e8f5a-122">Pokud používáte starší verzi sady Visual Studio, která nemá kartu **podepisování** ve vlastnostech projektu, doporučené umístění souboru klíče je adresář projektu se zadaným atributem souboru, a to takto:</span><span class="sxs-lookup"><span data-stu-id="e8f5a-122">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="e8f5a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8f5a-123">See also</span></span>

- [<span data-ttu-id="e8f5a-124">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="e8f5a-124">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
