---
title: 'Postupy: Podepsání sestavení silným názvem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927922"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Postupy: Podepsání sestavení silným názvem
Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:  
  
- Pomocí karty **podepisování** v dialogovém okně **vlastnosti** projektu v aplikaci Visual Studio. Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.  
  
- Pomocí linkeru [sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) můžete propojit modul kódu .NET Framework (soubor. netmodule) se souborem klíče.  
  
- Pomocí atributů sestavení pro vložení informací o silném názvu do kódu. Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, nebo, v závislosti na tom, kde je umístěn soubor klíče, který má být použit.  
  
- Pomocí možností kompilátoru.  
  
 Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Další informace o vytváření páru klíčů naleznete v tématu [How to: Vytvoří pár](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)veřejného a privátního klíče.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Vytvoření a podepsání sestavení silným názvem pomocí aplikace Visual Studio  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
2. Klikněte na kartu **podepisování** .  
  
3. Vyberte pole **podepsat sestavení** .  
  
4. V poli **zvolit soubor klíče se silným názvem** klikněte na tlačítko  **\<Procházet... >** a potom přejděte k souboru klíče. Chcete-li vytvořit nový soubor klíče, klikněte na tlačítko  **\<nový... >** a zadejte jeho název do dialogového okna **vytvořit klíč se silným názvem** .  
  
> [!NOTE]
> Aby bylo možné [zpozdit podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md), vyberte soubor veřejného klíče.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Vytvoření a podepsání sestavení silným názvem pomocí programu Assembly Linker  
  
- V [Developer Command Prompt pro Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md)zadejte následující příkaz:  
  
     **Al** **/out:** názevmodulu> AssemblyName **>/keyfile**:názevsouboru\< *\<* \<>  
  
     kde:  
  
     *assemblyName*  
     Název silně podepsaného sestavení (soubor .dll nebo .exe), který vygeneruje program Assembly Linker.  
  
     *moduleName*  
     Název modulu kódu rozhraní .NET Framework (soubor .netmodule), který obsahuje jeden nebo několik typů. Můžete vytvořit soubor. netmodule kompilováním kódu s `/target:module` přepínačem v C# nebo Visual Basic.  
  
     *keyfileName*  
     Název kontejneru nebo souboru, který obsahuje pár klíčů. Program Assembly Linker interpretuje relativní cestu vzhledem k aktuálnímu adresáři.  
  
 Následující příklad podepíše sestavení `MyAssembly.dll` se silným názvem pomocí souboru `sgKey.snk`klíče.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Další informace o tomto nástroji naleznete v tématu [linker sestavení](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podepsání sestavení silným názvem pomocí atributů  
  
1. Přidejte atribut <xref:System.Reflection.AssemblyKeyNameAttribute> nebo do souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje dvojici klíčů pro použití při podepisování sestavení silným názvem. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType>  
  
2. Zkompilujte soubor zdrojového kódu běžným způsobem.  
  
> [!NOTE]
> Kompilátory C# a Visual Basic vydávají upozornění kompilátoru (CS1699 a BC41008 v uvedeném pořadí) při výskytu <xref:System.Reflection.AssemblyKeyFileAttribute> atributu <xref:System.Reflection.AssemblyKeyNameAttribute> nebo ve zdrojovém kódu. Upozornění můžete ignorovat.  
  
 Následující příklad používá <xref:System.Reflection.AssemblyKeyFileAttribute> atribut se souborem klíče s názvem `keyfile.snk`, který je umístěn v adresáři, kde je sestavení zkompilováno.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet. Další informace naleznete v tématu [Zpožděné podepisování sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podepsání sestavení silným názvem pomocí kompilátoru  
  
- Zkompilujte soubor zdrojového `/keyfile` kódu nebo soubory pomocí možnosti kompilátoru nebo `/delaysign` v C# a Visual Basic nebo `/KEYFILE` `/DELAYSIGN` možnost linkeru v. C++ Za název možnosti přidejte dvojtečku a název souboru s klíčem. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.  
  
     Informace o zpožděném podepisování naleznete v tématu [Delay Signing Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Následující příklad používá C# kompilátor a podepíše sestavení `UtilityLibrary.dll` se silným názvem pomocí souboru `sgKey.snk`klíče.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Postupy: Vytvoření páru klíčů veřejného a soukromého](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Správa sestavení a podepsání manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Stránka Podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)
