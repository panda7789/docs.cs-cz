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
ms.openlocfilehash: 6bd250caae1bd98d238f8d99702a97f0cdbc7448
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826899"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Postupy: Podepsání sestavení silným názvem
Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:  
  
-   S použitím **podepisování** kartu v projektu **vlastnosti** dialogové okno v sadě Visual Studio. Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.  
  
-   S použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) propojení se souborem klíče modulu kódu rozhraní .NET Framework (soubor .netmodule).  
  
-   Pomocí atributů sestavení pro vložení informací o silném názvu do kódu. Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, podle toho, kde je umístěn soubor klíče, který se má použít.  
  
-   Pomocí možností kompilátoru.  
  
 Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Další informace o vytváření páru klíčů naleznete v tématu [jak: Vytvoření páru veřejného a privátního klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Vytvoření a podepsání sestavení silným názvem pomocí aplikace Visual Studio  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.  
  
2.  Zvolte **podepisování** kartu.  
  
3.  Vyberte **podepsat sestavení** pole.  
  
4.  V **vyberte soubor klíče se silným názvem** zvolte  **\<Procházet... >** a potom přejděte k souboru klíče. Chcete-li vytvořit nový soubor klíče, zvolte  **\<nový … >** a zadejte jeho název **vytvořit klíč se silným názvem** dialogové okno.  
  
> [!NOTE]
>  Za účelem [zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md), vyberte soubor veřejného klíče.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Vytvoření a podepsání sestavení silným názvem pomocí programu Assembly Linker  
  
-   Na [Developer Command Prompt pro sadu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), zadejte následující příkaz:  
  
     **Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*>  
  
     kde:  
  
     *assemblyName*  
     Název silně podepsaného sestavení (soubor .dll nebo .exe), který vygeneruje program Assembly Linker.  
  
     *moduleName*  
     Název modulu kódu rozhraní .NET Framework (soubor .netmodule), který obsahuje jeden nebo několik typů. Soubor .netmodule můžete vytvořit kompilací kódu pomocí `/target:module` přepínače v C# nebo Visual Basic.  
  
     *keyfileName*  
     Název kontejneru nebo souboru, který obsahuje pár klíčů. Program Assembly Linker interpretuje relativní cestu vzhledem k aktuálnímu adresáři.  
  
 Následující příklad podepíše sestavení `MyAssembly.dll` se silným názvem pomocí souboru klíče `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Další informace o tomto nástroji najdete v tématu [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podepsání sestavení silným názvem pomocí atributů  
  
1.  Přidat <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje pár klíčů má použít při podepisování sestavení silným názvem.  
  
2.  Zkompilujte soubor zdrojového kódu běžným způsobem.  
  
> [!NOTE]
>  Jazyce C# a Visual Basic vydají upozornění kompilátoru (CS1699 a BC41008, v uvedeném pořadí) pokud narazí <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atributů ve zdrojovém kódu. Upozornění můžete ignorovat.  
  
 V následujícím příkladu <xref:System.Reflection.AssemblyKeyFileAttribute> atribut se souborem klíčů nazvaným `keyfile.snk`, který se nachází v adresáři, ve kterém je sestavení zkompilováno.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet. Další informace najdete v tématu [zpožděné podepisování sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podepsání sestavení silným názvem pomocí kompilátoru  
  
-   Zkompilujte soubor zdrojového kódu nebo soubory s `/keyfile` nebo `/delaysign` – možnost kompilátoru v jazyce C# a Visual Basic nebo `/KEYFILE` nebo `/DELAYSIGN` – možnost linkeru v jazyce C++. Za název možnosti přidejte dvojtečku a název souboru s klíčem. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.  
  
     Informace o dodatečném podepisování naleznete v tématu [zpožděné podepisování sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Následující příklad použije kompilátor C# a podepíše sestavení `UtilityLibrary.dll` se silným názvem pomocí souboru klíče `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Postupy: Vytvoření páru veřejného a privátního klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Správa sestavení a podepsání manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Stránka Podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)
