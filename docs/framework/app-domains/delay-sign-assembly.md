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
ms.openlocfilehash: 4457bd6d5efd7404cdba6c5fbdbffa9f9eb62141
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="delay-signing-an-assembly"></a>Zpoždění podepsání sestavení
Organizace může mít úzce chráněného pár klíčů, vývojáři nemá přístup k každý den. Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezen na pouze několika jednotlivcům. Při vývoji sestavení se silnými názvy, každé sestavení tohoto sestavení cíl odkazy silným názvem obsahuje token veřejného klíče dávat cíl sestavení silným názvem. To vyžaduje, aby veřejný klíč k dispozici během procesu vývoje.  
  
 Rezerva místa v přenosné spustitelný soubor (PE) pro podpis silného názvu, ale odložené podepisování do některé pozdější fázi (obvykle jen před přesouvání sestavení) můžete použít zpožděné nebo částečné podepsání v čase vytvoření buildu.  
  
 Následující kroky popisují proces zpoždění podepsání sestavení:  
  
1.  Získejte veřejnou část klíče páru klíčů z organizace, která provede případné podepsání. Tento klíč je obvykle ve formátu souboru .snk, který lze vytvořit pomocí [silný název – nástroj (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Opatřete zdrojový kód pro sestavení dvěma vlastními atributy z <xref:System.Reflection>:  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, který předává název souboru, který obsahuje veřejný klíč jako parametr jeho konstruktoru.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, což naznačuje, že zpožděné podepisování je používáno předáním **true** jako parametr jeho konstruktoru. Příklad:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Kompilátor vloží veřejný klíč do manifestu a rezervy místa v souboru PE podpis úplné silného názvu. Reálný veřejný klíč musí být uložen při sestavení je sestaven tak, aby ostatních sestavení, které odkazují na toto sestavení můžete získat klíč, který chcete uložit do své vlastní odkaz sestavení.  
  
4.  Protože sestavení nemá podpis platný silného názvu, musí být vypnutý ověřování tohoto podpisu. Můžete to provést pomocí **– Vr** možnost pomocí nástroje silného názvu.  
  
     Následující příklad vypne ověřování pro sestavení nazvané `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Chcete-li vypnout ověření na platformách, kde nelze spustit nástroje pro silný název, jako je například procesory Advanced RISC Machine (ARM), použijte **– Vk** možnost vytvořte soubor registru. Importujte soubor registru do registru na počítači, ve které chcete vypnout ověření. Následující příklad vytvoří soubor registru pro `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Pomocí **– Vr** nebo **– Vk** možnost, může volitelně obsahovat soubor .snk pro test klíče podepisování.  
  
    > [!WARNING]
    > Nespoléhejte na silné názvy pro zabezpečení. Obsahují jenom jedinečnou identitu.
  
    > [!NOTE]
    >  Pokud používáte zpoždění podepsání během vývoje pomocí sady Visual Studio na 64bitovém počítači, a kompilaci sestavení pro **libovolný procesor**, možná budete muset použít **- Vr** možnost dvakrát. (V sadě Visual Studio, **libovolný procesor** je hodnota **Cílová platforma** vlastnost sestavení, když kompilujete z příkazového řádku, je výchozí.) Pokud chcete aplikaci spustit z příkazového řádku nebo z Průzkumníka souborů, použijte 64bitové verze [Sn.exe (nástroj silným názvem)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pro použití **- Vr** možnost sestavení. K načtení sestavení do sady Visual Studio v době návrhu (například pokud sestavení obsahuje součásti, které jsou používány jiné sestavení v aplikaci), použijte 32bitovou verzi nástroje silného názvu. To je proto kompilátoru za běhu (JIT) kompiluje sestavení 64-bit nativního kódu při spuštění sestavení z příkazového řádku a nativní kód 32-bit při sestavení načtení do prostředí návrhu.  
  
5.  Později, obvykle těsně před jejich odesláním, odešlete sestavení pro vaši organizaci podepisovací autority pro aktuální podepsání pomocí silného názvu **– R** možnost pomocí nástroje silného názvu.  
  
     Následující příklad podepíše sestavení nazvané `myAssembly.dll` se silným názvem pomocí `sgKey.snk` dvojice klíčů.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Postupy: Vytvoření páru veřejného a soukromého klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
