---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646057"
---
# <a name="how-to-create-a-publisher-policy"></a>Postupy: Vytváření zásad vydavatele

Dodavatelé sestavení mohou uvést, že aplikace by měly používat novější verzi sestavení zahrnutím souboru zásad vydavatele s upgradované sestavení. Soubor zásad vydavatele určuje přesměrování sestavení a základní nastavení kódu a používá stejný formát jako konfigurační soubor aplikace. Soubor zásad vydavatele je zkompilován do sestavení a umístěn do globální mezipaměti sestavení.

Při vytváření zásad vydavatele jsou zapojeny tři kroky:

1. Vytvořte soubor zásad vydavatele.

2. Vytvořte sestavení zásad vydavatele.

3. Přidejte sestavení zásad vydavatele do globální mezipaměti sestavení.

Zásady schématu pro vydavatele jsou popsány v části [Přesměrovat verze sestavení](redirect-assembly-versions.md). Následující příklad ukazuje soubor zásad vydavatele, který `myAssembly` přesměruje jednu verzi na jinou.

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

Informace o tom, jak zadat základ kódu, naleznete [v tématu Určení umístění sestavení](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Vytvoření sestavení zásad vydavatele

Pomocí [propojovacího zařízení sestavení (Al.exe)](../tools/al-exe-assembly-linker.md) vytvořte sestavení zásad vydavatele.

#### <a name="to-create-a-publisher-policy-assembly"></a>Vytvoření sestavení zásad vydavatele

Na příkazovém řádku zadejte následující příkaz:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

V tomto příkazu:

- Argument `publisherPolicyFile` je název souboru zásad vydavatele.

- Argument `publisherPolicyAssemblyFile` je název sestavení zásad vydavatele, který je výsledkem tohoto příkazu. Název souboru sestavení musí následovat podle formátu:

  'policy.majorNumber.minorNumber.mainAssemblyName.dll'

- Argument `keyPairFile` je název souboru obsahujícího dvojici klíčů. Sestavení sestavení a sestavení zásad vydavatele je nutné podepsat se stejným párem klíčů.

- Argument `processorArchitecture` identifikuje platformu, na kterou cílí sestavení specifické pro procesor.

  > [!NOTE]
  > Možnost cílit na konkrétní architekturu procesoru je k dispozici počínaje rozhraním .NET Framework 2.0.

Možnost cílit na konkrétní architekturu procesoru je k dispozici počínaje rozhraním .NET Framework 2.0. Následující příkaz vytvoří sestavení zásad `policy.1.0.myAssembly` vydavatele volané `pub.config`ze souboru zásad vydavatele s názvem `sgKey.snk` , přiřadí sestavení silný název pomocí dvojice klíčů v souboru a určí, že sestavení cílí na architekturu procesoru x86.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Sestavení zásad vydavatele musí odpovídat architektuře procesoru sestavení, na které se vztahuje. Proto pokud vaše sestavení <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> má <xref:System.Reflection.ProcessorArchitecture.MSIL>hodnotu , sestavení zásad vydavatele `/platform:anycpu`pro toto sestavení musí být vytvořeny s . Je nutné zadat samostatné sestavení zásad vydavatele pro každé sestavení specifické pro procesor.

Důsledkem tohoto pravidla je, že chcete-li změnit architekturu procesoru pro sestavení, je nutné změnit hlavní nebo menší součást čísla verze, abyste mohli zadat nové sestavení zásad vydavatele se správnou architekturou procesoru. Staré sestavení zásad vydavatele nemůže obsluhovat vaše sestavení, jakmile má vaše sestavení jinou architekturu procesoru.

Dalším důsledkem je, že propojovací program verze 2.0 nelze použít k vytvoření sestavení zásad vydavatele pro sestavení zkompilované pomocí dřívějších verzí rozhraní .NET Framework, protože vždy určuje architekturu procesoru.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Přidání sestavení zásad vydavatele do globální mezipaměti sestavení

Pomocí [nástroje Globální mezipaměti sestavení (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) přidejte sestavení zásad vydavatele do globální mezipaměti sestavení.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Přidání sestavení zásad vydavatele do globální mezipaměti sestavení

Na příkazovém řádku zadejte následující příkaz:

```console
gacutil /i publisherPolicyAssemblyFile
```

Následující příkaz `policy.1.0.myAssembly.dll` přidá do globální mezipaměti sestavení.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> Sestavení zásad vydavatele nelze přidat do globální mezipaměti sestavení, `/link` pokud původní soubor zásad vydavatele zadaný v argumentu není umístěn ve stejném adresáři jako sestavení.

## <a name="see-also"></a>Viz také

- [Programování se sestaveními](../../standard/assembly/index.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací pomocí konfiguračních souborů](index.md)
- [Schéma nastavení běhu](./file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](./file-schema/index.md)
- [Přesměrování verzí sestavení](redirect-assembly-versions.md)
