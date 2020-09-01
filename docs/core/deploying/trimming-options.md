---
title: Možnosti ořezávání
description: Naučte se řídit oříznutí aplikací, které jsou v ní obsažené.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: d6081a24cc18e424b55d40e152f519c680f11aa0
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271877"
---
# <a name="trimming-options"></a>Možnosti ořezávání

Následující vlastnosti a položky nástroje MSBuild mají vliv na chování [oříznutých samostatných nasazení](trim-self-contained.md). Některé z zmíněných možností `ILLink` , což je název základního nástroje, který implementuje ořezávání. Další informace o `ILLink` nástroji příkazového řádku najdete v části [illink Options](https://github.com/mono/linker/blob/master/docs/illink-options.md).

## <a name="enable-trimming"></a>Povolit oříznutí

- `<PublishTrimmed>true</PublishTrimmed>`

   Povolí ořezávání během publikování s výchozím nastavením definovaným sadou SDK.

Při použití nástroje `Microsoft.NET.Sdk` bude provedeno ořezávání sestavení rozhraní architektury na úrovni sestavení ze sady netcoreapp runtime Pack. Kód aplikace a knihovny bez architektury nejsou oříznuty. Jiné sady SDK mohou definovat různé výchozí hodnoty.

## <a name="trimming-granularity"></a>Rozřezání členitosti

Následující nastavení členitosti určují, jak se zruší agresivní nevyužité IL. To lze nastavit jako vlastnost nebo jako metadata v [jednotlivých sestaveních](#trimmed-assemblies).

- `<TrimMode>copyused</TrimMode>`

   Povolit ořezávání na úrovni sestavení, které uchová celé sestavení, pokud je použita kterákoli jeho část (staticky srozumitelným způsobem).

- `<TrimMode>link</TrimMode>`

    Povolí ořezávání na úrovni člena, které odebere nepoužívané členy z typů.

Sestavení s `<IsTrimmable>true</IsTrimmable>` metadaty, ale bez explicitní `TrimMode` , budou používat globální `TrimMode` . Výchozí hodnota `TrimMode` pro `Microsoft.NET.Sdk` je `copyused` .

## <a name="trimmed-assemblies"></a>Vystříhat sestavení

Při publikování aplikace s oříznutou sadou SDK vypočítá výjimku `ItemGroup` `ManagedAssemblyToLink` , která představuje sadu souborů, které mají být zpracovány pro ořezávání. `ManagedAssemblyToLink` může mít metadata, která řídí chování ořezávání na sestavení. Chcete-li nastavit tato metadata, vytvořte cíl, který bude spuštěn před předdefinovaným `PrepareForILLink` cílem. Tento příklad ukazuje, jak povolit oříznutí `MyAssembly` :

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

Nepřidávejte nebo Neodstraňujte položky do/z `ManagedAssemblyToLink` , protože sada SDK počítá tuto sadu během publikování a očekává, že se nemění. Podporovaná metadata:

- `<IsTrimmable>true</IsTrimmable>`

  Určuje, zda je dané sestavení oříznuto.

- `<TrimMode>copyused</TrimMode>` nebo `<TrimMode>link</TrimMode>`

  Řídí [členitost ořezávání](#trimming-granularity) tohoto sestavení. Má přednost před globálním `TrimMode` . Nastavení `TrimMode` v sestavení implikuje `<IsTrimmable>true</IsTrimmable>` .

## <a name="root-assemblies"></a>Kořenová sestavení

Všechna sestavení, která nejsou `<IsTrimmable>true</IsTrimmable>` považována za kořene pro analýzu, což znamená, že budou zachovány všechny své staticky srozumitelné závislosti. Další sestavení mohou být "rooted" podle názvu (bez `.dll` přípony):

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a>Kořenové deskriptory

Dalším způsobem, jak zadat kořeny pro analýzu, je použít soubor XML, který používá [Formát popisovače](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)linkeru. To vám umožní rootem konkrétní členy namísto celého sestavení.

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

Například `MyRoots.xml` může být kořenem konkrétní metoda, která je dynamicky k dispozici v aplikaci:

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a>Upozornění analýzy

Při ořezávání dojde k odebrání IL, který není staticky dosažitelný. Aplikace, které používají reflexi nebo jiné vzory, které vytvářejí dynamické závislosti, mohou být přerušeny oříznutím. Upozornění na tyto vzory:

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    Povolit upozornění analýzy střihu

Bude obsahovat upozornění na celou aplikaci, včetně vlastního kódu, kódu knihovny a kódu rozhraní.

## <a name="warning-versions"></a>Verze upozornění

Trim analýza ctí [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) vlastnost, která řídí verzi upozornění analýzy v rámci sady SDK. Existuje další vlastnost, která řídí verzi upozornění analýzy střihně nezávisle (podobně jako `WarningLevel` u kompilátoru):

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    Emituje jenom upozornění na danou úroveň nebo nižší. To může `9999` zahrnovat všechny verze upozornění.

## <a name="suppressing-warnings"></a>Potlačení upozornění

Jednotlivé [kódy upozornění](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) je možné potlačit pomocí běžných vlastností MSBuild, které jsou v sada nástrojů, včetně `NoWarn` , `WarningsAsErrors` , `WarningsNotAsErrors` a `TreatWarningsAsErrors` . Existuje další možnost, která řídí chování ILLink upozorňující na chybu nezávisle:

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    Nepovažujte upozornění ILLink za chyby. To může být užitečné, pokud chcete zabránit tomu, aby se upozornění analýzy při vystřihování zobrazovala chyby, když se chyby kompilátorů globálně zpracovávají

## <a name="removing-symbols"></a>Odebírání symbolů

Symboly se obvykle oříznou tak, aby odpovídaly oříznutým sestavením. Můžete také odebrat všechny symboly:

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    Odeberte symboly z oříznuté aplikace, včetně vložených soubory PDB a samostatných souborů PDB. To platí pro kód aplikace i všechny závislosti, které jsou dodávány se symboly.

Sada SDK také umožňuje zakázat podporu ladicího programu pomocí vlastnosti `DebuggerSupport` . Pokud je podpora ladicího programu zakázána, ořezávání odstraní symboly automaticky ( `TrimmerRemoveSymbols` Výchozí hodnota je true).
