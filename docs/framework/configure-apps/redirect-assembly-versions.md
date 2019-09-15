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
ms.openlocfilehash: c43ba119b92d4dc1a50b03d6359555ad25f37d08
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971560"
---
# <a name="redirecting-assembly-versions"></a>Přesměrování verzí sestavení

Můžete přesměrovat odkazy na vázání v době kompilace na sestavení .NET Framework, sestavení třetích stran nebo na sestavení vlastní aplikace. Aplikaci můžete přesměrovat tak, aby používala jinou verzi sestavení několika způsoby: prostřednictvím zásad vydavatele, prostřednictvím konfiguračního souboru aplikace; nebo prostřednictvím konfiguračního souboru počítače. Tento článek popisuje, jak vazba sestavení funguje v .NET Framework a jak je možné ji nakonfigurovat.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Sjednocení sestavení a výchozí vazba
 Vazby na .NET Framework sestavení jsou někdy přesměrovány pomocí procesu nazývaného *sjednocení sestavení*. .NET Framework se skládá z verze modulu CLR (Common Language Runtime) a přibližně dvou desítek .NET Framework sestavení, která tvoří knihovnu typů. Tato .NET Framework sestavení jsou zpracována modulem runtime jako jediná jednotka. Ve výchozím nastavení platí, že při spuštění aplikace jsou všechny odkazy na typy v kódu spouštěny modulem runtime směrovány na .NET Framework sestavení, která mají stejné číslo verze jako modul runtime, který je načten v procesu. Přesměrování, která se vyskytují v tomto modelu, jsou výchozím chováním modulu runtime.

 Například pokud vaše aplikace odkazuje na typy v oboru názvů System. XML a byla sestavena pomocí .NET Framework 4,5, obsahuje statické odkazy na sestavení System. XML, které je dodáváno s běhovou verzí 4,5. Chcete-li přesměrovat odkaz vazby tak, aby odkazoval na sestavení System. XML dodávané s .NET Framework 4, můžete informace o přesměrování umístit do konfiguračního souboru aplikace. Přesměrování vazby v konfiguračním souboru pro sestavení sjednocené .NET Framework zruší sjednocení pro toto sestavení.

 Kromě toho můžete chtít ručně přesměrovat vazbu sestavení pro sestavení třetích stran, pokud je k dispozici více verzí.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Přesměrování verzí sestavení pomocí zásad vydavatele
 Dodavatelé sestavení mohou směrovat aplikace do novější verze sestavení zahrnutím souboru zásad vydavatele s novým sestavením. Soubor zásad vydavatele, který je umístěn v globální mezipaměti sestavení (GAC), obsahuje nastavení přesměrování sestavení.

 Každá *Hlavní*verze. *dílčí* verze sestavení má svůj vlastní soubor zásad vydavatele. Například přesměrování z verze 2.0.2.222 na 2.0.3.000 a z verze 2.0.2.321 na verzi 2.0.3.000 patří do stejného souboru, protože jsou přidruženy k verzi 2,0. Přesměrování z verze 3.0.0.999 na verzi 4.0.0.000 však přejde do souboru verze 3.0.999. Každá hlavní verze .NET Framework má svůj vlastní soubor zásad vydavatele.

 Pokud pro sestavení existuje soubor zásad vydavatele, modul runtime tento soubor zkontroluje po kontrole manifestu sestavení a konfiguračního souboru aplikace. Dodavatelé by měli používat soubory zásad vydavatele pouze v případě, že je nové sestavení zpětně kompatibilní s přesměrovaným sestavením.

 Zásady vydavatele pro vaši aplikaci můžete obejít zadáním nastavení v konfiguračním souboru aplikace, jak je popsáno v [části obejití zásad vydavatele](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Přesměrování verzí sestavení na úrovni aplikace
 Existuje několik různých postupů pro změnu chování vazby pro vaši aplikaci prostřednictvím konfiguračního souboru aplikace: soubor můžete ručně upravit, můžete spoléhat na automatické přesměrování vazby nebo můžete určit chování vazby tím, že vynecháte zásady vydavatele.

### <a name="manually-editing-the-app-config-file"></a>Ruční úprava konfiguračního souboru aplikace
 Můžete ručně upravit konfigurační soubor aplikace a vyřešit problémy s sestavením. Například pokud dodavatel může vydávat novější verzi sestavení, které vaše aplikace používá bez poskytnutí zásady vydavatele, protože nezaručuje zpětnou kompatibilitu, můžete svou aplikaci nasměrovat tak, aby používala novější verzi sestavení vložením sestavení. v konfiguračním souboru vaší aplikace navážete informace následujícím způsobem.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Spoléhá se na automatické přesměrování vazby.

Když v aplikaci Visual Studio vytvoříte desktopovou aplikaci, která se zaměřuje na .NET Framework 4.5.1 nebo novější verzi, aplikace použije automatické přesměrování vazby. To znamená, že pokud dvě součásti odkazují na různé verze stejného sestavení se silným názvem, modul runtime automaticky přidá přesměrování vazby na novější verzi sestavení v souboru konfigurace výstupní aplikace (App. config). Toto přesměrování přepíše sjednocení sestavení, které by jinak mohlo probíhat. Zdrojový soubor app.config není změněn. Řekněme například, že vaše aplikace přímo odkazuje na součást mimo pásmo .NET Framework, ale používá knihovnu třetí strany, která cílí na starší verzi stejné komponenty. Při kompilaci aplikace se konfigurační soubor výstupní aplikace změní tak, aby obsahoval přesměrování vazby na novější verzi součásti. Pokud vytvoříte webovou aplikaci, obdržíte upozornění sestavení týkající se konfliktu vazby, který zase poskytuje možnost Přidat potřebné přesměrování vazby na zdrojový konfigurační soubor webu.

Pokud ručně přidáte přesměrování vazby na zdrojový soubor App. config v době kompilace, Visual Studio se pokusí sjednotit sestavení na základě přidaných přesměrování vazby. Řekněme například, že vložíte následující přesměrování vazby pro sestavení:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Pokud jiný projekt ve vaší aplikaci odkazuje na verzi 1.0.0.0 stejného sestavení, automatické přesměrování vazby přidá následující položku do výstupního souboru App. config tak, aby aplikace byla sjednocená na 2.0.0.0 verze tohoto sestavení:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Pokud vaše aplikace cílí na starší verze .NET Framework, můžete povolit automatické přesměrování vazby. Toto výchozí chování můžete přepsat poskytnutím informací o přesměrování vazby v souboru App. config pro jakékoli sestavení nebo vypnutím funkce přesměrování vazby. Informace o tom, jak tuto funkci zapnout nebo vypnout, najdete v [tématu How to: Povolí nebo zakáže automatické přesměrování](how-to-enable-and-disable-automatic-binding-redirection.md)vazby.

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Obejití zásad vydavatele
 V případě potřeby můžete zásady vydavatele v konfiguračním souboru aplikace přepsat. Například nové verze sestavení, které mají nárok na zpětnou kompatibilitu, můžou pořád poškodit aplikaci. Pokud chcete obejít zásadu vydavatele, přidejte [ \<element publisherPolicy >](./file-schema/runtime/publisherpolicy-element.md) do [ \<prvku dependentAssembly >](./file-schema/runtime/dependentassembly-element.md) v konfiguračním souboru aplikace a nastavte atribut **Apply** na **No**, který přepíše všechna předchozí nastavení **Ano** .

 `<publisherPolicy apply="no" />`

 Vynechejte zásady vydavatele, aby vaše aplikace zůstala spuštěná pro vaše uživatele, ale ujistěte se, že jste nahlásili tento problém dodavateli sestavení. Pokud má sestavení soubor zásad vydavatele, dodavatel by měl zajistit, aby bylo sestavení zpětně kompatibilní a aby klienti mohli používat novou verzi co nejvíc.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Přesměrování verzí sestavení na úrovni počítače
 Může dojít k vzácným případům, kdy správce počítače chce, aby všechny aplikace v počítači používaly určitou verzi sestavení. Například správce může chtít, aby každá aplikace používala konkrétní verzi sestavení, protože tato verze opravuje bezpečnostní riziko. Pokud je sestavení Přesměrováno do konfiguračního souboru počítače, všechny aplikace v tomto počítači, které používají starou verzi, budou přesměrovány na použití nové verze. Konfigurační soubor počítače přepíše konfigurační soubor aplikace a soubor zásad vydavatele. Tento soubor se nachází v adresáři%*běhové instalační cesta*% \ config. .NET Framework se obvykle nainstaluje do adresáře%drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Určení vazby sestavení v konfiguračních souborech
 Použijete stejný formát XML k určení přesměrování vazby, pokud je v konfiguračním souboru aplikace, konfiguračním souboru počítače nebo souboru zásad vydavatele. Pro přesměrování jedné verze sestavení na jiný použijte [ \<prvek > bindingRedirect](./file-schema/runtime/bindingredirect-element.md) . Atribut **OldVersion** může určit jednu verzi sestavení nebo rozsah verzí. `newVersion` Atribut by měl určovat jednu verzi.  Například `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` určuje, že modul runtime má použít verzi 2.0.0.0 namísto verzí sestavení mezi 1.1.0.0 a 1.2.0.0.

 Následující příklad kódu ukazuje řadu scénářů přesměrování vazby. Příklad určuje přesměrování pro rozsah verzí pro `myAssembly`a jediné přesměrování vazby pro. `mySecondAssembly` V tomto příkladu se také určuje, že soubor zásad vydavatele nepřepisuje přesměrování vazby pro `myThirdAssembly`.

 Chcete-li vytvořit vazby sestavení, je nutné zadat řetězec "urn: schemas-microsoft-com: asm. v1" s atributem **xmlns** ve [ \<značce assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md) .

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
 V konfiguračním souboru aplikace můžete použít atribut [ \<AppliesTo v assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md) elementu pro přesměrování odkazů na vazby sestavení na konkrétní verzi .NET Framework. Tento nepovinný atribut používá .NET Framework číslo verze k určení verze, na kterou se vztahuje. Pokud ne **appliesTo** atribut zadán, [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element platí pro všechny verze rozhraní .NET Framework.

 Například pro přesměrování vazby sestavení pro sestavení .NET Framework 3,5 byste měli do konfiguračního souboru aplikace zahrnout následující kód XML.

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

 Do pořadí verzí byste měli zadat informace o přesměrování. Například zadejte informace o přesměrování vazby sestavení pro sestavení .NET Framework 3,5 následovaná .NET Frameworkm sestavením 4,5. Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení .NET Framework, které nepoužívá atribut **AppliesTo** , a proto platí pro všechny verze .NET Framework. Pokud dojde ke konfliktu v přesměrování, použije se první shodný příkaz přesměrování v konfiguračním souboru.

 Chcete-li například přesměrovat jeden odkaz na sestavení .NET Framework 3,5 a jiný odkaz na sestavení .NET Framework 4, použijte vzor uvedený v následující pseudokódu.

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

- [Postupy: Povolení a zákaz automatického přesměrování vazby](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect> Element](./file-schema/runtime/bindingredirect-element.md)
- [Bezpečnostní oprávnění k přesměrování vazby sestavení](assembly-binding-redirection-security-permission.md)
- [Sestavení v .NET](../../standard/assembly/index.md)
- [Programování se sestaveními](../../standard/assembly/program.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](index.md)
- [Schéma nastavení běhového prostředí](./file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](./file-schema/index.md)
- [Postupy: Vytvoření zásady vydavatele](how-to-create-a-publisher-policy.md)
