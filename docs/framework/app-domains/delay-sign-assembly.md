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
ms.openlocfilehash: fc4ff8f914f0e049a0fdf27b5008b1e39bc40116
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566776"
---
# <a name="delay-signing-an-assembly"></a>Zpoždění podepsání sestavení
Organizace může mít pečlivě chráněný pár klíčů, ke kterým vývojáři nemají přístup každý den. Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezený jenom na pár jednotlivců. Při vývoji sestavení se silnými názvy obsahuje každé sestavení, které odkazuje na cílové sestavení se silným názvem, token veřejného klíče, který slouží k poskytnutí silného názvu cílového sestavení. K tomu je potřeba, aby byl během procesu vývoje dostupný veřejný klíč.  
  
 Můžete použít zpožděné nebo částečné podepisování v době sestavení a rezervovat tak místo v přenositelném spustitelném souboru (PE) pro podpis silného názvu, ale odložit skutečné přihlášení do pozdější fáze (obvykle těsně před expedicí sestavení).  
  
 Následující kroky popisují proces zpoždění podepsání sestavení:  
  
1. Získejte část páru klíčů veřejného klíče z organizace, která provede případné podepisování. Obvykle je tento klíč ve formě souboru. snk, který lze vytvořit pomocí [nástroje silného názvu (Sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) , který poskytuje Windows SDK.  
  
2. Opatřit zdrojový kód sestavení zadáním dvou vlastních atributů z <xref:System.Reflection>:  
  
    - <xref:System.Reflection.AssemblyKeyFileAttribute>, který předá název souboru obsahujícího veřejný klíč jako parametr konstruktoru.  
  
    - <xref:System.Reflection.AssemblyDelaySignAttribute>, což znamená, že je použito Zpožděné podepsání předáním **hodnoty true** jako parametru konstruktoru. Příklad:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje místo v souboru PE pro úplný podpis silného názvu. Skutečný veřejný klíč musí být uložen v době, kdy sestavení je sestaveno, aby ostatní sestavení, která odkazují na toto sestavení, mohla získat klíč pro uložení do vlastního odkazu na sestavení.  
  
4. Vzhledem k tomu, že sestavení nemá platný podpis silného názvu, musí být ověření podpisu vypnuto. To můžete provést pomocí možnosti **– VR** s nástrojem Strong Name.  
  
     Následující příklad vypne ověřování pro sestavení s názvem `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Pokud chcete vypnout ověřování na platformách, u kterých nemůžete spustit nástroj silného názvu, jako jsou mikroprocesory ARM (Advanced RISC Machine), použijte k vytvoření souboru registru možnost **– VK** . Importujte soubor registru do registru v počítači, ve kterém chcete vypnout ověřování. Následující příklad vytvoří soubor registru pro `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Pomocí možnosti **-VR** nebo **– VK** můžete volitelně zahrnout soubor. snk pro podepisování testovacího klíče.  
  
    > [!WARNING]
    > Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.
  
    > [!NOTE]
    >  Použijete-li zpožděné podepisování během vývoje pomocí sady Visual Studio na 64 počítači a zkompilujete sestavení pro **Libovolný procesor**, bude pravděpodobně nutné použít možnost **-VR** dvakrát. (V aplikaci Visual Studio je **Libovolný procesor** hodnotou vlastnosti sestavení **target Platform** ; při kompilaci z příkazového řádku je to výchozí nastavení.) Chcete-li spustit aplikaci z příkazového řádku nebo z Průzkumníka souborů, použijte 64 verzi programu [sn. exe (nástroj Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) , chcete-li použít možnost **-VR** pro sestavení. Chcete-li načíst sestavení do sady Visual Studio v době návrhu (například pokud sestavení obsahuje komponenty, které jsou používány jinými sestaveními v aplikaci), použijte 32 verzi nástroje pro silný název. Důvodem je, že kompilátor JIT zkompiluje sestavení do 64 bitového nativního kódu při spuštění sestavení z příkazového řádku a do 32 nativního kódu, když je sestavení načteno do prostředí pro dobu návrhu.  
  
5. Později obvykle těsně před expedicí odešlete sestavení do podpisového autority vaší organizace pro skutečný podpis silného názvu pomocí možnosti **– R** s nástrojem silného názvu.  
  
     Následující příklad podepíše sestavení s názvem `myAssembly.dll` se silným názvem `sgKey.snk` pomocí páru klíčů.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Postupy: Vytvoření páru klíčů veřejného a soukromého](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
