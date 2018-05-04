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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3459ebd2f1df38ac70e9211fd4865e227cd996cb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="redirecting-assembly-versions"></a>Přesměrování verzí sestavení
Můžete přesměrovat kompilaci vazby odkazy na sestavení rozhraní .NET Framework, sestavení třetích stran nebo sestavení vlastní aplikace. Můžete přesměrovat aplikace používat jinou verzi sestavení v mnoha různými způsoby: pomocí zásad vydavatele prostřednictvím konfigurační soubor aplikace; nebo prostřednictvím konfiguračním souboru počítače. Tento článek popisuje, jak funguje sestavení – vazby v rozhraní .NET Framework a jak může být nakonfigurován.  
  
<a name="BKMK_Assemblyunificationanddefaultbinding"></a>   
## <a name="assembly-unification-and-default-binding"></a>Sjednocení sestavení a výchozí vazby  
 Někdy přesměrování vazby na sestavení rozhraní .NET Framework prostřednictvím procesu zvaného *sjednocení sestavení*. Rozhraní .NET Framework se skládá z verzi modulu CLR a o dvacet sestavení rozhraní .NET Framework, které tvoří knihovny typů. Tyto sestavení rozhraní .NET Framework jsou považovány modulem runtime jako na jednu jednotku. Při spuštění aplikace, přesměruje se ve výchozím nastavení všechny odkazy na typy v kódu spustit modulem runtime sestavení rozhraní .NET Framework, které mají stejné číslo verze jako modul runtime, který je načten do procesu. Přesměrování, které se tento model se výchozí chování pro modul runtime.  
  
 Například pokud aplikace odkazuje typy v oboru názvů System.XML a byl vytvořený pomocí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], obsahuje statický odkazy na sestavení System.XML, který se dodává s runtime verze 4.5. Pokud chcete přesměrovat odkaz na vazby tak, aby odkazoval na System.XML sestavení, které se dodávají spolu s rozhraní .NET Framework 4, můžete umístit informace o přesměrování v konfiguračním souboru aplikace. Přesměrování vazby do konfiguračního souboru pro jednotné sestavení rozhraní .NET Framework zruší sjednocení pro toto sestavení.  
  
 Kromě toho můžete ručně přesměrování vazby pro sestavení třetích stran, pokud nejsou k dispozici více verzí sestavení.  
  
