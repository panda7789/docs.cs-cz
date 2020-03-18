---
title: Opožděný podpis sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733172"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="70fb2-102">Opožděný podpis sestavení</span><span class="sxs-lookup"><span data-stu-id="70fb2-102">Delay-sign an assembly</span></span>

<span data-ttu-id="70fb2-103">Organizace může mít pečlivě střežený pár klíčů, ke kterému vývojáři nemají přístup každý den.</span><span class="sxs-lookup"><span data-stu-id="70fb2-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="70fb2-104">Veřejný klíč je často k dispozici, ale přístup k soukromému klíči je omezen pouze na několik osob.</span><span class="sxs-lookup"><span data-stu-id="70fb2-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="70fb2-105">Při vývoji sestavení se silnými názvy obsahuje každé sestavení, které odkazuje na sestavení cíle se silným názvem, token veřejného klíče, který slouží k tomu, aby cílové sestavení bylo silným názvem.</span><span class="sxs-lookup"><span data-stu-id="70fb2-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="70fb2-106">To vyžaduje, aby veřejný klíč byl k dispozici během procesu vývoje.</span><span class="sxs-lookup"><span data-stu-id="70fb2-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="70fb2-107">Můžete použít zpožděné nebo částečné podepisování v době sestavení k rezervaci místa v přenosném spustitelném souboru (PE) pro podpis silného názvu, ale odložit skutečné podepisování na nějakou pozdější fázi, obvykle těsně před odesláním sestavení.</span><span class="sxs-lookup"><span data-stu-id="70fb2-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="70fb2-108">Zpoždění-podepsat sestavení:</span><span class="sxs-lookup"><span data-stu-id="70fb2-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="70fb2-109">Získejte část veřejného klíče dvojice klíčů od organizace, která bude dělat případné podepisování.</span><span class="sxs-lookup"><span data-stu-id="70fb2-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="70fb2-110">Obvykle je tento klíč ve formě souboru *.snk,* který lze vytvořit pomocí [nástroje Silný název (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) poskytovaného sadou Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="70fb2-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="70fb2-111">Osušte zdrojový kód sestavení dvěma vlastními atributy z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="70fb2-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="70fb2-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, který předá název souboru obsahujícího veřejný klíč jako parametr jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="70fb2-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="70fb2-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, což znamená, že podepisování zpoždění se používá předáním **true** jako parametr jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="70fb2-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="70fb2-114">Například:</span><span class="sxs-lookup"><span data-stu-id="70fb2-114">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="70fb2-115">Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje místo v souboru PE pro úplný podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="70fb2-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="70fb2-116">Skutečný veřejný klíč musí být uložen při sestavení je sestaven tak, aby ostatní sestavení, které odkazují na toto sestavení můžete získat klíč pro uložení v jejich vlastní odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="70fb2-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="70fb2-117">Vzhledem k tomu, že sestavení nemá platný podpis silného názvu, musí být ověření tohoto podpisu vypnuto.</span><span class="sxs-lookup"><span data-stu-id="70fb2-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="70fb2-118">Můžete to udělat pomocí volby **–Vr** s nástrojem Silný název.</span><span class="sxs-lookup"><span data-stu-id="70fb2-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="70fb2-119">Následující příklad vypne ověření pro sestavení s názvem *myAssembly.dll*.</span><span class="sxs-lookup"><span data-stu-id="70fb2-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="70fb2-120">Chcete-li vypnout ověřování na platformách, kde nelze spustit nástroj Silný název, jako jsou mikroprocesory Advanced RISC Machine (ARM), vytvořte soubor registru pomocí možnosti **–Vk.**</span><span class="sxs-lookup"><span data-stu-id="70fb2-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="70fb2-121">Importujte soubor registru do registru v počítači, ve kterém chcete ověření vypnout.</span><span class="sxs-lookup"><span data-stu-id="70fb2-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="70fb2-122">Následující příklad vytvoří soubor `myAssembly.dll`registru pro .</span><span class="sxs-lookup"><span data-stu-id="70fb2-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="70fb2-123">S možností **–Vr** nebo **–Vk** můžete volitelně zahrnout soubor *.snk* pro podepisování testovacího klíče.</span><span class="sxs-lookup"><span data-stu-id="70fb2-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="70fb2-124">Nespoléhejte se na silné názvy pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="70fb2-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="70fb2-125">Poskytují pouze jedinečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="70fb2-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="70fb2-126">Pokud používáte zpoždění podepisování během vývoje s Visual Studio na 64bitový počítač a zkompilovat sestavení pro **libovolný procesor**, budete muset použít **-VR** možnost dvakrát.</span><span class="sxs-lookup"><span data-stu-id="70fb2-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="70fb2-127">(V sadě Visual Studio **je libovolný procesor** hodnotou vlastnosti sestavení Target **platformy;** při kompilaci z příkazového řádku je výchozí.) Chcete-li aplikaci spustit z příkazového řádku nebo z Průzkumníka souborů, použijte 64bitovou verzi [nástroje Sn.exe (nástroj silný název)](../../framework/tools/sn-exe-strong-name-tool.md) k použití možnosti **-Vr** na sestavení.</span><span class="sxs-lookup"><span data-stu-id="70fb2-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="70fb2-128">Chcete-li načíst sestavení do sady Visual Studio v době návrhu (například pokud sestava obsahuje součásti, které jsou používány jinými sestaveními v aplikaci), použijte 32bitovou verzi nástroje silného názvu.</span><span class="sxs-lookup"><span data-stu-id="70fb2-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="70fb2-129">Důvodem je, že kompilátor just-in-time (JIT) zkompiluje sestavení do 64bitového nativního kódu při spuštění sestavení z příkazového řádku a do 32bitového nativního kódu při načtení sestavení do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="70fb2-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="70fb2-130">Později, obvykle těsně před odesláním, odešlete sestavení podpisové autoritě vaší organizace pro skutečné podepisování silného názvu pomocí možnosti **–R** pomocí nástroje Silný název.</span><span class="sxs-lookup"><span data-stu-id="70fb2-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="70fb2-131">Následující příklad podepisuje sestavení s názvem *myAssembly.dll* se silným názvem pomocí dvojice klíčů *sgKey.snk.*</span><span class="sxs-lookup"><span data-stu-id="70fb2-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="70fb2-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="70fb2-132">See also</span></span>

- [<span data-ttu-id="70fb2-133">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="70fb2-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="70fb2-134">Postup: Vytvoření páru klíčů veřejného a soukromého sektoru</span><span class="sxs-lookup"><span data-stu-id="70fb2-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="70fb2-135">Sn.exe (nástroj silný název)</span><span class="sxs-lookup"><span data-stu-id="70fb2-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
