---
title: "Postupy: Podepsání sestavení silným názvem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fe5fbb5299c8e9c130538f99fe13081f8f26a55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Postupy: Podepsání sestavení silným názvem
Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:  
  
-   Pomocí **podpisování** kartě v projektu na **vlastnosti** dialogové okno v sadě Visual Studio. Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.  
  
-   Pomocí [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) propojte modul kódu rozhraní .NET Framework (soubor .netmodule) se soubor klíče.  
  
-   Pomocí atributů sestavení pro vložení informací o silném názvu do kódu. Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, v závislosti na tom, kde se nachází soubor klíče, který se má použít.  
  
-   Pomocí možností kompilátoru.  
  
 Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Další informace o vytváření pár klíčů najdete v tématu [postupy: vytvoření pár veřejného a privátního klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Vytvoření a podepsání sestavení silným názvem pomocí aplikace Visual Studio  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**.  
  
2.  Vyberte **podpisování** kartě.  
  
3.  Vyberte **podepsání sestavení** pole.  
  
4.  V **vyberte soubor klíče se silným názvem** vyberte  **\<Procházet... >**a potom přejděte na soubor klíče. Chcete-li vytvořit nový soubor klíče, zvolte  **\<nová... >** a zadejte jeho název **vytvořit klíč se silným názvem** dialogové okno.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Vytvoření a podepsání sestavení silným názvem pomocí programu Assembly Linker  
  
-   Na [Visual Studio – příkazový řádek](../../../docs/framework/tools/developer-command-prompt-for-vs.md), zadejte následující příkaz:  
  
     **Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*>  
  
     kde:  
  
     *assemblyName*  
     Název silně podepsaného sestavení (soubor .dll nebo .exe), který vygeneruje program Assembly Linker.  
  
     *Název modulu*  
     Název modulu kódu rozhraní .NET Framework (soubor .netmodule), který obsahuje jeden nebo několik typů. Můžete vytvořit soubor .netmodule kompilací kódu s `/target:module` přepínače v C# nebo Visual Basic.  
  
     *keyfileName*  
     Název kontejneru nebo souboru, který obsahuje pár klíčů. Program Assembly Linker interpretuje relativní cestu vzhledem k aktuálnímu adresáři.  
  
 Následující příklad podepíše sestavení `MyAssembly.dll` se silným názvem pomocí souboru klíče `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Další informace o tomto nástroji najdete v tématu [Linker sestavení](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podepsání sestavení silným názvem pomocí atributů  
  
1.  Přidat <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut vašeho souboru se zdrojovým kódem a zadejte název souboru nebo kontejner, který obsahuje pár klíčů mají použít při podepisování sestavení se silným názvem.  
  
2.  Zkompilujte soubor zdrojového kódu běžným způsobem.  
  
> [!NOTE]
>  Kompilátory jazyka C# a Visual Basic vydat upozornění kompilátoru (CS1699 a BC41008, v uvedeném pořadí) narazí, když <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut ve zdrojovém kódu. Upozornění můžete ignorovat.  
  
 Následující příklad používá <xref:System.Reflection.AssemblyKeyFileAttribute> atribut s názvem soubor klíče `keyfile.snk`, který je umístěný v adresáři, kde je kompilováno sestavení.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet. Další informace najdete v tématu [zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podepsání sestavení silným názvem pomocí kompilátoru  
  
-   Kompilace souboru se zdrojovým kódem nebo soubory s `/keyfile` nebo `/delaysign` – možnost kompilátoru v C# a Visual Basic nebo `/KEYFILE` nebo `/DELAYSIGN` – možnost linkeru v jazyce C++. Za název možnosti přidejte dvojtečku a název souboru s klíčem. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.  
  
     Informace o podepisování zpoždění najdete v tématu [zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Následující příklad používá kompilátor jazyka C# a podepisuje sestavení `UtilityLibrary.dll` se silným názvem pomocí souboru klíče `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Postupy: Vytvoření páru veřejného a soukromého klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Správa sestavení a podepsání manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [Stránka Podepisování, Návrhář projektu](https://msdn.microsoft.com/library/0k50fs3b)
