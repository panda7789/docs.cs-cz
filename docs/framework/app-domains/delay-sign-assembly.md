---
title: "Zpoždění podepsání sestavení"
ms.date: 07/31/2017
ms.prod: .net-framework
ms.technology: dotnet-bcl
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08f0f48a71415878cd24640272a41de4c0a5ade6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="63ec3-102">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="63ec3-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="63ec3-103">Organizace může mít úzce chráněného pár klíčů, vývojáři nemá přístup k každý den.</span><span class="sxs-lookup"><span data-stu-id="63ec3-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="63ec3-104">Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezen na pouze několika jednotlivcům.</span><span class="sxs-lookup"><span data-stu-id="63ec3-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="63ec3-105">Při vývoji sestavení se silnými názvy, každé sestavení tohoto sestavení cíl odkazy silným názvem obsahuje token veřejného klíče dávat cíl sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="63ec3-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="63ec3-106">To vyžaduje, aby veřejný klíč k dispozici během procesu vývoje.</span><span class="sxs-lookup"><span data-stu-id="63ec3-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="63ec3-107">Rezerva místa v přenosné spustitelný soubor (PE) pro podpis silného názvu, ale odložené podepisování do některé pozdější fázi (obvykle jen před přesouvání sestavení) můžete použít zpožděné nebo částečné podepsání v čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="63ec3-108">Následující kroky popisují proces zpoždění podepsání sestavení:</span><span class="sxs-lookup"><span data-stu-id="63ec3-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1.  <span data-ttu-id="63ec3-109">Získejte veřejnou část klíče páru klíčů z organizace, která provede případné podepsání.</span><span class="sxs-lookup"><span data-stu-id="63ec3-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="63ec3-110">Tento klíč je obvykle ve formátu souboru .snk, který lze vytvořit pomocí [silný název – nástroj (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63ec3-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2.  <span data-ttu-id="63ec3-111">Opatřete zdrojový kód pro sestavení dvěma vlastními atributy z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="63ec3-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <span data-ttu-id="63ec3-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, který předává název souboru, který obsahuje veřejný klíč jako parametr jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="63ec3-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <span data-ttu-id="63ec3-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, což naznačuje, že zpožděné podepisování je používáno předáním **true** jako parametr jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="63ec3-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="63ec3-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="63ec3-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  <span data-ttu-id="63ec3-115">Kompilátor vloží veřejný klíč do manifestu a rezervy místa v souboru PE podpis úplné silného názvu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="63ec3-116">Reálný veřejný klíč musí být uložen při sestavení je sestaven tak, aby ostatních sestavení, které odkazují na toto sestavení můžete získat klíč, který chcete uložit do své vlastní odkaz sestavení.</span><span class="sxs-lookup"><span data-stu-id="63ec3-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4.  <span data-ttu-id="63ec3-117">Protože sestavení nemá podpis platný silného názvu, musí být vypnutý ověřování tohoto podpisu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="63ec3-118">Můžete to provést pomocí **– Vr** možnost pomocí nástroje silného názvu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="63ec3-119">Následující příklad vypne ověřování pro sestavení nazvané `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="63ec3-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="63ec3-120">Chcete-li vypnout ověření na platformách, kde nelze spustit nástroje pro silný název, jako je například procesory Advanced RISC Machine (ARM), použijte **– Vk** možnost vytvořte soubor registru.</span><span class="sxs-lookup"><span data-stu-id="63ec3-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="63ec3-121">Importujte soubor registru do registru na počítači, ve které chcete vypnout ověření.</span><span class="sxs-lookup"><span data-stu-id="63ec3-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="63ec3-122">Následující příklad vytvoří soubor registru pro `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="63ec3-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="63ec3-123">Pomocí **– Vr** nebo **– Vk** možnost, může volitelně obsahovat soubor .snk pro test klíče podepisování.</span><span class="sxs-lookup"><span data-stu-id="63ec3-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="63ec3-124">Nespoléhejte na silné názvy pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="63ec3-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="63ec3-125">Obsahují jenom jedinečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="63ec3-126">Pokud používáte zpoždění podepsání během vývoje pomocí sady Visual Studio na 64bitovém počítači, a kompilaci sestavení pro **libovolný procesor**, možná budete muset použít **- Vr** možnost dvakrát.</span><span class="sxs-lookup"><span data-stu-id="63ec3-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="63ec3-127">(V sadě Visual Studio, **libovolný procesor** je hodnota **Cílová platforma** vlastnost sestavení, když kompilujete z příkazového řádku, je výchozí.) Pokud chcete aplikaci spustit z příkazového řádku nebo z Průzkumníka souborů, použijte 64bitové verze [Sn.exe (nástroj silným názvem)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pro použití **- Vr** možnost sestavení.</span><span class="sxs-lookup"><span data-stu-id="63ec3-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="63ec3-128">K načtení sestavení do sady Visual Studio v době návrhu (například pokud sestavení obsahuje součásti, které jsou používány jiné sestavení v aplikaci), použijte 32bitovou verzi nástroje silného názvu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="63ec3-129">To je proto kompilátoru za běhu (JIT) kompiluje sestavení 64-bit nativního kódu při spuštění sestavení z příkazového řádku a nativní kód 32-bit při sestavení načtení do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5.  <span data-ttu-id="63ec3-130">Později, obvykle těsně před jejich odesláním, odešlete sestavení pro vaši organizaci podepisovací autority pro aktuální podepsání pomocí silného názvu **– R** možnost pomocí nástroje silného názvu.</span><span class="sxs-lookup"><span data-stu-id="63ec3-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="63ec3-131">Následující příklad podepíše sestavení nazvané `myAssembly.dll` se silným názvem pomocí `sgKey.snk` dvojice klíčů.</span><span class="sxs-lookup"><span data-stu-id="63ec3-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="63ec3-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="63ec3-132">See Also</span></span>  
 [<span data-ttu-id="63ec3-133">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="63ec3-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="63ec3-134">Postupy: vytvoření páru veřejného a privátního klíče RSA</span><span class="sxs-lookup"><span data-stu-id="63ec3-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="63ec3-135">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="63ec3-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="63ec3-136">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="63ec3-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
