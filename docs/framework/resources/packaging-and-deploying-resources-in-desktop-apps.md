---
title: Zabalení a nasazení prostředků v aplikacích .NET
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2f0ceced1749f42d57094a09f768c192b49ff4e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131531"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Zabalení a nasazení prostředků v aplikacích .NET
Aplikací spoléhá v rozhraní .NET Framework Resource Manageru, reprezentovaný <xref:System.Resources.ResourceManager> třídy načíst lokalizované prostředky. Správce prostředků se předpokládá, že model střed a paprsek slouží k zabalení a nasazení prostředků. Centrum je hlavní sestavení, která obsahuje spustitelný kód nelokalizovatelné a prostředky pro jediné jazykové verze, volá se, neutrální nebo výchozí jazykovou verzi. Výchozí jazykovou verzi je záložní jazykovou verzi pro aplikaci. je jazykovou verzi, jehož prostředky se použijí, pokud nelze najít lokalizované prostředky. Každého paprsku se připojí k satelitní sestavení, která obsahuje prostředky pro jediné jazykové verze, ale neobsahuje žádný kód.  
  
 Existuje několik výhod tohoto modelu:  
  
-   Prostředky pro nové jazykové verze můžete inkrementálně přidávat po nasazení aplikace. Protože další rozvoj prostředky specifické pro jazykovou verzi může vyžadovat značné množství času, to umožňuje nejdřív uvolnit hlavní aplikaci a poskytovat prostředky specifické pro jazykovou verzi později.  
  
-   Můžete aktualizovat a změnit satelitní sestavení aplikace bez nutnosti znovu kompilovat aplikace.  
  
-   Aplikace je potřeba načíst pouze satelitní sestavení, které obsahují prostředky potřebné pro konkrétní jazykovou verzi. To může výrazně snížit využívání systémových prostředků.  
  
 Existují však také nevýhody tohoto modelu:  
  
-   Musíte spravovat několik sad prostředků.  
  
-   Počáteční náklady na testování aplikace zvýší, protože je nutné vyzkoušet několik konfigurací. Všimněte si, že v dlouhodobém horizontu je jednodušší a méně nákladné na testování jedné základní aplikace s několika satelity než testování a udržovat několik paralelní mezinárodní verze.  
  
