---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 346671d4febd5f3999f1f4fbf2fe4b7e475ae5fa
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040192"
---
# <a name="how-to-create-a-publisher-policy"></a>Postupy: Vytváření zásad vydavatele

Dodavatelé sestavení mohou stanovit, že aplikace by měly používat novější verzi sestavení zahrnutím souboru zásad vydavatele s upgradovaným sestavením. Soubor zásad vydavatele určuje přesměrování sestavení a základní nastavení kódu a používá stejný formát jako konfigurační soubor aplikace. Soubor zásad vydavatele je zkompilován do sestavení a umístěn do globální mezipaměti sestavení (GAC).

Existují tři kroky, které se týkají vytváření zásad vydavatele:

1. Vytvořte soubor zásad vydavatele.

2. Vytvořte sestavení zásad vydavatele.

3. Přidejte sestavení zásad vydavatele do globální mezipaměti sestavení (GAC).

Schéma pro zásady vydavatele je popsáno v tématu [Přesměrování verzí sestavení](redirect-assembly-versions.md). Následující příklad ukazuje soubor zásad vydavatele, který přesměruje jednu verzi `myAssembly` na jinou.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Informace o tom, jak zadat základ kódu, naleznete v tématu [určení umístění sestavení](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Vytváření sestavení zásad vydavatele

Pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md) vytvořte sestavení zásad vydavatele.

#### <a name="to-create-a-publisher-policy-assembly"></a>Vytvoření sestavení zásad vydavatele

Do příkazového řádku zadejte následující příkaz:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

V tomto příkazu:

- Argument `publisherPolicyFile` je název souboru zásad vydavatele.

- Argument `publisherPolicyAssemblyFile` je název sestavení zásad vydavatele, které je výsledkem tohoto příkazu. Název souboru sestavení musí odpovídat formátu:

  ' Policy. majorNumber. minorNumber. mainAssemblyName. dll '

- Argument `keyPairFile` je název souboru, který obsahuje dvojici klíčů. Sestavení zásad sestavení a vydavatel je nutné podepsat se stejnou dvojicí klíčů.

- Argument `processorArchitecture` identifikuje platformu, na kterou cílí sestavení specifické pro procesor.

  > [!NOTE]
  > Možnost cílení na konkrétní architekturu procesoru je k dispozici od .NET Framework 2,0.

Možnost cílení na konkrétní architekturu procesoru je k dispozici od .NET Framework 2,0. Následující příkaz vytvoří sestavení zásad vydavatele s názvem `policy.1.0.myAssembly` ze souboru zásad vydavatele s názvem `pub.config`, přiřadí sestavení silný název pomocí páru klíčů v souboru `sgKey.snk` a určí, že sestavení cílí na procesor x86. Architektura.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Sestavení zásad vydavatele se musí shodovat s architekturou procesoru sestavení, na které se vztahuje. Proto pokud má vaše sestavení hodnotu <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL>, musí být sestavení zásad vydavatele pro toto sestavení vytvořeno pomocí `/platform:anycpu`. Pro každé sestavení specifické pro procesor musíte zadat samostatné sestavení zásad vydavatele.

V důsledku tohoto pravidla je, že pro změnu architektury procesoru pro sestavení je nutné změnit hlavní nebo dílčí komponentu čísla verze, abyste mohli dodat nové sestavení zásad vydavatele se správnou architekturou procesoru. Sestavení původní zásady vydavatele nemůže obsluhovat sestavení, jakmile má vaše sestavení jinou architekturu procesoru.

Další příčinou je, že linker verze 2,0 nelze použít k vytvoření sestavení zásad vydavatele pro sestavení zkompilované pomocí dřívější verze .NET Framework, protože vždy určuje architekturu procesoru.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Přidání sestavení zásad vydavatele do globální mezipaměti sestavení (GAC)

K přidání sestavení zásad vydavatele do globální mezipaměti sestavení [(GAC) použijte nástroj Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Chcete-li přidat sestavení zásad vydavatele do globální mezipaměti sestavení (GAC)

Do příkazového řádku zadejte následující příkaz:

```console
gacutil /i publisherPolicyAssemblyFile
```

Následující příkaz přidá `policy.1.0.myAssembly.dll` do globální mezipaměti sestavení (GAC).

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> Sestavení zásady vydavatele nelze přidat do globální mezipaměti sestavení (GAC), pokud původní soubor zásad vydavatele není umístěn ve stejném adresáři jako sestavení.

## <a name="see-also"></a>Viz také:

- [Programování se sestaveními](../../standard/assembly/program.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací pomocí konfiguračních souborů](index.md)
- [Schéma nastavení běhového prostředí](./file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](./file-schema/index.md)
- [Přesměrování verzí sestavení](redirect-assembly-versions.md)