<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>   
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Přesměrování verzí sestavení pomocí zásad vydavatele  
 Dodavatelé sestavení může směrovat aplikace na novější verzi sestavení zahrnutím souboru zásad vydavatele s nové sestavení. Soubor zásad vydavatele, který je umístěný v globální mezipaměti sestavení, obsahuje nastavení pro přesměrování sestavení.  
  
 Každý *hlavní*. *méně závažné* verze sestavení má svůj vlastní soubor zásad vydavatele. Například přesměrování z verze 2.0.2.222 k 2.0.3.000 a z verze 2.0.2.321 na verzi 2.0.3.000 obě přejděte do stejného souboru, protože jsou přidruženy verze 2.0. Přesměrování z verze 3.0.0.999 verzi 4.0.0.000 však přejde do souboru pro verzi 3.0.999. Každá hlavní verze rozhraní .NET Framework má svůj vlastní soubor zásad vydavatele.  
  
 Pokud existuje soubor zásad vydavatele pro sestavení, modul runtime zkontroluje tento soubor po zkontrolování konfigurační soubor manifestu a aplikace je sestavení. Dodavatelé by měl použít vydavatel – soubory zásad jenom v případě, že nové sestavení je zpětně kompatibilní s sestavení přesměrování.  
  
 Můžete obejít zásady vydavatele pro vaši aplikaci tak, že zadáte nastavení v konfiguračním souboru aplikace, jak je popsáno v [obcházení část zásad vydavatele](#bypass_PP).  
  
<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>   
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Přesměrování verzí sestavení na úrovni aplikace  
 Existuje několik různých postupů pro změnu chování vazby pro vaši aplikaci pomocí konfiguračního souboru aplikace: Chcete soubor upravit ručně, můžete spolehnout na automatického přesměrování vazby nebo můžete zadat chování vazby obcházení zásad vydavatele.  
  
### <a name="manually-editing-the-app-config-file"></a>Ruční úpravy souboru config aplikace  
 Můžete ručně upravit konfigurační soubor aplikace vyřešení problémů sestavení. Například pokud dodavatele může uvolnit z novější verze sestavení, které vaše aplikace používá bez nutnosti zadávat zásad vydavatele, protože není zaručeno zpětné kompatibility, můžete nastavit aplikaci pro použití novější verze sestavení umístěním sestavení informace v konfiguračním souboru aplikace vazby následujícím způsobem.  
  
```xml  
<dependentAssembly>  
  <assemblyIdentity name="someAssembly"  
    publicKeyToken="32ab4ba45e0a69a1"  
    culture="en-us" />  
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />  
</dependentAssembly>  
```  
  
### <a name="relying-on-automatic-binding-redirection"></a>Spoléhat na automatického přesměrování vazby  
 Počínaje [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], nové plochy aplikací, které se zaměřují [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] pomocí automatického přesměrování vazby. To znamená, že pokud dvě součásti odkazovat různé verze stejného sestavení se silným názvem, modulu runtime automaticky přidá přesměrování vazby sestavení ve výstupním souboru aplikace (app.config) konfigurace na novější verzi. Toto přesměrování přepíše sjednocení sestavení, který jinak může probíhat. Zdrojový soubor app.config není změněn. Řekněme například, že aplikace přímo odkazuje na komponentu out-of-band rozhraní .NET Framework, ale používá knihovnu třetích stran, která cílí na starší verzi stejné komponenty. Při kompilaci aplikace konfiguračního souboru aplikace výstup se upravují tak, aby obsahovala přesměrování vazby součásti na novější verzi. Pokud vytvoříte webovou aplikaci, zobrazí se upozornění sestavení týkající se konfliktů vazby, které se pak vám dává možnost přidat přesměrování nezbytné vazby do konfiguračního souboru webového zdroje.  
  
 Pokud jste ručně přidejte přesměrování vazby do souboru app.config zdroje v době kompilace [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] pokusí sjednocení sestavení podle přesměrování vazby jste přidali. Řekněme například, že vložte následující přesměrování vazby sestavení:  
  
 `<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`  
  
 Jiného projektu ve vaší aplikaci odkazuje verzi 1.0.0.0 do stejného sestavení, přidá automatického přesměrování vazby následující položku do výstupního souboru app.config tak, aby aplikace je jednotná na verzi 2.0.0.0 toto sestavení:  
  
 `<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`  
  
 Můžete povolit automatického přesměrování vazby, pokud aplikace cílí starší verze rozhraní .NET Framework v [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]. Můžete přepsat toto výchozí chování tím, že poskytuje informace o vazbě přesměrování v souboru app.config pro všechny sestavení nebo vypnout funkci přesměrování vazby. Informace o tom, jak tuto funkci zapněte nebo vypněte najdete v tématu [postupy: povolení a zakázání automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).  
  
<a name="bypass_PP"></a>   
### <a name="bypassing-publisher-policy"></a>Obcházení zásady vydavatele  
 Zásada vydavatele v konfiguračním souboru aplikace v případě potřeby můžete přepsat. Například nové verze sestavení, které deklarace identity, aby byly zpětně kompatibilní může stále dojít k narušení aplikace. Pokud chcete obejít zásady vydavatele, přidejte [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu, který chcete [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) element v konfiguračním souboru aplikace a nastavte **použít** atribut **žádné**, která přepisuje všechny předchozí **Ano** nastavení.  
  
 `<publisherPolicy apply="no" />`  
  
 Nepoužívat zásad vydavatele zachovat aplikace spuštěna pro vaše uživatele, ale ujistěte se, že jste potíže nahlásit dodavatele sestavení. Pokud má sestavení souboru zásad vydavatele, dodavatele měli ujistit, že sestavení je zpětně kompatibilní a který můžou klienti použít co nejvíce novou verzi.  
  
<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>   
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Přesměrování verzí sestavení na úrovni počítače  
 Je možné výjimečných případech Pokud chce správce počítače, aby všechny aplikace v počítači a použít konkrétní verzi sestavení. Správce může například každé aplikaci, aby používala konkrétní sestavení verze, vzhledem k tomu, že verze opravy bezpečnostní riziko. Pokud je v konfiguračním souboru počítače přesměrována sestavení, všechny aplikace na tomto počítači, které používají starou budete přesměrováni na použití nové verze. Konfigurační soubor počítače přepíše konfiguračního souboru aplikace a soubor zásad vydavatele. Tento soubor je umístěný ve složce %*runtime instalační cesty*%\Config adresáře. Rozhraní .NET Framework je obvykle nainstalovaný v adresáři %drive%\Windows\Microsoft.NET\Framework.  
  
<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>   
## <a name="specifying-assembly-binding-in-configuration-files"></a>Určení sestavení – vazby v konfiguračních souborech  
 Stejný formát XML se používá k určení přesměrování vazby, zda je v konfiguračním souboru aplikace, konfiguračním souboru počítače nebo soubor zásad vydavatele. Přesměrovat jednu verzi sestavení do druhého, použijte [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) element. **Atribut oldVersion** atributu můžete zadat verzi jednoho sestavení nebo rozsah verzí. `newVersion` Atribut by měl určovat jednu verzi.  Například `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` Určuje, že modul runtime musí používat verzi 2.0.0.0 namísto verzí sestavení mezi 1.1.0.0 a 1.2.0.0.  
  
 Následující příklad kódu ukazuje celou řadu scénářů přesměrování vazby. V příkladu určuje přesměrování pro řadu verze pro `myAssembly`a jednu vazbu přesměrování pro `mySecondAssembly`. V příkladu také určuje, že soubor zásad vydavatele nebude přepsat přesměrování vazeb pro `myThirdAssembly`.  
  
 Chcete-li vytvořit vazbu sestavení, je nutné zadat řetězec "urn: schémata-microsoft-com:asm.v1" s **xmlns** atribut [ \<assemblybinding – >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) značky.  
  
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
  
### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Omezení pro konkrétní verzi vazby sestavení  
 Můžete použít **AppliesTo –** atributu u [ \<assemblybinding – >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element v konfiguračním souboru aplikace pro přesměrování odkazy na sestavení vazbu na konkrétní verzi rozhraní .NET Framework. Tento volitelný atribut používá označíte, jaká verze se vztahuje na číslo verze rozhraní .NET Framework. Pokud žádné **AppliesTo –** atribut zadán, [ \<assemblybinding – >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element platí pro všechny verze rozhraní .NET Framework.  
  
 Například k přesměrování vazby sestavení rozhraní .NET Framework 3.5 sestavení, bude zahrnovat následující kód XML v konfiguračním souboru aplikace.  
  
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
  
 Měli byste zadat informace o přesměrování v pořadí verze. Například zadejte informace o přesměrování vazby sestavení pro sestavení rozhraní .NET Framework 3.5, za nímž následuje sestavení rozhraní .NET Framework 4.5. Nakonec zadejte informace o přesměrování vazby sestavení pro žádné přesměrování sestavení rozhraní .NET Framework, který nepoužívá **AppliesTo –** atribut a proto se vztahuje na všechny verze rozhraní .NET Framework. Pokud dojde ke konfliktu v přesměrování, použije se první odpovídající příkaz přesměrování v konfiguračním souboru.  
  
 Například přesměrovat jeden odkaz na sestavení rozhraní .NET Framework 3.5 a další odkaz na sestavení rozhraní .NET Framework 4, použití vzoru uvedené v následující pseudokódu.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v3.5 ">   
  <!—.NET Framework version 3.5 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v4.0.30319">   
  <!—.NET Framework version 4.0 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- redirects meant for all versions of the runtime -->   
</assemblyBinding>  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [\<bindingRedirect – > elementu](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Bezpečnostní oprávnění k přesměrování vazby sestavení](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Konfigurace aplikací rozhraní .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Schéma nastavení běhového prostředí](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Postupy: Vytváření zásad vydavatele](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
