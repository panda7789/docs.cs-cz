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
ms.openlocfilehash: a833bb0f412407d1f18793c356d4c207716eb101
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632618"
---
# <a name="delay-signing-an-assembly"></a>Zpoždění podepsání sestavení
Organizace může mít úzce strážených pár klíčů, že vývojáři nebudou mít přístup k každý den. Veřejný klíč je často k dispozici, ale přístup k privátnímu klíči je omezen pouze několika jednotlivcům. Při vývoji podepisují sestavení silnými názvy, každé sestavení této cílové sestavení silným názvem odkazy obsahuje token veřejný klíč slouží k pojmenování cílové sestavení silným názvem. To vyžaduje veřejný klíč k dispozici během procesu vývoje.  
  
 Zpožděné nebo částečné podepisování v okamžiku sestavení můžete použít k rezervaci místa do přenosného spustitelného souboru (PE) pro podpis silného názvu, ale odložit podepisování do některých později (obvykle pouze před dodáním sestavení).  
  
 Následující kroky popisují postup odložení sestavení:  
  
1.  Získáte část s veřejným klíčem z dvojice klíčů z organizace, která provede konečnou podepisování. Tento klíč je obvykle ve formě souboru .snk, které je možné vytvořit [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Přidat poznámku zdrojového kódu pro sestavení pomocí dvou vlastních atributů z <xref:System.Reflection>:  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, který předává název souboru, který obsahuje veřejný klíč jako parametr konstruktoru.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, což znamená, že zpožděné podepisování se používá předáním **true** jako parametr konstruktoru. Příklad:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Kompilátor vloží veřejný klíč do manifestu sestavení a rezervuje prostor v souboru PE pro podpis úplné silného názvu. Reálný veřejný klíč musí být uložen, zatímco sestavení je vytvořený tak, aby jiná sestavení, které odkazují na toto sestavení můžete získat klíč, který chcete uložit do své vlastní odkaz na sestavení.  
  
4.  Protože sestavení nemá silný název platný podpis, musí být vypnutý ověření podpisu. Můžete to provést pomocí **– Vr** parametrem nástroj Strong Name.  
  
     Následující příklad vypne ověření pro sestavení nazvané `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Chcete-li vypnout ověřování na platformách, kde nelze spustit nástroj Strong Name, jako je například mikroprocesory Advanced RISC Machine (ARM), použijte **– Vk** možnost vytvořit soubor registru. Importujte soubor registru do registru na počítači, ve které chcete vypnout ověřování. Následující příklad vytvoří soubor registru pro `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Buď **– Vr** nebo **– Vk** možnost, může volitelně zahrnovat souboru .snk pro testovací podpis klíče.  
  
    > [!WARNING]
    > Nespoléhejte na silných názvů pro zabezpečení. Poskytují jedinečné identity.
  
    > [!NOTE]
    >  Pokud používáte zpoždění podepsání během vývoje pomocí sady Visual Studio na 64bitovém počítači, a kompilace sestavení pro **jakýkoli procesor**, bude pravděpodobně nutné použít **- Vr** možnost dvakrát. (V sadě Visual Studio **jakýkoli procesor** je hodnota **Cílová platforma** vlastnost sestavení; při kompilaci z příkazového řádku, je výchozí nastavení.) Ke spuštění aplikace z příkazového řádku nebo z Průzkumníka souborů, použijte verzi 64-bit [Sn.exe (nástroj Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) použít **- Vr** možnost sestavení. K načtení sestavení do sady Visual Studio v době návrhu (například, pokud sestavení obsahuje součásti, které jsou používány jiné sestavení ve vaší aplikaci), pomocí 32bitové verze nástroj pro silný název. Je to proto, že kompilátor just-in-time (JIT) kompiluje sestavení do nativního kódu 64-bit při spuštění sestavení z příkazového řádku a do nativního kódu 32-bit při sestavení je načteno do návrhové prostředí.  
  
5.  Později, obvykle těsně před předáním, odešlete sestavení pro vaši organizaci podepisovací autority pro aktuální podepsání pomocí silného názvu **– R** parametrem nástroj Strong Name.  
  
     Následující příklad podepíše sestavení nazvané `myAssembly.dll` se silným názvem pomocí `sgKey.snk` pár klíčů.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Postupy: Vytvoření páru veřejného a privátního klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
