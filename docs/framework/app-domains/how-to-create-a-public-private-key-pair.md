---
title: 'Postupy: vytvoření páru veřejného a privátního klíče RSA'
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
ms.openlocfilehash: fe799e15655d4ae1d9d9b7303728b503a5e45082
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741747"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="69c01-102">Postupy: vytvoření páru veřejného a privátního klíče RSA</span><span class="sxs-lookup"><span data-stu-id="69c01-102">How to: Create a Public-Private Key Pair</span></span>
<span data-ttu-id="69c01-103">Pro podepsání sestavení silným názvem, musíte mít pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="69c01-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="69c01-104">Tento pár veřejného a soukromého kryptografické klíče se používá během kompilace k vytvoření sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="69c01-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="69c01-105">Můžete vytvořit pár klíčů pomocí [silný název – nástroj (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="69c01-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="69c01-106">Soubory párů klíčů obvykle mají příponu .snk.</span><span class="sxs-lookup"><span data-stu-id="69c01-106">Key pair files usually have an .snk extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69c01-107">V sadě Visual Studio, zahrnují stránky vlastností projektu C# a Visual Basic **podpisování** kartu, která umožňuje vybrat existující soubory klíčů nebo generování nových klíčů souborů bez použití Sn.exe.</span><span class="sxs-lookup"><span data-stu-id="69c01-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="69c01-108">V jazyce Visual C++, můžete zadat umístění existujícího souboru s klíčem v **Upřesnit** stránka vlastností v **Linkeru** části **vlastnosti konfigurace** části **Stránky vlastností** okno.</span><span class="sxs-lookup"><span data-stu-id="69c01-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="69c01-109">Použití <xref:System.Reflection.AssemblyKeyFileAttribute> atribut k identifikaci soubor klíče dvojice byl proveden zastaralé od verze [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69c01-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
### <a name="to-create-a-key-pair"></a><span data-ttu-id="69c01-110">Chcete-li vytvořit pár klíčů</span><span class="sxs-lookup"><span data-stu-id="69c01-110">To create a key pair</span></span>  
  
1.  <span data-ttu-id="69c01-111">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="69c01-111">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="69c01-112">**sn – k** \< *název souboru*></span><span class="sxs-lookup"><span data-stu-id="69c01-112">**sn –k** \<*file name*></span></span>  
  
     <span data-ttu-id="69c01-113">V tomto příkazu *název souboru* je název výstupního souboru, který obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="69c01-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>  
  
 <span data-ttu-id="69c01-114">Následující příklad vytvoří pár klíčů nazvaný `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="69c01-114">The following example creates a key pair called `sgKey.snk`.</span></span>  
  
```  
sn -k sgKey.snk  
```  
  
 <span data-ttu-id="69c01-115">Pokud máte v úmyslu zpoždění podepsání sestavení a řídit celý pár klíčů (což je pravděpodobně mimo testovací scénáře), můžete použít následující příkazy ke generování páru klíčů a potom z něj extrahujte veřejný klíč do samostatného souboru.</span><span class="sxs-lookup"><span data-stu-id="69c01-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="69c01-116">Nejprve vytvořte dvojici klíčů:</span><span class="sxs-lookup"><span data-stu-id="69c01-116">First, create the key pair:</span></span>  
  
```  
sn -k keypair.snk  
```  
  
 <span data-ttu-id="69c01-117">V dalším kroku extrahovat veřejný klíč z tohoto páru klíčů a zkopírujte jej do samostatného souboru:</span><span class="sxs-lookup"><span data-stu-id="69c01-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>  
  
```  
sn -p keypair.snk public.snk  
```  
  
 <span data-ttu-id="69c01-118">Po vytvoření páru klíčů, je nutné umístit tam, kde podepisování silným názvem můžete najít soubor.</span><span class="sxs-lookup"><span data-stu-id="69c01-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>  
  
 <span data-ttu-id="69c01-119">Při podpisu sestavení se silným názvem, [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) hledá klíč souboru relativní k aktuálnímu adresáři a do výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="69c01-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="69c01-120">Pokud používáte kompilátory příkazového řádku, můžete jednoduše zkopírovat klíč k aktuálnímu adresáři obsahuje moduly kódu.</span><span class="sxs-lookup"><span data-stu-id="69c01-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>  
  
 <span data-ttu-id="69c01-121">Pokud používáte starší verze sady Visual Studio, který nemá **podpisování** karta ve vlastnostech projektu je umístění souboru doporučené klíče adresář projektu s atributem souboru určeným následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="69c01-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="69c01-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="69c01-122">See Also</span></span>  
 [<span data-ttu-id="69c01-123">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="69c01-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
