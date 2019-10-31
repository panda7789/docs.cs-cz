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
ms.openlocfilehash: 75c86c49f4d471452a7e8f56856d5437e84df307
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084341"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="fe3eb-102">Opožděný podpis sestavení</span><span class="sxs-lookup"><span data-stu-id="fe3eb-102">Delay-sign an assembly</span></span>

<span data-ttu-id="fe3eb-103">Organizace může mít pečlivě chráněný pár klíčů, ke kterým můžou vývojáři získat přístup denně.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="fe3eb-104">Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezený jenom na pár jednotlivců.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="fe3eb-105">Při vývoji sestavení se silnými názvy obsahuje každé sestavení, které odkazuje na cílové sestavení se silným názvem, token veřejného klíče, který slouží k poskytnutí silného názvu cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="fe3eb-106">K tomu je potřeba, aby byl během procesu vývoje dostupný veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="fe3eb-107">Můžete použít zpožděné nebo částečné podepisování v době sestavení a rezervovat tak místo v přenositelném spustitelném souboru (PE) pro podpis silného názvu, ale odložit skutečné přihlášení do pozdější fáze, obvykle těsně před expedicí sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="fe3eb-108">Zpožděné podepsání sestavení:</span><span class="sxs-lookup"><span data-stu-id="fe3eb-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="fe3eb-109">Získejte veřejnou klíčovou část páru klíčů od organizace, která provede případné podepisování.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="fe3eb-110">Obvykle je tento klíč ve formě souboru *. snk* , který lze vytvořit pomocí [nástroje silného názvu (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) , který poskytuje Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="fe3eb-111">Opatřit zdrojový kód pro sestavení pomocí dvou uživatelských atributů z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="fe3eb-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="fe3eb-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, která předá do svého konstruktoru název souboru obsahujícího veřejný klíč jako parametr.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="fe3eb-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, která označuje, že se opožděné podepisování používá předáním **hodnoty true** jako parametru konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="fe3eb-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fe3eb-114">For example:</span></span>

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

3. <span data-ttu-id="fe3eb-115">Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje místo v souboru PE pro úplný podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="fe3eb-116">Skutečný veřejný klíč musí být uložen v době, kdy sestavení je sestaveno, aby ostatní sestavení, která odkazují na toto sestavení, mohla získat klíč pro uložení do vlastního odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="fe3eb-117">Vzhledem k tomu, že sestavení nemá platný podpis silného názvu, musí být ověření podpisu vypnuto.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="fe3eb-118">To můžete provést pomocí možnosti **– VR** s nástrojem Strong Name.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="fe3eb-119">Následující příklad vypne ověřování pro sestavení s názvem *MyAssembly. dll*.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="fe3eb-120">Pokud chcete vypnout ověřování na platformách, u kterých nemůžete spustit nástroj silného názvu, jako jsou mikroprocesory ARM (Advanced RISC Machine), použijte k vytvoření souboru registru možnost **– VK** .</span><span class="sxs-lookup"><span data-stu-id="fe3eb-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="fe3eb-121">Importujte soubor registru do registru v počítači, ve kterém chcete vypnout ověřování.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="fe3eb-122">Následující příklad vytvoří soubor registru pro `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="fe3eb-123">Pomocí možnosti **-VR** nebo **– VK** můžete volitelně zahrnout soubor *. snk* pro podepisování testovacího klíče.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="fe3eb-124">Nespoléhá se na silné názvy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="fe3eb-125">Poskytují pouze jedinečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="fe3eb-126">Použijete-li zpožděné podepisování během vývoje pomocí sady Visual Studio na 64 počítači a zkompilujete sestavení pro **Libovolný procesor**, bude pravděpodobně nutné použít možnost **-VR** dvakrát.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="fe3eb-127">(V aplikaci Visual Studio je **Libovolný procesor** hodnotou vlastnosti sestavení **target Platform** ; při kompilaci z příkazového řádku je to výchozí nastavení.) Chcete-li spustit aplikaci z příkazového řádku nebo z Průzkumníka souborů, použijte 64 verzi programu [sn. exe (nástroj Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md) , chcete-li použít možnost **-VR** pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="fe3eb-128">Chcete-li načíst sestavení do sady Visual Studio v době návrhu (například pokud sestavení obsahuje komponenty, které jsou používány jinými sestaveními v aplikaci), použijte 32 verzi nástroje pro silný název.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="fe3eb-129">Důvodem je, že kompilátor JIT zkompiluje sestavení do 64 bitového nativního kódu při spuštění sestavení z příkazového řádku a do 32 nativního kódu, když je sestavení načteno do prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="fe3eb-130">Později obvykle těsně před expedicí odešlete sestavení do podpisového autority vaší organizace pro skutečný podpis silného názvu pomocí možnosti **– R** s nástrojem silného názvu.</span><span class="sxs-lookup"><span data-stu-id="fe3eb-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="fe3eb-131">Následující příklad podepíše sestavení s názvem *MyAssembly. dll* se silným názvem pomocí páru klíčů *klíči sgKey. snk* .</span><span class="sxs-lookup"><span data-stu-id="fe3eb-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="fe3eb-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe3eb-132">See also</span></span>

- [<span data-ttu-id="fe3eb-133">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="fe3eb-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="fe3eb-134">Postupy: Vytvoření páru veřejného a soukromého klíče</span><span class="sxs-lookup"><span data-stu-id="fe3eb-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="fe3eb-135">SN. exe (Nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="fe3eb-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="fe3eb-136">Program se sestaveními</span><span class="sxs-lookup"><span data-stu-id="fe3eb-136">Program with assemblies</span></span>](program.md)
