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
ms.openlocfilehash: fa7c0c22d070ec12cb67252dee7dca02c5160b9e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380090"
---
# <a name="redirecting-assembly-versions"></a>Přesměrování verzí sestavení

Můžete přesměrovat odkazy vazby kompilace na sestavení rozhraní .NET Framework, sestavení třetích stran nebo sestavení vlastní aplikace. Můžete přesměrovat svou aplikaci k používání jiné verze sestavení v několika způsoby: prostřednictvím zásady aplikace publisher prostřednictvím konfiguračního souboru aplikace; nebo pomocí konfiguračního souboru počítače. Tento článek popisuje princip vazby sestavení v rozhraní .NET Framework a jak ho lze konfigurovat.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Sjednocení sestavení a výchozí vazby
 Vazby na sestavení rozhraní .NET Framework jsou někdy přesměrovány prostřednictvím procesu nazývaného *sjednocení sestavení*. Rozhraní .NET Framework se skládá z verze common language runtime a asi z dvou tuctů sestavení rozhraní .NET Framework, které tvoří knihovnu typů. Tato sestavení rozhraní .NET Framework nakládá modul runtime jako jeden celek. Ve výchozím nastavení při spuštění aplikace všechny odkazy na typy v kódu spustit modul runtime přesměrováni na sestavení rozhraní .NET Framework, které mají stejné číslo verze jako modul runtime, který je načten v procesu. Přesměrování, ke kterým dochází v tomto modelu se výchozí chování modulu runtime.

 Například pokud vaše aplikace odkazuje na typy v oboru názvů System.XML a byla vytvořena pomocí rozhraní .NET Framework 4.5, obsahuje statické odkazy na sestavení System.XML, který se dodává s modulem runtime verze 4.5. Pokud budete chtít přesměrovat odkazy vazby tak, aby odkazoval na sestavení System.XML dodané rozhraním .NET Framework 4, můžete vložit informace o přesměrování v konfiguračním souboru aplikace. Přesměrování vazby v konfiguračním souboru pro jednotné sestavení rozhraní .NET Framework zruší sjednocení pro dané sestavení.

 Kromě toho můžete ručně přesměrovat vazby pro sestavení třetích stran, pokud jsou k dispozici více verzí sestavení.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Přesměrování verze sestavení pomocí zásady vydavatele
 Dodavatelé sestavení mohou nasměrovat aplikace na novější verze sestavení zahrnutím souboru zásad vydavatele s novým sestavením. Soubor zásad vydavatele, který je umístěn v globální mezipaměti sestavení, obsahuje nastavení přesměrování sestavení.

 Každý *hlavní*. *vedlejší* verze sestavení má svůj vlastní soubor zásad vydavatele. Například přesměrování z verze 2.0.2.222 na 2.0.3.000 a z verze 2.0.2.321 na 2.0.3.000 obě přecházet do stejného souboru, protože jsou spojeny s verzí 2.0. Přesměrování z verze 3.0.0.999 na verzi 4.0.0.000 však přechází do souboru pro verzi 3.0.999. Každá hlavní verze rozhraní .NET Framework má svůj vlastní soubor zásad vydavatele.

 Pokud pro sestavení existuje soubor se zásadami vydavatele, modul runtime zkontroluje tento soubor po kontrole konfigurační soubor aplikace a manifest sestavení. Dodavatelé by měli používat soubory zásad vydavatele, pouze v případě nové sestavení zpětně kompatibilní s přesměrovaným sestavením.

 Můžete obejít zásady vydavatele pro svou aplikaci zadáním nastavení v konfiguračním souboru aplikace, jak je popsáno v [vynechání části zásad vydavatele](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Přesměrování verze sestavení na úrovni aplikace
 Existuje několik různých postupů pro změnu chování vazeb pro vaší aplikaci pomocí konfiguračního souboru aplikace: můžete ručně upravit soubor, můžete se spolehnout na automatické přesměrování vazby nebo můžete určit chování vazby obejitím zásad vydavatele.

### <a name="manually-editing-the-app-config-file"></a>Ruční úprava konfiguračního souboru aplikace
 Můžete ručně upravit konfigurační soubor aplikace k řešení problémů se sestavením. Například pokud dodavatel vydá novější verzi sestavení, které vaše aplikace používá bez poskytnutí zásad vydavatele, protože není zaručena zpětná kompatibilita, můžete nasměrovat vaši aplikaci, aby používala novější verzi sestavení vložením sestavení Vazba informací v konfiguračním souboru aplikace následujícím způsobem.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Spoléhání na automatické přesměrování vazby

Při vytváření aplikace klasické pracovní plochy v sadě Visual Studio, který cílí na rozhraní .NET Framework 4.5.1 nebo novější verze aplikace používá automatické přesměrování vazby. To znamená, že pokud dvě součásti odkazují na různé verze téhož sestavení se silným názvem, modul runtime automaticky přidá přesměrování vazby na novější verzi sestavení ve výstupní soubor konfigurace (app.config) aplikace. Toto přesměrování přepíše sjednocení sestavení, které jinak může probíhat. Zdrojový soubor app.config není změněn. Řekněme například, že vaše aplikace přímo odkazuje na součást out-of-band rozhraní .NET Framework, ale používá knihovnu třetí strany, zaměřuje na starší verze stejné součásti. Při kompilaci aplikace výstupní soubor konfigurace aplikace je změněn, aby obsahoval přesměrování vazby na novější verzi součásti. Pokud vytvoříte webovou aplikaci, zobrazí se upozornění sestavení týkající se konfliktu vazeb, které v vám dává možnost přidat nezbytné přesměrování vazby do zdrojového souboru konfigurace webu.

Pokud ručně přidáte přesměrování vazby na zdrojový soubor app.config při kompilaci, sada Visual Studio se pokusí sjednotit sestavení podle přesměrování vazby, kterou jste přidali. Řekněme například, že vložíte následující přesměrování vazby sestavení:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Pokud jiný projekt ve vaší aplikaci na verzi 1.0.0.0 stejného sestavení, automatické přesměrování vazby přidá následující položku do výstupního souboru app.config tak, že aplikace je jednotně ve verzi 2.0.0.0 toto sestavení:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Pokud svojí aplikací cílíte na starších verzích rozhraní .NET Framework, můžete povolit automatické přesměrování vazby. Toto výchozí chování můžete přepsat tím, že poskytuje informace o přesměrování vazby v souboru app.config pro libovolné sestavení nebo tak, že vypnete funkci přesměrování vazby. Informace o tom, jak tuto funkci zapnout nebo vypnout, najdete v části [jak: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Obcházení zásad vydavatele
 Můžete přepsat zásady vydavatele v konfiguračním souboru aplikace v případě potřeby. Například nové verze sestavení, které uvádí zpětnou kompatibilitu lze i přesto narušit funkce aplikace. Pokud chcete obejít zásady vydavatele, přidejte [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) element v konfiguračním souboru aplikace a nastavte **použít** atribut **žádné**, která přepisuje jakékoli předchozí **Ano** nastavení.

 `<publisherPolicy apply="no" />`

 Přejitím zásad vydavatele můžete zachovat aplikaci spuštěnou pro vaše uživatele, ale nezapomeňte že problém ohlásit poskytovateli sestavení. Pokud sestavení využívá soubor se zásadami vydavatele, dodavatele by měl Ujistěte se, že je sestavení zpětně kompatibilní a klienti mohou používat novou verzi co nejvíc.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Přesměrování verze sestavení na úrovni počítače
 Můžou nastat výjimečných případech při správce počítače chce, aby všechny aplikace na počítači používaly určitou verzi sestavení. Správce může být například vhodné každá aplikace používala konkrétní verzi sestavení, protože tato verze opravuje bezpečnostní riziko. Pokud je sestavení přesměrováno do konfiguračního souboru počítače, všechny aplikace v daném počítači, které používají starší verzi budete přesměrováni na použití nové verze. Konfigurační souboru počítače přepíše konfigurační soubor aplikace a soubor zásad vydavatele. Tento soubor je umístěn ve složce %*cesta pro instalaci modulu runtime*%\Config adresáře. Rozhraní .NET Framework se obvykle instaluje v adresáři %drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Určení vazby v konfiguračních souborech sestavení
 Chcete-li určit přesměrování vazby, jestli je v konfiguračním souboru aplikace, konfiguračním souboru počítače nebo soubor zásad vydavatele používáte stejný formát XML. Chcete-li přesměrování jedné verze sestavení do druhého, použijte [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) elementu. **OldVersion** atribut můžete určit verzi jednoho sestavení nebo rozsah verzí. `newVersion` Atribut by měl určit jednu verzi.  Například `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` Určuje, zda modul runtime by měl používat verzi 2.0.0.0 namísto verze sestavení 1.1.0.0 a 1.2.0.0.

 Následující příklad kódu ukazuje různé scénáře přesměrování vazby. Příklad určuje přesměrování pro rozsah verzí pro `myAssembly`a přesměrování jedné vazby pro `mySecondAssembly`. Příklad také určuje, že soubor zásad vydavatele nezruší přesměrování vazby pro `myThirdAssembly`.

 K vytvoření vazby sestavení, musíte zadat řetězec "urn: schémata-microsoft-com:asm.v1" s **xmlns** atribut v [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) značky.

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Omezení vazeb sestavení na konkrétní verzi
 Můžete použít **appliesTo** atribut na [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element v konfiguračním souboru aplikace přesměrovat odkazy vazby sestavení na konkrétní verzi rozhraní .NET Architektura. Tento volitelný atribut používá pro určení verze, se vztahuje na číslo verze rozhraní .NET Framework. Pokud ne **appliesTo** atribut zadán, [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element platí pro všechny verze rozhraní .NET Framework.

 Například pro přesměrování vazeb sestavení pro sestavení rozhraní .NET Framework 3.5, bude zahrnovat následující kód XML v konfiguračním souboru aplikace.

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

 Měli byste zadat informace o přesměrování v pořadí verze. Například zadejte informace o přesměrování vazby sestavení pro sestavení rozhraní .NET Framework 3.5, následované sestavení rozhraní .NET Framework 4.5. Nakonec je třeba zadat informace o přesměrování vazby sestavení pro všechny přesměrování sestavení rozhraní .NET Framework, která nepoužívá **appliesTo** atribut a tedy platí pro všechny verze rozhraní .NET Framework. Pokud dojde ke konfliktu při přesměrování, použije se první odpovídající příkaz přesměrování konfiguračního souboru.

 Například pro přesměrování jednoho odkazu na sestavení rozhraní .NET Framework 3.5 a jiného odkazu na sestavení rozhraní .NET Framework 4, použijte vzor, uvedený v následujícím pseudokódu.

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

## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect> Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Bezpečnostní oprávnění k přesměrování vazby sestavení](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)
- [Schéma nastavení běhového prostředí](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)
- [Postupy: Vytváření zásad vydavatele](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
