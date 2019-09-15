---
title: Zpožděný podpis sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: e7679520e246ab3eda03e6f0e0d092c7d09f1845
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991321"
---
# <a name="delay-sign-an-assembly"></a>Zpožděný podpis sestavení

Organizace může mít pečlivě chráněný pár klíčů, ke kterým můžou vývojáři získat přístup denně. Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezený jenom na pár jednotlivců. Při vývoji sestavení se silnými názvy obsahuje každé sestavení, které odkazuje na cílové sestavení se silným názvem, token veřejného klíče, který slouží k poskytnutí silného názvu cílového sestavení. K tomu je potřeba, aby byl během procesu vývoje dostupný veřejný klíč.

Můžete použít zpožděné nebo částečné podepisování v době sestavení a rezervovat tak místo v přenositelném spustitelném souboru (PE) pro podpis silného názvu, ale odložit skutečné přihlášení do pozdější fáze, obvykle těsně před expedicí sestavení.

Zpožděné podepsání sestavení:

1. Získejte veřejnou klíčovou část páru klíčů od organizace, která provede případné podepisování. Obvykle je tento klíč ve formě souboru *. snk* , který lze vytvořit pomocí [nástroje silného názvu (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) , který poskytuje Windows SDK.

2. Opatřit zdrojový kód sestavení zadáním dvou vlastních atributů z <xref:System.Reflection>:

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, který předá název souboru obsahujícího veřejný klíč jako parametr konstruktoru.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, což znamená, že je použito Zpožděné podepsání předáním **hodnoty true** jako parametru konstruktoru.

   Příklad:

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

3. Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje místo v souboru PE pro úplný podpis silného názvu. Skutečný veřejný klíč musí být uložen v době, kdy sestavení je sestaveno, aby ostatní sestavení, která odkazují na toto sestavení, mohla získat klíč pro uložení do vlastního odkazu na sestavení.

4. Vzhledem k tomu, že sestavení nemá platný podpis silného názvu, musí být ověření podpisu vypnuto. To můžete provést pomocí možnosti **– VR** s nástrojem Strong Name.

     Následující příklad vypne ověřování pro sestavení s názvem *MyAssembly. dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Pokud chcete vypnout ověřování na platformách, u kterých nemůžete spustit nástroj silného názvu, jako jsou mikroprocesory ARM (Advanced RISC Machine), použijte k vytvoření souboru registru možnost **– VK** . Importujte soubor registru do registru v počítači, ve kterém chcete vypnout ověřování. Následující příklad vytvoří soubor registru pro `myAssembly.dll`.

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   Pomocí možnosti **-VR** nebo **– VK** můžete volitelně zahrnout soubor *. snk* pro podepisování testovacího klíče.

   > [!WARNING]
   > Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

   > [!NOTE]
   > Použijete-li zpožděné podepisování během vývoje pomocí sady Visual Studio na 64 počítači a zkompilujete sestavení pro **Libovolný procesor**, bude pravděpodobně nutné použít možnost **-VR** dvakrát. (V aplikaci Visual Studio je **Libovolný procesor** hodnotou vlastnosti sestavení **target Platform** ; při kompilaci z příkazového řádku je to výchozí nastavení.) Chcete-li spustit aplikaci z příkazového řádku nebo z Průzkumníka souborů, použijte 64 verzi programu [sn. exe (nástroj Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md) , chcete-li použít možnost **-VR** pro sestavení. Chcete-li načíst sestavení do sady Visual Studio v době návrhu (například pokud sestavení obsahuje komponenty, které jsou používány jinými sestaveními v aplikaci), použijte 32 verzi nástroje pro silný název. Důvodem je, že kompilátor JIT zkompiluje sestavení do 64 bitového nativního kódu při spuštění sestavení z příkazového řádku a do 32 nativního kódu, když je sestavení načteno do prostředí pro dobu návrhu.

5. Později obvykle těsně před expedicí odešlete sestavení do podpisového autority vaší organizace pro skutečný podpis silného názvu pomocí možnosti **– R** s nástrojem silného názvu.

   Následující příklad podepíše sestavení s názvem *MyAssembly. dll* se silným názvem pomocí páru klíčů *klíči sgKey. snk* .

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](create.md)
- [Postupy: Vytvoření páru klíčů veřejného a soukromého](create-public-private-key-pair.md)
- [SN. exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Program se sestaveními](program.md)
