---
title: 'Postupy: vytvoření páru veřejného a privátního klíče'
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
ms.openlocfilehash: 08715f2824dcb7dbc2c6aa26fd3bd8bd71b97038
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086280"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="480dd-102">Postupy: vytvoření páru veřejného a privátního klíče</span><span class="sxs-lookup"><span data-stu-id="480dd-102">How to: Create a Public-Private Key Pair</span></span>

<span data-ttu-id="480dd-103">K podepsání sestavení silným názvem, potřebujete pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="480dd-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="480dd-104">Tento pár veřejného a privátního kryptografických klíčů se používá během kompilace k vytvoření sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="480dd-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="480dd-105">Můžete vytvořit, pomocí páru klíčů [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="480dd-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="480dd-106">Soubory párů klíčů mají obvykle .snk rozšíření.</span><span class="sxs-lookup"><span data-stu-id="480dd-106">Key pair files usually have an .snk extension.</span></span>

> [!NOTE]
> <span data-ttu-id="480dd-107">V sadě Visual Studio zahrnují stránky vlastností projektu jazyka C# a Visual Basic **podepisování** kartu, která umožňuje vybrat existující soubory klíčů nebo generování nových klíčů souborů bez použití Sn.exe.</span><span class="sxs-lookup"><span data-stu-id="480dd-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="480dd-108">V jazyce Visual C++ můžete zadat umístění existujícího souboru s klíčem v **Upřesnit** stránku vlastností v **Linkeru** část **vlastnosti konfigurace** část **Stránky vlastností** okna.</span><span class="sxs-lookup"><span data-stu-id="480dd-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="480dd-109">Použití <xref:System.Reflection.AssemblyKeyFileAttribute> atribut k identifikaci souboru klíče dvojice provedl zastaralé od verze Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="480dd-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="to-create-a-key-pair"></a><span data-ttu-id="480dd-110">K vytvoření páru klíčů</span><span class="sxs-lookup"><span data-stu-id="480dd-110">To create a key pair</span></span>

1.  <span data-ttu-id="480dd-111">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="480dd-111">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="480dd-112">**sériové číslo – k** \< *název souboru*></span><span class="sxs-lookup"><span data-stu-id="480dd-112">**sn –k** \<*file name*></span></span>

     <span data-ttu-id="480dd-113">V tomto příkazu *název_souboru* je název výstupního souboru, který obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="480dd-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

 <span data-ttu-id="480dd-114">Následující příklad vytvoří pár klíčů nazvaný `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="480dd-114">The following example creates a key pair called `sgKey.snk`.</span></span>

```
sn -k sgKey.snk
```

 <span data-ttu-id="480dd-115">Pokud máte v úmyslu zpoždění podepsání sestavení a řídit celý pár klíčů (což je pravděpodobně mimo scénáře testování), můžete použít následující příkazy ke generování dvojice klíčů a potom z něj extrahovat veřejný klíč do samostatného souboru.</span><span class="sxs-lookup"><span data-stu-id="480dd-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="480dd-116">Vytvoření páru klíčů:</span><span class="sxs-lookup"><span data-stu-id="480dd-116">First, create the key pair:</span></span>

```
sn -k keypair.snk
```

 <span data-ttu-id="480dd-117">V dalším kroku extrahujte veřejný klíč z páru klíčů a zkopírujte ho do samostatného souboru:</span><span class="sxs-lookup"><span data-stu-id="480dd-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```
sn -p keypair.snk public.snk
```

 <span data-ttu-id="480dd-118">Po vytvoření páru klíčů je nutné umístit tam, kde podepisování silným názvem můžete najít soubor.</span><span class="sxs-lookup"><span data-stu-id="480dd-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

 <span data-ttu-id="480dd-119">Při podepisování sestavení silným názvem, [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) hledá klíče souboru relativní k aktuálnímu adresáři a do výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="480dd-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="480dd-120">Při použití kompilátorů příkazového řádku, můžete jednoduše zkopírovat klíč do aktuálního adresáře, který obsahuje moduly kódu.</span><span class="sxs-lookup"><span data-stu-id="480dd-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

 <span data-ttu-id="480dd-121">Pokud používáte starší verzi sady Visual Studio, který nemá **podepisování** karty ve vlastnostech projektu je soubor klíče se doporučené umístění adresáře projektu s atributem souboru zadaný následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="480dd-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a><span data-ttu-id="480dd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="480dd-122">See Also</span></span>

- [<span data-ttu-id="480dd-123">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="480dd-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