## <a name="resource-naming-conventions"></a>Zásady vytváření názvů prostředků  
 Když vytvoříte balíček prostředků vaší aplikace, je nutné pojmenovat pomocí zásady vytváření názvů prostředků, které se očekává, že modul common language runtime. Modul runtime identifikuje prostředek podle názvu jazykové verze. Jednotlivé jazykové verze je uveden jedinečný název, který je obvykle kombinací názvu dvě písmena, malá písmena jazykové verze přidružený jazyk a v případě potřeby dvě písmena, velká písmena subkulturu název přidružené zemi nebo oblast. Název subkultury následuje název jazykové verze, které jsou odděleny spojovníkem (-). Mezi příklady patří ja-JP pro japonštinu, jako používá se v Japonsku je en US pro angličtinu, jak je slyšet ve Spojených státech, de-DE pro němčinu jako používaný v Německu nebo de AT pro němčinu jako používaný v Rakousko. Zobrazit [Reference k rozhraní API národní jazykové podpory (NLS)](https://go.microsoft.com/fwlink/?LinkId=200048) na globální Centrum pro vývojáře Go pro úplný seznam všech názvech jazykových verzí.  
  
> [!NOTE]
>  Informace o vytváření souborů prostředků naleznete v tématu [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) a [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>Proces získávání náhradních prostředků  
 Model střed a paprsek pro balení a nasazování prostředků používá proces získávání náhradních k vyhledání příslušné prostředky. Pokud aplikace požaduje lokalizovaný prostředek, který je k dispozici, modul common language runtime vyhledá hierarchii jazykových verzí odpovídající záložní prostředky, který nejlépe odpovídá uživatele aplikace požadavku uživatele a vyvolá výjimku, pouze jako poslední možnost. Na všech úrovních hierarchie Pokud je nalezen odpovídající prostředek, modul runtime používá. Pokud prostředek není nalezen, vyhledávání pokračuje na další úroveň.  
  
 Chcete-li zlepšit výkon vyhledávání, použijte <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut do hlavního sestavení a předejte mu název neutrální jazyk, který bude fungovat s vaším hlavním sestavením.  
  
### <a name="net-framework-resource-fallback-process"></a>Proces získávání náhradních prostředků rozhraní .NET framework
 Proces získávání náhradních prostředků rozhraní .NET Framework zahrnuje následující kroky:

> [!TIP]
>  Je možné použít [ \<relativebindforresources – >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) konfiguračního prvku optimalizace procesu nalezení záložního prostředku a proces, podle kterého modul runtime sondy pro sestavení prostředků. Další informace najdete v tématu [optimalizovat proces záložního prostředku](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) oddílu.  
  
1.  První kontroly za běhu [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md) pro sestavení, která odpovídá požadovanou jazykovou verzi pro vaši aplikaci.  
  
     Sestavení prostředků, které sdílí mnoho aplikací může ukládat do globální mezipaměti sestavení. Nebudete muset zahrnout konkrétní sady prostředků do struktury adresářů každou aplikaci, kterou vytvoříte. Pokud modul runtime vyhledá odkaz na sestavení, vyhledá sestavení pro požadovaný prostředek. Pokud najde položku v sestavení, použije se požadovaný prostředek. Pokud se položka nenajde, pokračuje v hledání.  
  
2.  Modul runtime příště připojí adresáři právě spuštěné sestavení pro podadresář, který odpovídá požadovanou jazykovou verzi. Pokud najde podadresáři, hledá podadresář pro platné satelitní sestavení pro požadovanou jazykovou verzi. Modul runtime hledá pak satelitní sestavení pro požadovaný prostředek. Pokud najde prostředku v sestavení, používá ho. Pokud se prostředek nenajde, pokračuje v hledání.
  
3.  Modul runtime vedle dotazuje Instalační služby systému Windows k určení, zda se má nainstalovat na vyžádání do satelitního sestavení. Pokud ano, zpracovává instalace, načte sestavení a jeho prohledává požadovaný prostředek. Pokud najde prostředku v sestavení, používá ho. Pokud se prostředek nenajde, pokračuje v hledání.  
  
4.  Modul runtime vyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost označující, že se jedná o satelitní sestavení nebylo nalezeno. Pokud se rozhodnete ke zpracování události, vaše obslužná rutina události může vrátit odkaz na satelitní sestavení, jehož prostředky se použije pro vyhledávání. V opačném případě vrátí obslužná rutina události `null` a pokračuje v hledání.  
  
5.  Modul runtime další prohledá mezipaměti globálního sestavení znovu, tentokrát pro nadřazené sestavení požadovanou jazykovou verzi. Pokud existuje nadřazený sestavení v globální mezipaměti sestavení, modul runtime vyhledá sestavení pro požadovaný prostředek.  
  
     Nadřazená jazykové verze je definován jako odpovídající záložní jazykovou verzi. Zvažte rodiče jako kandidáty pro použití náhradní lokality, protože za předpokladu, že všechny prostředky je vhodnější než došlo k výjimce. Tento proces také umožňuje znovu použít prostředky. Prostředek na nadřazené úrovni by měl obsahovat pouze v případě, že jazykovou verzi podřízené nemusí lokalizovat požadovaný prostředek. Například, pokud zadáte satelitní sestavení pro `en` (neutrální v angličtině), `en-GB` (v angličtině jako používaný ve Spojeném království), a `en-US` (v angličtině jako používaný v USA), `en` satelitní by obsahoval společné terminologie a `en-GB` a `en-US` by mohly poskytovat přepsání pro pouze výrazy, které se liší.
  
6.  Modul runtime příště připojí adresář aktuálně prováděné sestavení, pokud obsahuje nadřazeného adresáře. Pokud nadřazeném adresáři existuje, modul runtime vyhledá v adresáři sestavení platný satelit pro nadřazenou jazykovou verzi. Pokud najde sestavení, modul runtime vyhledá sestavení pro požadovaný prostředek. Pokud najde zdroj, používá ho. Pokud se prostředek nenajde, pokračuje v hledání.  
  
7.  Modul runtime vyhledá další instalační služby systému Windows k určení, zda se má nainstalovat na vyžádání nadřazené satelitní sestavení. Pokud ano, zpracovává instalace, načte sestavení a jeho prohledává požadovaný prostředek. Pokud najde prostředku v sestavení, používá ho. Pokud se prostředek nenajde, pokračuje v hledání.  
  
8.  Modul runtime vyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost označující, že se nepodařilo najít odpovídající záložní prostředky. Pokud se rozhodnete ke zpracování události, vaše obslužná rutina události může vrátit odkaz na satelitní sestavení, jehož prostředky se použije pro vyhledávání. V opačném případě vrátí obslužná rutina události `null` a pokračuje v hledání.  
  
9. Modul runtime další prohledá nadřazené sestavení, stejně jako v předchozí tři kroky na mnoho možných úrovních. Jednotlivé jazykové verze mají pouze jeden nadřazený prvek, který je definovaný <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastnost, ale nadřazený může mít svůj vlastní nadřazený. Hledat nadřazená jazykové verze chvíle, kdy se jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> vrátí vlastnost <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>; pro použití náhradní lokality, invariantní jazyková verze není považováno za nadřazenou jazykovou verzi nebo jazykovou verzi, která může mít prostředky prostředků.  
  
10. Pokud byly prohledány všechny nadřazené položky a pro jazykovou verzi, který byl původně zadán a stále prostředek nenajde, použije se prostředků pro výchozí jazykovou verzi (použití náhradní lokality). Prostředky pro výchozí jazykovou verzi jsou obvykle součástí sestavení hlavní aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> pro <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> vlastnost <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut označuje, že ultimate záložní umístění zdroje satelitní sestavení, nikoli hlavní sestavení.  
  
    > [!NOTE]
    >  Výchozí prostředek je jediný zdroj, který může být sestaven s hlavním sestavením. Pokud nezadáte satelitní sestavení s použitím <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut, je ultimate použití náhradní lokality (konečný nadřazený prvek). Proto doporučujeme vždy zahrnovat výchozí sadu prostředků ve vašem hlavním sestavení. To pomáhá zabránit vyvolané výjimky. Zahrnutím výchozí prostředek souboru zadejte záložní pro všechny prostředky a zkontrolujte, že aspoň jeden prostředek je vždy k dispozici pro uživatele, i když není jazykově specifické.
  
11. Nakonec, pokud modul runtime nedokáže najít prostředek pro výchozí kulturu (použití náhradní lokality), <xref:System.Resources.MissingManifestResourceException> nebo <xref:System.Resources.MissingSatelliteAssemblyException> k označení, že se nenašel prostředek je vyvolána výjimka.  
  
 Předpokládejme například, žádosti o aplikace prostředku lokalizované pro španělština (Mexiko) ( `es-MX` jazykové verze). Modul runtime nejprve hledá globální mezipaměti sestavení pro sestavení, která odpovídá `es-MX`, ale nebyl nalezen. Potom prohledá adresář právě spuštěné sestavení pro modul runtime `es-MX` adresáře. Pokud se to nepovede, modul runtime vyhledává globální mezipaměti sestavení znovu nadřazené sestavení, která odráží odpovídající záložní jazykovou verzi – v takovém případě `es` (španělština). Pokud se nenajde nadřazené sestavení, modul runtime hledá všechny potenciální úrovně nadřazeného sestavení pro `es-MX` jazykovou verzi, dokud nenajde odpovídající prostředek. Pokud se prostředek nenajde, modul runtime používá prostředek pro výchozí jazykovou verzi.
  
<a name="Optimizing"></a>   
#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optimalizace procesu nalezení záložního prostředku rozhraní .NET Framework
 Za následujících podmínek můžete optimalizovat proces, podle kterého modul runtime vyhledává prostředky v satelitní sestavení  
  
-   Satelitní sestavení jsou nasazené ve stejném umístění jako sestavení kódu. Pokud kód sestavení nainstaluje [Global Assembly Cache](../../../docs/framework/app-domains/gac.md), satelitní sestavení jsou také nainstalované v globální mezipaměti sestavení. Pokud sestavení kódu je nainstalováno v adresáři, satelitních sestavení se instalují do složky specifické pro jazykovou verzi daného adresáře.  
  
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
  
 Optimalizované sondy pro satelitní sestavení je přihlašovaná funkce. To znamená, modul runtime provede kroky uvedené v [proces pro použití náhradní lokality prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) není-li [ \<relativebindforresources – >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) prvek nachází v konfiguraci vaší aplikace soubor a jeho `enabled` atribut je nastaven na `true`. Pokud je to tento případ, je proces zjišťování pro satelitní sestavení upraveny následujícím způsobem:  
  
-   Modul runtime používá umístění nadřazeného kód sestavení pro sběr dat pro satelitní sestavení. Pokud je sestavení nadřazené nainstalováno v globální mezipaměti sestavení, testy modulu runtime v mezipaměti, ale ne v adresáři aplikace. Pokud je sestavení nadřazené nainstalováno v adresáři aplikace, modul runtime testy v adresáři aplikace, ale ne v globální mezipaměti sestavení.  
  
-   Modul runtime nepodporuje dotaz Instalační služby systému Windows pro instalaci na vyžádání satelitních sestavení.  
  
-   Pokud selže test pro určitý prostředek sestavení modulu runtime nevyvolá <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  

### <a name="net-core-resource-fallback-process"></a>Proces získávání náhradních prostředků .NET core
 Proces získávání náhradních prostředků .NET Core zahrnuje následující kroky:

1.  Modul runtime pokusí se načíst satelitní sestavení pro požadovanou jazykovou verzi.
     * Ověří adresáři právě spuštěné sestavení pro podadresář, který odpovídá požadovanou jazykovou verzi. Pokud najde podadresáři, podadresář hledá platný satelitní sestavení pro požadovanou jazykovou verzi a jejím načítání.

       > [!NOTE]
       >  V systémech s případ sensistive systémy souborů (to znamená, Linux a macOS) vyhledávání podadresář název jazykové verze je velká a malá písmena.  Název podadresáře musí přesně odpovídat velikost písmen <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (například `es` nebo `es-MX`).

       > [!NOTE]
       > Pokud programátorovi obsahuje odvozené kontext načtení vlastního sestavení ze <xref:System.Runtime.Loader.AssemblyLoadContext>, situace je složitá.  Pokud prováděné sestavení bylo načteno do vlastní místní, načte modul runtime do vlastní místní satelitní sestavení.  Podrobnosti jsou mimo rozsah pro tento dokument.  Zobrazit <xref:System.Runtime.Loader.AssemblyLoadContext>.

     * Pokud se sestavit satelit nebyl nalezen, <xref:System.Runtime.Loader.AssemblyLoadContext> vyvolá <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> událost označující, že se jedná o satelitní sestavení nebylo nalezeno. Pokud se rozhodnete ke zpracování události, může vaše obslužná rutina události načtení a vrátit odkaz do satelitního sestavení.
     * Pokud satelitní sestavení stále nebyl nalezen, AssemblyLoadContext způsobí, že doména AppDomain k aktivaci <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost označující, že se jedná o satelitní sestavení nebylo nalezeno. Pokud se rozhodnete ke zpracování události, může vaše obslužná rutina události načtení a vrátit odkaz do satelitního sestavení.

2. Pokud se najde satelitní sestavení, modul runtime vyhledá v něm pro požadovaný prostředek. Pokud najde prostředku v sestavení, používá ho. Pokud se prostředek nenajde, pokračuje v hledání.

     > [!NOTE]
     >  K vyhledání prostředku v satelitní sestavení, modul runtime vyhledá soubor prostředků požadoval <xref:System.Resources.ResourceManager> pro aktuální <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.  V rámci prostředku souboru ho seaches jako název požadovaný prostředek.  Pokud se buď nenajde, považuje za zdroj nebyl nalezen.

3. Modul runtime vedle vyhledá sestavení nadřazenou jazykovou verzi na mnoho možných úrovních, pokaždé, když opakováním kroků 1 a 2.

     Nadřazená jazykové verze je definován jako odpovídající záložní jazykovou verzi. Zvažte rodiče jako kandidáty pro použití náhradní lokality, protože za předpokladu, že všechny prostředky je vhodnější než došlo k výjimce. Tento proces také umožňuje znovu použít prostředky. Prostředek na nadřazené úrovni by měl obsahovat pouze v případě, že jazykovou verzi podřízené nemusí lokalizovat požadovaný prostředek. Například, pokud zadáte satelitní sestavení pro `en` (neutrální v angličtině), `en-GB` (v angličtině jako používaný ve Spojeném království), a `en-US` (v angličtině jako používaný v USA), `en` satelitní obsahuje společné terminologie a `en-GB` a `en-US` satelity poskytuje přepsání pro pouze výrazy, které se liší.

     Jednotlivé jazykové verze mají pouze jeden nadřazený prvek, který je definovaný <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastnost, ale nadřazený může mít svůj vlastní nadřazený. Hledat nadřazená jazykové verze chvíle, kdy se jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> vrátí vlastnost <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Pro použití náhradní lokality prostředek invariantní jazyková verze není považována za nadřazenou jazykovou verzi jazykovou verzi, která může mít prostředky.

4. Pokud byly prohledány všechny nadřazené položky a pro jazykovou verzi, který byl původně zadán a stále prostředek nenajde, použije se prostředků pro výchozí jazykovou verzi (použití náhradní lokality). Prostředky pro výchozí jazykovou verzi jsou obvykle součástí sestavení hlavní aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> pro <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> vlastnost umožňující označit, že ultimate záložní umístění zdroje je satelitní sestavení spíše než hlavní sestavení.

    > [!NOTE]
    >  Výchozí prostředek je jediný zdroj, který může být sestaven s hlavním sestavením. Pokud nezadáte satelitní sestavení s použitím <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut, je ultimate použití náhradní lokality (konečný nadřazený prvek). Proto doporučujeme vždy zahrnovat výchozí sadu prostředků ve vašem hlavním sestavení. To pomáhá zabránit vyvolané výjimky. Včetně výchozího souboru prostředků, zadejte záložní pro všechny prostředky a ujistěte se, že aspoň jeden prostředek vždy k dispozici pro uživatele, i když není jazykově specifické.

5. Nakonec, pokud modul runtime nedokáže najít soubor prostředků pro výchozí (základní) jazykové verze, <xref:System.Resources.MissingManifestResourceException> nebo <xref:System.Resources.MissingSatelliteAssemblyException> k označení, že se nenašel prostředek je vyvolána výjimka.  Pokud je nalezen soubor prostředků, ale požadovaný prostředek není k dispozici žádosti vrátí `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Ultimate nouzového řešení ověření pomocí satelitní sestavení  
 Můžete volitelně odebrat prostředky z hlavního sestavení a určit, že modul runtime by se měly načíst záložním prostředkům v satelitním sestavení, která odpovídá konkrétní jazykovou verzi. K řízení procesu pro použití náhradní lokality, můžete použít <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> konstruktor a zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation> parametr, který určuje, zda správce prostředků by měl extrahovat záložní prostředky z hlavního sestavení nebo satelitního sestavení.  
  
 Následující příklad rozhraní .NET Framework používá <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut pro uložení aplikační záložní prostředky v satelitní sestavení pro francouzská (`fr`) jazyk.  Tento příklad obsahuje dva soubory prostředků založený na textu, které definují jeden řetězcový prostředek pojmenovaný `Greeting`. První, resources.fr.txt, obsahuje prostředek francouzštinu.
  
```  
Greeting=Bon jour!  
```  
  
 Druhý, resources,ru.txt, ruštině prostředek obsahuje.  
  
```  
Greeting=Добрый день  
```  
  
 Tyto dva soubory jsou zkompilovány do souborů .resources spuštěním [nástroje resource file generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) z příkazového řádku.  Pro prostředek francouzštinu příkaz je:  
  
 **resgen.exe resources.fr.txt**  
  
 Pro prostředek ruštině je příkaz:  
  
 **Resgen.exe resources.ru.txt**  
  
 Soubory .resources jsou vloženy do knihoven DLL spuštěním [programu assembly linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) z příkazu řádek pro francouzštinu prostředek následujícím způsobem:  
  
 **Al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 a pro prostředek Ruskou jazykovou následujícím způsobem:  
  
 **Al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 Zdrojový kód aplikace se nachází v souboru s názvem Example1.cs nebo Example1.vb. Její součástí <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut označuje, že výchozí prostředek aplikace v podadresáři fr. Vytvoří instanci Resource Manageru, načte hodnotu `Greeting` prostředků a zobrazí ji do konzoly.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Zdrojový kód C# z příkazového řádku můžete poté zkompilovat následujícím způsobem:  
  
```console 
csc Example1.cs
```
  
 Příkaz pro kompilátor jazyka Visual Basic je velmi podobné:  
  
```console
vbc Example1.vb
```  
  
 Protože nejsou žádné prostředky v hlavním sestavení, není nutné kompilovat s použitím `/resource` přepnout.  
  
 Pokud spustit příklad ze systému, jejíž jazyk nic jiného než ruština zobrazí následující výstup:  
  
```  
Bon jour!  
```  
## <a name="suggested-packaging-alternative"></a>Navrhovaná alternativní balení  
 Vytvoření sady prostředků pro každou subkulturu, kterou podporuje vaše aplikace může zabránit omezení času a rozpočtu. Místo toho můžete vytvořit jeden satelitní sestavení pro nadřazenou jazykovou verzi, že všechny související subkultury můžete použít. Například může poskytovat jednotné anglické satelitní sestavení (cs), která jsou načítána uživatelů, kteří požadují anglické prostředky specifické pro oblast a jedno německé satelitní sestavení (de) pro uživatele, kteří žádají o německý prostředky specifické pro oblast. Například požadavky pro němčinu jako používaný v Německu (de-DE), Rakousko (de-AT) a Švýcarska (de-CH) by vrátit zpět k německé satelitní sestavení (de). Výchozí prostředky jsou poslední použití náhradní lokality a proto musí být prostředky, které bude vyžádána většinou uživatelé vaší aplikace, takže pečlivě tyto prostředky. Tento přístup nasazuje prostředky, které jsou méně jazykově specifické, ale může výrazně snížit náklady na lokalizaci vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
