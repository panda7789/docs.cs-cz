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
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="5b9c4-102">Postup: Vytvoření páru klíčů veřejného a soukromého sektoru</span><span class="sxs-lookup"><span data-stu-id="5b9c4-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="5b9c4-103">Chcete-li podepsat sestavení se silným názvem, musíte mít dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="5b9c4-104">Tento veřejný a soukromý pár kryptografických klíčů se používá během kompilace k vytvoření sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="5b9c4-105">Pár klíčů můžete vytvořit pomocí [nástroje Silný název (Sn.exe).](../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="5b9c4-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="5b9c4-106">Soubory dvojice klíčů mají obvykle příponu *SNK.*</span><span class="sxs-lookup"><span data-stu-id="5b9c4-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9c4-107">V sadě Visual Studio obsahují stránky vlastností projektu jazyka C# a Visual Basic kartu **Podepisování,** která umožňuje vybrat existující klíčové soubory nebo generovat nové soubory klíčů bez použití *programu Sn.exe*.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="5b9c4-108">V jazyce Visual C++ můžete určit umístění existujícího souboru klíče na stránce **Vlastností Upřesnit** v části **Propojovací program** v části **Vlastnosti konfigurace** v okně **Stránky vlastností.**</span><span class="sxs-lookup"><span data-stu-id="5b9c4-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="5b9c4-109">Použití atributu <xref:System.Reflection.AssemblyKeyFileAttribute> k identifikaci párů souborů klíčů bylo zastaralé počínaje visual studio 2005.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="5b9c4-110">Vytvoření páru klíčů</span><span class="sxs-lookup"><span data-stu-id="5b9c4-110">Create a key pair</span></span>

<span data-ttu-id="5b9c4-111">Chcete-li vytvořit dvojici klíčů, zadejte na příkazovém řádku následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5b9c4-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="5b9c4-112">**sn –k** \< *název souboru*></span><span class="sxs-lookup"><span data-stu-id="5b9c4-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="5b9c4-113">V tomto příkazu je *název souboru* výstupního souboru obsahujícího dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="5b9c4-114">Následující příklad vytvoří dvojici klíčů nazvanou *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="5b9c4-115">Pokud máte v úmyslu zpozdit podepsat sestavení a řídit celý pár klíčů (což je nepravděpodobné, mimo testovací scénáře), můžete použít následující příkazy ke generování dvojice klíčů a potom extrahovat veřejný klíč z něj do samostatného souboru.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="5b9c4-116">Nejprve vytvořte dvojici klíčů:</span><span class="sxs-lookup"><span data-stu-id="5b9c4-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="5b9c4-117">Dále extrahujte veřejný klíč z dvojice klíčů a zkopírujte jej do samostatného souboru:</span><span class="sxs-lookup"><span data-stu-id="5b9c4-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="5b9c4-118">Jakmile vytvoříte dvojici klíčů, musíte soubor umístit tam, kde jej mohou najít nástroje pro podepisování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="5b9c4-119">Při podepisování sestavení se silným názvem hledá [linker sestavení (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) soubor klíče vzhledem k aktuálnímu adresáři a výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="5b9c4-120">Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat klíč do aktuálního adresáře obsahujícího moduly kódu.</span><span class="sxs-lookup"><span data-stu-id="5b9c4-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="5b9c4-121">Pokud používáte starší verzi sady Visual Studio, která nemá kartu **Podepisování** ve vlastnostech projektu, je doporučeným umístěním souboru klíče adresář projektu s atributem souboru určeným následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b9c4-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="5b9c4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b9c4-122">See also</span></span>

- [<span data-ttu-id="5b9c4-123">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="5b9c4-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
