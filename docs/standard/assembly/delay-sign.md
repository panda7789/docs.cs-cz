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
# <a name="delay-sign-an-assembly"></a>Opožděný podpis sestavení

Organizace může mít pečlivě střežený pár klíčů, ke kterému vývojáři nemají přístup každý den. Veřejný klíč je často k dispozici, ale přístup k soukromému klíči je omezen pouze na několik osob. Při vývoji sestavení se silnými názvy obsahuje každé sestavení, které odkazuje na sestavení cíle se silným názvem, token veřejného klíče, který slouží k tomu, aby cílové sestavení bylo silným názvem. To vyžaduje, aby veřejný klíč byl k dispozici během procesu vývoje.

Můžete použít zpožděné nebo částečné podepisování v době sestavení k rezervaci místa v přenosném spustitelném souboru (PE) pro podpis silného názvu, ale odložit skutečné podepisování na nějakou pozdější fázi, obvykle těsně před odesláním sestavení.

Zpoždění-podepsat sestavení:

1. Získejte část veřejného klíče dvojice klíčů od organizace, která bude dělat případné podepisování. Obvykle je tento klíč ve formě souboru *.snk,* který lze vytvořit pomocí [nástroje Silný název (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) poskytovaného sadou Windows SDK.

2. Osušte zdrojový kód sestavení dvěma vlastními atributy z <xref:System.Reflection>:

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, který předá název souboru obsahujícího veřejný klíč jako parametr jeho konstruktoru.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, což znamená, že podepisování zpoždění se používá předáním **true** jako parametr jeho konstruktoru.

   Například:

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

3. Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje místo v souboru PE pro úplný podpis silného názvu. Skutečný veřejný klíč musí být uložen při sestavení je sestaven tak, aby ostatní sestavení, které odkazují na toto sestavení můžete získat klíč pro uložení v jejich vlastní odkaz na sestavení.

4. Vzhledem k tomu, že sestavení nemá platný podpis silného názvu, musí být ověření tohoto podpisu vypnuto. Můžete to udělat pomocí volby **–Vr** s nástrojem Silný název.

     Následující příklad vypne ověření pro sestavení s názvem *myAssembly.dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Chcete-li vypnout ověřování na platformách, kde nelze spustit nástroj Silný název, jako jsou mikroprocesory Advanced RISC Machine (ARM), vytvořte soubor registru pomocí možnosti **–Vk.** Importujte soubor registru do registru v počítači, ve kterém chcete ověření vypnout. Následující příklad vytvoří soubor `myAssembly.dll`registru pro .

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   S možností **–Vr** nebo **–Vk** můžete volitelně zahrnout soubor *.snk* pro podepisování testovacího klíče.

   > [!WARNING]
   > Nespoléhejte se na silné názvy pro zabezpečení. Poskytují pouze jedinečnou identitu.

   > [!NOTE]
   > Pokud používáte zpoždění podepisování během vývoje s Visual Studio na 64bitový počítač a zkompilovat sestavení pro **libovolný procesor**, budete muset použít **-VR** možnost dvakrát. (V sadě Visual Studio **je libovolný procesor** hodnotou vlastnosti sestavení Target **platformy;** při kompilaci z příkazového řádku je výchozí.) Chcete-li aplikaci spustit z příkazového řádku nebo z Průzkumníka souborů, použijte 64bitovou verzi [nástroje Sn.exe (nástroj silný název)](../../framework/tools/sn-exe-strong-name-tool.md) k použití možnosti **-Vr** na sestavení. Chcete-li načíst sestavení do sady Visual Studio v době návrhu (například pokud sestava obsahuje součásti, které jsou používány jinými sestaveními v aplikaci), použijte 32bitovou verzi nástroje silného názvu. Důvodem je, že kompilátor just-in-time (JIT) zkompiluje sestavení do 64bitového nativního kódu při spuštění sestavení z příkazového řádku a do 32bitového nativního kódu při načtení sestavení do prostředí návrhu.

5. Později, obvykle těsně před odesláním, odešlete sestavení podpisové autoritě vaší organizace pro skutečné podepisování silného názvu pomocí možnosti **–R** pomocí nástroje Silný název.

   Následující příklad podepisuje sestavení s názvem *myAssembly.dll* se silným názvem pomocí dvojice klíčů *sgKey.snk.*

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Viz také

- [Vytváření sestavení](create.md)
- [Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](create-public-private-key-pair.md)
- [Sn.exe (nástroj silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
