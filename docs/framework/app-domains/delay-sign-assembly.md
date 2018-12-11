---
title: Zpoždění podepsání sestavení
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87346b28ff98c453949fe31aea4d0ef1880b0095
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152289"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="e12c3-102">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="e12c3-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="e12c3-103">Organizace může mít úzce strážených pár klíčů, že vývojáři nebudou mít přístup k každý den.</span><span class="sxs-lookup"><span data-stu-id="e12c3-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="e12c3-104">Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezen pouze několika jednotlivcům.</span><span class="sxs-lookup"><span data-stu-id="e12c3-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="e12c3-105">Při vývoji podepisují sestavení silnými názvy, každé sestavení této cílové sestavení silným názvem odkazy obsahuje token veřejný klíč slouží k pojmenování cílové sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e12c3-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="e12c3-106">To vyžaduje veřejný klíč k dispozici během procesu vývoje.</span><span class="sxs-lookup"><span data-stu-id="e12c3-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="e12c3-107">Zpožděné nebo částečné podepisování v okamžiku sestavení můžete použít k rezervaci místa do přenosného spustitelného souboru (PE) pro podpis silného názvu, ale odložit podepisování do některých později (obvykle pouze před dodáním sestavení).</span><span class="sxs-lookup"><span data-stu-id="e12c3-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="e12c3-108">Následující kroky popisují postup odložení sestavení:</span><span class="sxs-lookup"><span data-stu-id="e12c3-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1.  <span data-ttu-id="e12c3-109">Získáte část s veřejným klíčem z dvojice klíčů z organizace, která provede konečnou podepisování.</span><span class="sxs-lookup"><span data-stu-id="e12c3-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="e12c3-110">Tento klíč je obvykle ve formě souboru .snk, které je možné vytvořit [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e12c3-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2.  <span data-ttu-id="e12c3-111">Přidat poznámku zdrojového kódu pro sestavení pomocí dvou vlastních atributů z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="e12c3-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <span data-ttu-id="e12c3-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, který předává název souboru, který obsahuje veřejný klíč jako parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e12c3-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <span data-ttu-id="e12c3-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, což znamená, že zpožděné podepisování se používá předáním **true** jako parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e12c3-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="e12c3-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e12c3-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  <span data-ttu-id="e12c3-115">Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje prostor v souboru PE pro podpis úplné silného názvu.</span><span class="sxs-lookup"><span data-stu-id="e12c3-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="e12c3-116">Reálný veřejný klíč musí být uložen, zatímco sestavení je vytvořený tak, aby jiná sestavení, které odkazují na toto sestavení můžete získat klíč, který chcete uložit do své vlastní odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="e12c3-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4.  <span data-ttu-id="e12c3-117">Protože sestavení nemá silný název platný podpis, musí být vypnutý ověření podpisu.</span><span class="sxs-lookup"><span data-stu-id="e12c3-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="e12c3-118">Můžete to provést pomocí **– Vr** parametrem nástroj Strong Name.</span><span class="sxs-lookup"><span data-stu-id="e12c3-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="e12c3-119">Následující příklad vypne ověření pro sestavení nazvané `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e12c3-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="e12c3-120">Chcete-li vypnout ověřování na platformách, kde nelze spustit nástroj Strong Name, jako je například mikroprocesory Advanced RISC Machine (ARM), použijte **– Vk** možnost vytvořit soubor registru.</span><span class="sxs-lookup"><span data-stu-id="e12c3-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="e12c3-121">Importujte soubor registru do registru na počítači, ve které chcete vypnout ověřování.</span><span class="sxs-lookup"><span data-stu-id="e12c3-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="e12c3-122">Následující příklad vytvoří soubor registru pro `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e12c3-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="e12c3-123">Buď **– Vr** nebo **– Vk** možnost, může volitelně zahrnovat souboru .snk pro testovací podpis klíče.</span><span class="sxs-lookup"><span data-stu-id="e12c3-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="e12c3-124">Nespoléhejte na silných názvů pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e12c3-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="e12c3-125">Poskytují jedinečné identity.</span><span class="sxs-lookup"><span data-stu-id="e12c3-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="e12c3-126">Pokud používáte zpoždění podepsání během vývoje pomocí sady Visual Studio na 64bitovém počítači, a kompilace sestavení pro **jakýkoli procesor**, bude pravděpodobně nutné použít **- Vr** možnost dvakrát.</span><span class="sxs-lookup"><span data-stu-id="e12c3-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="e12c3-127">(V sadě Visual Studio **jakýkoli procesor** je hodnota **Cílová platforma** vlastnost sestavení; při kompilaci z příkazového řádku, je výchozí nastavení.) Ke spuštění aplikace z příkazového řádku nebo z Průzkumníka souborů, použijte verzi 64-bit [Sn.exe (nástroj Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) použít **- Vr** možnost sestavení.</span><span class="sxs-lookup"><span data-stu-id="e12c3-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="e12c3-128">K načtení sestavení do sady Visual Studio v době návrhu (například, pokud sestavení obsahuje součásti, které jsou používány jiné sestavení ve vaší aplikaci), pomocí 32bitové verze nástroj pro silný název.</span><span class="sxs-lookup"><span data-stu-id="e12c3-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="e12c3-129">Je to proto, že kompilátor just-in-time (JIT) kompiluje sestavení do nativního kódu 64-bit při spuštění sestavení z příkazového řádku a do nativního kódu 32-bit při sestavení je načteno do návrhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="e12c3-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5.  <span data-ttu-id="e12c3-130">Později, obvykle těsně před předáním, odešlete sestavení pro vaši organizaci podepisovací autority pro aktuální podepsání pomocí silného názvu **– R** parametrem nástroj Strong Name.</span><span class="sxs-lookup"><span data-stu-id="e12c3-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="e12c3-131">Následující příklad podepíše sestavení nazvané `myAssembly.dll` se silným názvem pomocí `sgKey.snk` pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="e12c3-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e12c3-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e12c3-132">See Also</span></span>  
- [<span data-ttu-id="e12c3-133">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="e12c3-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="e12c3-134">Jak: Vytvoření páru veřejného a privátního klíče</span><span class="sxs-lookup"><span data-stu-id="e12c3-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
- [<span data-ttu-id="e12c3-135">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="e12c3-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
- [<span data-ttu-id="e12c3-136">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="e12c3-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
