---
title: 'Postup: Podepsání sestavení se silným názvem'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160310"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Postup: Podepsání sestavení se silným názvem

> [!NOTE]
> Přestože .NET Core podporuje sestavení se silným názvem a všechna sestavení v knihovně .NET Core jsou podepsána, většina sestavení třetích stran nepotřebují silné názvy. Další informace najdete [v tématu Podpis silného názvu](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) na GitHubu.

Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:  
  
- Pomocí karty **Podpisv** dialogovém okně **Vlastnosti** projektu v sadě Visual Studio. Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.  
  
- Pomocí [propojovacího programu sestavení (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) propojte modul kódu rozhraní .NET Framework (soubor *.netmodule)* se souborem klíče.  
  
- Pomocí atributů sestavení pro vložení informací o silném názvu do kódu. Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, v závislosti na tom, kde je umístěn soubor klíče, který má být použit.  
  
- Pomocí možností kompilátoru.  
  
 Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Další informace o vytvoření páru klíčů naleznete v [tématu Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](create-public-private-key-pair.md).  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Vytvoření a podepsání sestavení se silným názvem pomocí sady Visual Studio  
  
1. V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Vlastnosti**.  
  
2. Zvolte kartu **Podpisování.**  
  
3. Vyberte podepsat pole **sestavy.**  
  
4. V poli **Zvolit soubor klíče se silným názvem** zvolte **Procházet**a přejděte na soubor klíče. Chcete-li vytvořit nový soubor klíče, zvolte **Nový** a zadejte jeho název do dialogového okna **Vytvořit silný klíč názvu.**  
  
> [!NOTE]
> Chcete-li [zpozdit podepsání sestavení](delay-sign.md), zvolte soubor veřejného klíče.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Vytvoření a podepsání sestavení se silným názvem pomocí propojovacího zařízení sestavení  
  
Na [příkazovém řádku pro vývojáře pro visual studio](../../framework/tools/developer-command-prompt-for-vs.md)zadejte následující příkaz:  

**al** **/out:**\<*moduleName*> *\<moduleName>* **/keyfile:**\<*keyfileName*>  

Kde:  

- *assemblyName* je název silně podepsaného sestavení (soubor *U.dll* nebo *.exe),* který bude vyzařovávat Linker sestavení.  
  
- *moduleName* je název modulu kódu rozhraní .NET Framework (soubor *.netmodule),* který obsahuje jeden nebo více typů. Soubor *.netmodule* můžete vytvořit kompilací kódu pomocí `/target:module` přepínače v jazyce C# nebo Visual Basic.
  
- *keyfileName* je název kontejneru nebo souboru, který obsahuje dvojici klíčů. Linker sestavení interpretuje relativní cestu ve vztahu k aktuálnímu adresáři.  

Následující příklad podepisuje sestavení *MyAssembly.dll* silným názvem pomocí souboru klíče *sgKey.snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Další informace o tomto nástroji naleznete v [tématu Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podepsání sestavení silným názvem pomocí atributů  
  
1. Přidejte <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> <xref:System.Reflection.AssemblyKeyNameAttribute> atribut nebo do souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje dvojici klíčů, která se má použít při podepisování sestavení se silným názvem.  

2. Zkompilujte soubor zdrojového kódu běžným způsobem.  

   > [!NOTE]
   > Kompilátory jazyka C# a Visual Basic vydávají upozornění kompilátoru (CS1699 a <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> BC41008, v uvedeném pořadí), když narazí na atribut nebo ve zdrojovém kódu. Upozornění můžete ignorovat.  

Následující příklad používá <xref:System.Reflection.AssemblyKeyFileAttribute> atribut s klíčovým souborem s názvem *keyfile.snk*, který je umístěn v adresáři, kde je sestavení kompilován.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet. Další informace naleznete v [tématu Delay-sign sestavení](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podepsání sestavení se silným názvem pomocí kompilátoru  

Kompilace souboru zdrojového `/keyfile` kódu `/delaysign` nebo soubory s možností nebo kompilátoru v jazyce C# a Visual Basic nebo `/KEYFILE` možnost nebo `/DELAYSIGN` linker v jazyce C++. Za název možnosti přidejte dvojtečku a název souboru s klíčem. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.  

Informace o zpoždění podepisování naleznete v [tématu Delay-sign sestavení](delay-sign.md).  

Následující příklad používá kompilátor Jazyka C# a podepisuje soubor *Assembly UtilityLibrary.dll* silným názvem pomocí souboru klíče *sgKey.snk*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Viz také

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
- [Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](create-public-private-key-pair.md)
- [Al.exe (linker sestavení)](../../framework/tools/al-exe-assembly-linker.md)
- [Opožděný podpis sestavení](delay-sign.md)
- [Správa podepsání sestavení a manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Podepisovací stránka, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)
