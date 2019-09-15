---
title: 'Postupy: Podepsat sestavení silným názvem'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973059"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Postupy: Podepsat sestavení silným názvem

> [!NOTE]
> I když .NET Core podporuje sestavení se silným názvem a všechna sestavení v knihovně .NET Core jsou podepsaná, většina sestavení třetích stran nepotřebuje silné názvy. Další informace najdete v tématu [podepisování silného názvu](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) na GitHubu.

Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:  
  
- Pomocí karty **podepisování** v dialogovém okně **vlastnosti** projektu v aplikaci Visual Studio. Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.  
  
- Pomocí [linkeru sestavení (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) můžete propojit modul kódu .NET Framework (soubor *. netmodule* ) se souborem klíče.  
  
- Pomocí atributů sestavení pro vložení informací o silném názvu do kódu. Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, nebo, v závislosti na tom, kde je umístěn soubor klíče, který má být použit.  
  
- Pomocí možností kompilátoru.  
  
 Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Další informace o vytváření páru klíčů naleznete v tématu [How to: Vytvoří pár](create-public-private-key-pair.md)veřejného a privátního klíče.  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Vytvoření a podepsání sestavení silným názvem pomocí sady Visual Studio  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
2. Klikněte na kartu **podepisování** .  
  
3. Vyberte pole **podepsat sestavení** .  
  
4. V poli **Zvolte soubor klíče se silným názvem** zvolte možnost **Procházet**a potom přejděte k souboru klíče. Chcete-li vytvořit nový soubor klíče, vyberte možnost **Nový** a zadejte jeho název do dialogového okna **vytvořit klíč se silným názvem** .  
  
> [!NOTE]
> Aby bylo možné [zpozdit podepsání sestavení](delay-sign.md), vyberte soubor veřejného klíče.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Vytvoření a podepsání sestavení silným názvem pomocí linkeru sestavení  
  
V [Developer Command Prompt pro Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)zadejte následující příkaz:  

**Al** **/out:** názevmodulu> AssemblyName **>/keyfile**:názevsouboru\< *\<* \<>  

,  

- *AssemblyName* je název silně podepsaného sestavení (soubor *. dll* nebo *. exe* ), který bude linker sestavení generovat.  
  
- název *modulu* je název modulu .NET Frameworkho kódu (soubor *. netmodule* ), který obsahuje jeden nebo více typů. Můžete vytvořit soubor *. netmodule* kompilováním kódu s `/target:module` přepínačem v C# nebo Visual Basic.
  
- název *souboru* je název kontejneru nebo souboru, který obsahuje pár klíčů. Linker sestavení interpretuje relativní cestu ve vztahu k aktuálnímu adresáři.  

Následující příklad podepíše sestavení *MyAssembly. dll* se silným názvem pomocí souboru Key *klíči sgKey. snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Další informace o tomto nástroji naleznete v tématu [linker sestavení](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podepsání sestavení silným názvem pomocí atributů  
  
1. Přidejte atribut <xref:System.Reflection.AssemblyKeyNameAttribute> nebo do souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje dvojici klíčů pro použití při podepisování sestavení silným názvem. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType>  
   
2. Zkompilujte soubor zdrojového kódu běžným způsobem.  
   
   > [!NOTE]
   > Kompilátory C# a Visual Basic vydávají upozornění kompilátoru (CS1699 a BC41008 v uvedeném pořadí) při výskytu <xref:System.Reflection.AssemblyKeyFileAttribute> atributu <xref:System.Reflection.AssemblyKeyNameAttribute> nebo ve zdrojovém kódu. Upozornění můžete ignorovat.  

Následující příklad používá <xref:System.Reflection.AssemblyKeyFileAttribute> atribut se souborem klíče s názvem *keyfile. snk*, který je umístěn v adresáři, kde je sestavení zkompilováno.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet. Další informace naleznete v tématu [opožděné podepsání sestavení](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podepsání sestavení silným názvem pomocí kompilátoru  

Zkompilujte soubor zdrojového `/keyfile` kódu nebo soubory pomocí možnosti kompilátoru nebo `/delaysign` v C# a Visual Basic nebo `/KEYFILE` `/DELAYSIGN` možnost linkeru v. C++ Za název možnosti přidejte dvojtečku a název souboru s klíčem. Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.  

Informace o zpožděném podepisování naleznete v tématu [opožděné podepsání sestavení](delay-sign.md).  

Následující příklad používá C# kompilátor a podepíše sestavení *UtilityLibrary. dll* se silným názvem pomocí souboru klíče *klíči sgKey. snk*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Viz také:

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
- [Postupy: Vytvoření páru klíčů veřejného a soukromého](create-public-private-key-pair.md)
- [Al.exe (linker sestavení)](../../framework/tools/al-exe-assembly-linker.md)
- [Zpožděný podpis sestavení](delay-sign.md)
- [Správa podepsání sestavení a manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Stránka podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)
