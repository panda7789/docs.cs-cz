---
title: Přesměrování verzí sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
ms.openlocfilehash: 0d55171e37ec056b3470d238a60bc32f2feb04fb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646047"
---
# <a name="redirecting-assembly-versions"></a>Přesměrování verzí sestavení

Můžete přesměrovat odkazy na vazbu kompilace na sestavení rozhraní .NET Framework, sestavení třetích stran nebo sestavení vlastní aplikace. Aplikaci můžete přesměrovat tak, aby používala jinou verzi sestavení několika způsoby: prostřednictvím zásad vydavatele, prostřednictvím konfiguračního souboru aplikace. nebo prostřednictvím konfiguračního souboru počítače. Tento článek popisuje, jak funguje vazba sestavení v rozhraní .NET Framework a jak ji lze nakonfigurovat.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Sjednocení sestavení a výchozí vazba
 Vazby na sestavení rozhraní .NET Framework jsou někdy přesměrovány prostřednictvím procesu nazývaného *sjednocení sestavení*. Rozhraní .NET Framework se skládá z verze za běhu běžného jazyka a asi dvou desítek sestavení rozhraní .NET Framework, která tvoří knihovnu typů. Tato sestavení rozhraní .NET Framework jsou runtime považována za jednu jednotku. Ve výchozím nastavení při spuštění aplikace jsou všechny odkazy na typy v kódu spuštěném za běhu směrovány na sestavení rozhraní .NET Framework, která mají stejné číslo verze jako runtime načtený v procesu. Přesměrování, ke kterým dochází s tímto modelem, jsou výchozím chováním pro běhový čas.

 Pokud například vaše aplikace odkazuje na typy v oboru názvů System.XML a byla vytvořena pomocí rozhraní .NET Framework 4.5, obsahuje statické odkazy na sestavení System.XML, které je dodáváno s runtime verze 4.5. Pokud chcete přesměrovat odkaz na vazbu tak, aby odkazoval na sestavení System.XML, které je dodáváno s rozhraním .NET Framework 4, můžete informace o přesměrování vložit do konfiguračního souboru aplikace. Přesměrování vazby v konfiguračním souboru pro sjednocené sestavení rozhraní .NET Framework zruší sjednocení pro toto sestavení.

 Kromě toho můžete ručně přesměrovat vazbu sestavení pro sestavení jiných výrobců, pokud je k dispozici více verzí.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Přesměrování verzí sestavení pomocí zásad vydavatele
 Dodavatelé sestavení můžete přesměrovat aplikace na novější verzi sestavení zahrnutím souboru zásad vydavatele s novým sestavením. Soubor zásad vydavatele, který je umístěn v globální mezipaměti sestavení, obsahuje nastavení přesměrování sestavení.

 Každý *hlavní*. *dílčí* verze sestavení má vlastní soubor zásad vydavatele. Například přesměrování z verze 2.0.2.222 na 2.0.3.000 a z verze 2.0.2.321 na verzi 2.0.3.000 přejdou do stejného souboru, protože jsou přidruženy k verzi 2.0. Přesměrování z verze 3.0.0.999 na verzi 4.0.0.000 však přejde do souboru pro verzi 3.0.999. Každá hlavní verze rozhraní .NET Framework má svůj vlastní soubor zásad vydavatele.

 Pokud pro sestavení existuje soubor zásad vydavatele, runtime tento soubor zkontroluje po kontrole manifestu sestavení a konfiguračního souboru aplikace. Dodavatelé by měli používat soubory zásad vydavatele pouze v případě, že nové sestavení je zpětně kompatibilní s přesměrované sestavení.

 Zásady vydavatele aplikace můžete obejít zadáním nastavení v konfiguračním souboru aplikace, jak je popsáno v [části Obejití vydavatele](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Přesměrování verzí sestavení na úrovni aplikace
 Existuje několik různých technik pro změnu chování vazby pro vaši aplikaci prostřednictvím konfiguračního souboru aplikace: můžete ručně upravit soubor, můžete se spolehnout na automatické přesměrování vazby nebo můžete určit chování vazby vynecháním zásad vydavatele.

### <a name="manually-editing-the-app-config-file"></a>Ruční úprava konfiguračního souboru aplikace
 Konfigurační soubor aplikace můžete ručně upravit a vyřešit tak problémy se sestavením. Například pokud dodavatel může uvolnit novější verzi sestavení, které vaše aplikace používá bez poskytnutí zásad vydavatele, protože nezaručuje zpětnou kompatibilitu, můžete nasměrovat aplikaci k použití novější verze sestavení vložením informace o vazbě sestavení v konfiguračním souboru aplikace takto.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Spoléhání se na automatické přesměrování vazeb

Když vytvoříte desktopovou aplikaci v sadě Visual Studio, která cílí na rozhraní .NET Framework 4.5.1 nebo novější verzi, aplikace použije automatické přesměrování vazby. To znamená, že pokud dvě součásti odkazují na různé verze stejného sestavení se silným názvem, runtime automaticky přidá přesměrování vazby na novější verzi sestavení v souboru konfigurace výstupní aplikace (app.config). Toto přesměrování přepíše sjednocení sestavení, které by jinak mohlo proběhnet. Zdrojový soubor app.config není změněn. Řekněme například, že vaše aplikace přímo odkazuje na nepásmovou komponentu .NET Framework, ale používá knihovnu jiného výrobce, která cílí na starší verzi stejné součásti. Při kompilaci aplikace je konfigurační soubor výstupní aplikace upraven tak, aby obsahoval přesměrování vazby na novější verzi komponenty. Pokud vytvoříte webovou aplikaci, zobrazí se upozornění sestavení týkající se konfliktu vazby, což vám dává možnost přidat potřebné přesměrování vazby do zdrojového webového konfiguračního souboru.

Pokud ručně přidáte přesměrování vazby do zdrojového souboru app.config, v době kompilace se Visual Studio pokusí sjednotit sestavení na základě přidaných přesměrování vazby. Řekněme například, že vložíte následující přesměrování vazby pro sestavení:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Pokud jiný projekt ve vaší aplikaci odkazuje na verzi 1.0.0.0 stejného sestavení, automatické přesměrování vazby přidá do výstupního souboru app.config následující položku tak, aby aplikace byla sjednocena ve verzi 2.0.0.0 tohoto sestavení:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Přesměrování automatických vazeb můžete povolit, pokud vaše aplikace cílí na starší verze rozhraní .NET Framework. Toto výchozí chování můžete přepsat poskytnutím informací o přesměrování vazby v souboru app.config pro libovolné sestavení nebo vypnutím funkce přesměrování vazby. Informace o zapnutí nebo vypnutí této funkce naleznete v [tématu Postup: Povolení a zakázání automatického přesměrování vazby](how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Vynechání zásad vydavatele
 V případě potřeby můžete přepsat zásady vydavatele v konfiguračním souboru aplikace. Například nové verze sestavení, které tvrdí, že jsou zpětně kompatibilní, mohou stále přerušit aplikaci. Pokud chcete obejít zásady vydavatele, přidejte element [ \<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) do prvku [ \<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) v konfiguračním souboru aplikace a nastavte atribut **apply** na **no**, který přepíše všechna předchozí nastavení **yes.**

 `<publisherPolicy apply="no" />`

 Obejít zásady vydavatele, aby vaše aplikace spuštěna pro vaše uživatele, ale ujistěte se, že problém nahlásit dodavateli sestavení. Pokud má sestavení soubor zásad vydavatele, měl by se dodavatel ujistit, že sestavení je zpětně kompatibilní a že klienti mohou používat novou verzi co nejvíce.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Přesměrování verzí sestavení na úrovni stroje
 Může být vzácné případy, kdy správce počítače chce, aby všechny aplikace v počítači používaly určitou verzi sestavení. Správce může například chtít, aby každá aplikace používala určitou verzi sestavení, protože tato verze opravuje bezpečnostní díru. Pokud je sestavení přesměrováno v konfiguračním souboru počítače, budou všechny aplikace v tomto počítači, které používají starou verzi, přesměrovány na použití nové verze. Konfigurační soubor počítače přepíše konfigurační soubor aplikace a soubor zásad vydavatele. Tento soubor je umístěn v instalační cestě %*za běhu*%\Config. Rozhraní .NET Framework je obvykle nainstalováno v adresáři %drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Určení vazby sestavení v konfiguračních souborech
 Stejný formát XML slouží k určení přesměrování vazeb bez ohledu na to, zda se jedná o konfigurační soubor aplikace, konfigurační soubor počítače nebo soubor zásad vydavatele. Chcete-li přesměrovat jednu [ \<](./file-schema/runtime/bindingredirect-element.md) verzi sestavení na jinou, použijte vazbyRedirect>prvek. Atribut **oldVersion** můžete zadat jednu verzi sestavení nebo rozsah verzí. Atribut `newVersion` by měl určit jednu verzi.  Například `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` určuje, že runtime by měl používat verzi 2.0.0.0 namísto verze sestavení mezi 1.1.0.0 a 1.2.0.0.

 Následující příklad kódu ukazuje různé scénáře přesměrování vazby. Příklad určuje přesměrování pro rozsah verzí pro `myAssembly`aplikace a jedno vazby `mySecondAssembly`pro . Příklad také určuje, že soubor zásad vydavatele nepřepíše `myThirdAssembly`přesměrování vazeb pro aplikaci .

 Chcete-li vytvořit vazbu sestavení, musíte zadat řetězec "urn:schemas-microsoft-com:asm.v1" s atributem **xmlns** ve značce [ \<assemblyBinding>.](./file-schema/runtime/assemblybinding-element-for-runtime.md)

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Omezení vazeb sestavení na určitou verzi
 Atribut **appliesTo** na elementu [ \<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) v konfiguračním souboru aplikace můžete použít k přesměrování odkazů na vazbu sestavení na konkrétní verzi rozhraní .NET Framework. Tento volitelný atribut používá číslo verze rozhraní .NET Framework k označení, na jakou verzi se vztahuje. Pokud není zadán žádný atribut **appliesTo,** element [ \<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) se vztahuje na všechny verze rozhraní .NET Framework.

 Chcete-li například přesměrovat vazbu sestavení pro sestavení rozhraní .NET Framework 3.5, zahrnete do konfiguračního souboru aplikace následující kód XML.

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 Měli byste zadat informace o přesměrování v pořadí verzí. Zadejte například informace o přesměrování vazby sestavení pro sestavení rozhraní .NET Framework 3.5 následované sestaveními rozhraní .NET Framework 4.5. Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení rozhraní .NET Framework, které nepoužívá atribut **appliesTo** a proto se vztahuje na všechny verze rozhraní .NET Framework. Pokud dojde ke konfliktu přesměrování, použije se první odpovídající příkaz přesměrování v konfiguračním souboru.

 Chcete-li například přesměrovat jeden odkaz na sestavení rozhraní .NET Framework 3.5 a jiný odkaz na sestavení rozhraní .NET Framework 4, použijte vzorek zobrazený v následujícím pseudokódu.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Viz také

- [Postupy: Povolení a zákaz automatického přesměrování vazby](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect> Element](./file-schema/runtime/bindingredirect-element.md)
- [Bezpečnostní oprávnění k přesměrování vazby sestavení](assembly-binding-redirection-security-permission.md)
- [Sestavení v .NET](../../standard/assembly/index.md)
- [Programování se sestaveními](../../standard/assembly/index.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](index.md)
- [Schéma nastavení běhu](./file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](./file-schema/index.md)
- [Postupy: Vytváření zásad vydavatele](how-to-create-a-publisher-policy.md)
