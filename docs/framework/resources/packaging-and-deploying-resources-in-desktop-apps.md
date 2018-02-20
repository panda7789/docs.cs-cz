---
title: "Zabalení a nasazení prostředků v aplikacích klasické pracovní plochy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ab23b263d572a5573de5fc21f15b56e784a9a94
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="packaging-and-deploying-resources-in-desktop-apps"></a>Zabalení a nasazení prostředků v aplikacích klasické pracovní plochy
Aplikací v rozhraní .NET Framework Resource Manageru, reprezentována závisí <xref:System.Resources.ResourceManager> třída načíst lokalizované prostředky. Resource Manager předpokládá, že model hvězdicové slouží k zabalení a nasazení prostředků. Rozbočovače je hlavní sestavení, které obsahuje nelokalizovatelný, spustitelný kód a prostředky pro jednu kulturu, nazvanou neutrální nebo výchozí jazykovou verzi. Představuje výchozí jazykovou verzi záložní jazykovou verzi pro aplikaci. je jazyková verze, jejichž zdroje se použijí, pokud nelze nalézt lokalizované prostředky. Každý paprsek připojí k satelitní sestavení, které obsahuje prostředky pro jednu kulturu, ale neobsahuje žádný kód.  
  
 Existuje několik výhod k tomuto modelu:  
  
-   Prostředky pro nové jazykové verze můžete přidat postupně po nasazení aplikace. Protože následné vývoj specifické pro jazykovou verzi zdrojů může vyžadovat dlouhou dobu, můžete tak nejprve uvolnit hlavní aplikaci a poskytování prostředků specifické pro jazykovou verzi později.  
  
-   Můžete aktualizovat a změnit satelitní sestavení aplikace bez nutnosti rekompilace aplikace.  
  
-   Aplikace je potřeba načíst pouze satelitní sestavení, které obsahují prostředky potřebné pro konkrétní jazykovou verzi. To může výrazně snížit využití systémových prostředků.  
  
 Existují však také nevýhody k tomuto modelu:  
  
-   Je třeba spravovat více sad prostředků.  
  
-   Počáteční náklady na testování aplikace se zvyšuje, protože je nutné vyzkoušet několik konfigurací. Všimněte si, že z dlouhodobého hlediska bude jednodušší a levnější otestovat jednu základní aplikaci s několika satelity, než testovat a udržovat několik paralelních mezinárodní verze.  
  
## <a name="resource-naming-conventions"></a>Zásady vytváření názvů prostředků  
 Pokud balíček s prostředky aplikace, musí název je pomocí zásady vytváření názvů prostředků, které modul common language runtime očekává. Modul runtime identifikuje prostředek jeho název jazykové verze. Každou jazykovou verzi je uveden jedinečný název, který je obvykle kombinací související s jazykem název jazykové verze dvě písmena, malá písmena a v případě potřeby dvě písmena, velká písmena subkulturu název přidružené zemi či oblasti. Název subkultury následuje název jazykové verze, oddělené pomlčkou (-). Mezi příklady patří ja-JP pro japonštinu jako používaný v Japonsku, en US pro angličtinu jako používaný v USA, de-DE pro němčinu jako používaný v Německu nebo de-AT pro němčinu jako používaný v Rakousko. Najdete v článku [referenční dokumentace rozhraní API National jazykové podpory (NLS)](http://go.microsoft.com/fwlink/?LinkId=200048) ve přejděte globální středisku pro vývojáře úplný seznam názvů jazykovou verzi.  
  
> [!NOTE]
>  Informace o vytváření soubory prostředků najdete v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) a [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>Proces získávání náhradních prostředků  
 Pro balení a nasazení prostředků střed a paprsek modelu používá záložní proces najít odpovídající prostředky. Pokud aplikace vyžaduje lokalizovaný prostředek, který je k dispozici, modul common language runtime vyhledá hierarchii jazykových verzí odpovídající záložní prostředků, která nejvíce odpovídá implementované aplikaci uživatele je žádosti a vyvolá výjimku pouze jako poslední možnost. Na každé úrovni hierarchie, pokud je nalezen odpovídající prostředek, modul runtime používá ji. Pokud prostředek není nalezen, pokračuje v hledání na další úrovni.  
  
 Chcete-li zlepšit výkon vyhledávání, použít <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut hlavní sestavení a předejte ji název neutrální jazyk, který bude fungovat s vaším hlavním sestavením.  
  
> [!TIP]
>  Nebudete moci používat [ \<relativebindforresources – >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) konfigurační element pro optimalizaci prostředků záložní proces a proces, pomocí kterého sondy modulu runtime pro sestavení prostředků. Další informace najdete v tématu [optimalizace proces nouzového prostředku](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) části.  
  
 Prostředek, který je záložní proces zahrnuje následující kroky:  
  
1.  První kontrol za běhu [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md) pro sestavení, které odpovídá požadovanou jazykovou verzi pro vaši aplikaci.  
  
     Sestavení prostředků, které jsou sdíleny mnoho aplikací můžete uložit do globální mezipaměti sestavení. To s není pro zahrnutí určité sady prostředků do struktury adresářů každou aplikaci, kterou vytvoříte. Pokud modul runtime najde odkaz na sestavení, vyhledává sestavení pro požadovaný prostředek. Pokud najde položku v sestavení, používá požadovaný prostředek. Pokud položka není nalezena, pokračuje v hledání.  
  
2.  Modul runtime dále zkontroluje adresář aktuálně prováděné sestavení pro adresář, který odpovídá požadovanou jazykovou verzi. Pokud adresář najde, vyhledá adresáře platné satelitní sestavení pro požadovanou jazykovou verzi. Modul runtime pak prohledá satelitní sestavení pro požadovaný prostředek. Pokud najde prostředku v sestavení, použije ho. Pokud se nenajde prostředek, pokračuje v hledání.  
  
3.  Modul runtime další dotazy k určení, zda satelitních sestavení na vyžádání nainstalovat Instalační služby systému Windows. Pokud ano, zpracuje instalace, načte sestavení a vyhledá ho nebo požadovaný prostředek. Pokud najde prostředku v sestavení, použije ho. Pokud se nenajde prostředek, pokračuje v hledání.  
  
4.  Modul runtime vyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události označit, že se nepodařilo najít satelitní sestavení. Pokud zvolíte možnost zpracování události, vaší obslužné rutiny události může vrátit odkaz na satelitní sestavení, jehož prostředky se použije pro vyhledávání. Jinak vrátí obslužné rutiny události `null` a pokračuje v hledání.  
  
5.  Modul runtime dále prohledá globální mezipaměti sestavení znovu, tentokrát pro nadřazené sestavení požadovanou jazykovou verzi. Pokud nadřazené sestavení v globální mezipaměti sestavení existuje, běhové prostředí vyhledává sestavení pro požadovaný prostředek.  
  
     Jazyková verze nadřazené je definován jako odpovídající záložní jazykovou verzi. Zvažte nadřazené položky jako záložní kandidáty, protože zajištění, že žádný prostředek, je vhodnější došlo k výjimce. Tento proces také vám umožní znova využít prostředky. K určitému prostředku na nadřazené úrovni by měla obsahovat pouze v případě, že jazyková verze podřízené nepotřebuje k lokalizaci požadovaný prostředek. Pokud zadáte satelitní sestavení pro en (neutrální angličtina), například en-GB (angličtina jako používaný v Spojené království) a en US (angličtina jako používaný v USA), satelit en by obsahovat běžné terminologii a en-GB a en US satelity mohly poskytovat přepsání pro tyto podmínky, které se liší.  
  
6.  Modul runtime dále zkontroluje adresář aktuálně prováděné sestavení, které chcete zobrazit, pokud obsahuje nadřazený adresář. Pokud nadřazený adresář existuje, modul runtime adresáři hledá platný satelitní sestavení pro nadřazenou jazykovou verzi. Pokud najde sestavení, běhové prostředí vyhledává sestavení pro požadovaný prostředek. Pokud prostředek najde, použije ho. Pokud se nenajde prostředek, pokračuje v hledání.  
  
7.  Modul runtime další dotazy k určení, zda nadřazené satelitní sestavení na vyžádání nainstalovat Instalační služby systému Windows. Pokud ano, zpracuje instalace, načte sestavení a vyhledá ho nebo požadovaný prostředek. Pokud najde prostředku v sestavení, použije ho. Pokud se nenajde prostředek, pokračuje v hledání.  
  
8.  Modul runtime vyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události označit, že se nepodařilo najít nouzový prostředek. Pokud zvolíte možnost zpracování události, vaší obslužné rutiny události může vrátit odkaz na satelitní sestavení, jehož prostředky se použije pro vyhledávání. Jinak vrátí obslužné rutiny události `null` a pokračuje v hledání.  
  
9. Modul runtime dále prohledá nadřazené sestavení, jako předchozí tři kroky prostřednictvím mnoha potenciální úrovně. Každá jazyková verze má jen jednu nadřazenou položku, který je definovaný <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastnost, ale nadřazený může mít svůj vlastní nadřazenou položku. Vyhledejte nadřazené jazykových verzí zastaví činnost, když jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> vlastnost vrátí <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>; pro prostředek záložní neutrální jazykovou verzi není považováno za nadřazenou jazykovou verzi nebo jazykovou verzi, která může mít prostředky.  
  
10. Pokud byly prohledány jazykovou verzi, která byla původně zadaná a všechny nadřazené objekty a stále nebyl nalezen prostředek, prostředek pro výchozí jazykovou verzi (záložní) se používá. Obvykle se prostředky pro výchozí jazykovou verzi jsou součástí sestavení hlavní aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> pro <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> vlastnost <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut označuje, že ultimate záložní umístění zdroje satelitní sestavení, nikoli hlavní sestavení.  
  
    > [!NOTE]
    >  Výchozí prostředek je pouze prostředek, který může být zkompilován s hlavní sestavení. Pokud nezadáte satelitní sestavení pomocí <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut je konečným nouzovým (konečný nadřazený prvek). Proto doporučujeme vždy zahrnovat výchozí sadu prostředků v hlavní sestavení. To pomáhá zabránit výjimek. Zahrnutím výchozí soubor prostředků zadejte zálohu pro všechny prostředky a ujistěte se, že nejméně jeden prostředek je vždy k dispozici pro uživatele, i když není jazykově specifické.  
  
11. Nakonec, pokud modul runtime nenajde prostředek pro kulturu výchozí (záložní), <xref:System.Resources.MissingManifestResourceException> nebo <xref:System.Resources.MissingSatelliteAssemblyException> indikující, že prostředek nelze nalézt je vyvolána výjimka.  
  
 Žádosti o aplikace Předpokládejme například, prostředek lokalizovaný pro španělština (Mexico) (es-MX jazykovou verzi). Modul runtime nejprve hledá globální mezipaměti sestavení pro sestavení, které odpovídá es-MX, ale nebyla nalezena. Modul runtime pak prohledá adresář aktuálně prováděné sestavení pro adresář es-MX. Pokud neexistuje, modul runtime hledá globální mezipaměti sestavení znovu nadřazené sestavení, které se vztahuje k příslušné záložní jazykovou verzi – v tomto případě es (španělština). Pokud není nalezen nadřazené sestavení, modul runtime prohledá všechny potenciální úrovně nadřazeného sestavení pro jazykovou verzi es-MX, dokud nenajde odpovídající prostředek. Pokud není nalezen prostředek, modul runtime používá prostředek pro výchozí jazykovou verzi.  
  
<a name="Optimizing"></a>   
### <a name="optimizing-the-resource-fallback-process"></a>Optimalizace procesu nalezení záložního prostředku  
 Za těchto podmínek můžete optimalizovat proces, pomocí kterého modulu runtime hledá prostředky v satelitní sestavení  
  
-   Satelitní sestavení nasazených ve stejném umístění jako sestavení kódu. Pokud je kód sestavení nainstalováno v [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md), satelitních sestavení jsou také nainstalované v globální mezipaměti sestavení. Pokud sestavení kódu je nainstalován v adresáři, satelitní sestavení jsou nainstalovány ve složkách specifické pro jazykovou verzi tohoto adresáře.  
  
-   Satelitní sestavení nejsou nainstalovány na vyžádání.  
  
-   Kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
 Optimalizace sondy pro satelitní sestavení zahrnutím [ \<relativebindforresources – >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) elementu a nastavení jeho `enabled` atribut `true` v konfiguračním souboru aplikace, jak je znázorněno v následujícím příkladu.  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 Optimalizované testu pro satelitní sestavení je funkce přihlášení. Tedy dodržuje modulu runtime kroků popsaných v [prostředků záložní proces](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) Pokud [ \<relativebindforresources – >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) element nachází konfigurace aplikace souboru a jeho `enabled` je nastavena na hodnotu `true`. Pokud je to tento případ, procesu zjišťování pro satelitní sestavení je upravit takto:  
  
-   Modul runtime používá umístění nadřazeného kódu sestavení testovat pro satelitní sestavení. Pokud je nadřazený sestavení v globální mezipaměti sestavení nainstalováno, modul runtime sondy v mezipaměti, ale není v adresáři aplikace. Pokud je nadřazený sestavení nainstalováno v adresáři aplikace, modulu runtime sondy v adresáři aplikace, ale není v globální mezipaměti sestavení.  
  
-   Modul runtime není dotaz Instalační služby systému Windows pro instalaci na vyžádání satelitních sestavení.  
  
-   Pokud selže test pro určitý prostředek sestavení, modul runtime nevyvolá <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
### <a name="ultimate-fallback-to-satellite-assembly"></a>Ultimate záloha pro satelitní sestavení  
 Volitelně můžete odebrat prostředky z hlavní sestavení a určit, že modul runtime by se měly načíst ultimate nouzové prostředky z satelitní sestavení, která odpovídá konkrétní jazykové verze. Chcete-li řídit záložní proces, použijte <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> konstruktor a zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation> parametr, který určuje, zda by měl správce prostředků extrahovat nouzové prostředky z hlavní sestavení nebo satelitní sestavení.  
  
 Následující příklad používá <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut pro uložení aplikace nouzové prostředky v satelitní sestavení pro jazyk francouzština (fr).  V příkladu má dva soubory založený na textu prostředků, které definují jeden řetězec prostředek s názvem `Greeting`. První, resources.fr.txt, obsahuje prostředek francouzštinu.  
  
```  
Greeting=Bon jour!  
```  
  
 Druhý, resources,ru.txt, obsahuje prostředek ruštinu.  
  
```  
Greeting=Добрый день  
```  
  
 Tyto dva soubory zkompilovány pro soubory .resources spuštěním [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) z příkazového řádku.  Pro prostředek francouzštinu příkaz je:  
  
 **resgen.exe resources.fr.txt**  
  
 Pro ruštinu prostředek příkaz je:  
  
 **resgen.exe resources.ru.txt**  
  
 Soubory .resources jsou vloženy do dynamické knihovny spuštěním [linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) z příkazu řádek pro prostředek francouzštinu následujícím způsobem:  
  
 **al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 a pro ruštinu prostředek následujícím způsobem:  
  
 **al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 Zdrojový kód aplikace se nachází v souboru s názvem Example1.cs nebo Example1.vb. Její součástí <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut označuje, že výchozí prostředek aplikace v podadresáři fr. Ji vytvoří Resource Manager, načte hodnotu `Greeting` prostředků a zobrazí se ke konzole.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Zdrojový kód C# z příkazového řádku můžete zkompilovat pak následujícím způsobem:  
  
 **CSC Example1.cs**  
  
 Příkaz pro kompilátor jazyka Visual Basic je velmi podobný jako:  
  
 **Vbc – Example1.vb**  
  
 Protože nejsou k dispozici žádné prostředky vložených v hlavní sestavení, není nutné kompilovat pomocí `/resource` přepínače.  
  
 Při spuštění v příkladu ze systému, jejichž jazyk je jakoukoli jinou hodnotu než ruština, zobrazí se následující výstup:  
  
```  
Bon jour!  
```  
  
## <a name="suggested-packaging-alternative"></a>Navrhované alternativní balení  
 Vytváření sadu prostředků pro každou subkulturu, který podporuje vaše aplikace může zabránit čas nebo rozpočtu omezení. Místo toho můžete vytvořit jedno satelitní sestavení pro nadřazenou jazykovou verzi, všechny související subkultury můžete použít. Můžete například zadat jedno anglické satelitní sestavení (cs), která jsou načítána uživatelů, kteří požadují anglické prostředky pro konkrétní oblasti a jedno německé satelitní sestavení (de) pro uživatele, kteří požadují oblast německé prostředky. Například požadavky pro němčinu jako používaný v Německu (de-DE), Rakousko (de-AT) a Švýcarska (de-CH) by vrátit zpět k německé satelitní sestavení (de). Výchozí prostředky jsou konečnou zálohou a proto by měla být prostředky, které budou vyžadovány většina uživatelů vaší aplikace, takže pečlivě zvolte tyto prostředky. Tento přístup nasadí prostředky, které jsou méně jazykově specifické, ale může výrazně snížit náklady na lokalizaci vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
