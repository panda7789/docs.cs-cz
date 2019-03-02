---
title: Prostředky v aplikacích .NET
ms.date: 07/25/2018
helpviewer_keywords:
  - 'deploying applications [.NET Framework], resources'
  - 'deploying applications [.NET Core], resources'
  - application resources
  - resource files
  - satellite assemblies
  - localization
  - packaging application resources
  - localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
author: rpetrusha
ms.author: ronpet
---
# <a name="resources-in-net-apps"></a>Prostředky v aplikacích .NET
Téměř každá aplikace produkční kvality musí používat prostředky. Prostředek je jakákoli nespustitelná část dat, která je logicky nasazována s aplikací. Prostředek může zobrazit v aplikaci jako chybové zprávy nebo jako součást uživatelského rozhraní. Prostředky mohou obsahovat data v různých formách, včetně řetězců, obrázků a trvale uložených objektů. (K zápisu do souboru prostředků trvalé objekty, objekty musí být serializovatelné.) Ukládání dat do souboru prostředků vám umožní měnit data bez opětovné kompilace celou aplikaci. Také umožňuje ukládat data na jednom místě a eliminuje nutnost využívají pevně zakódované data, která je uložena v několika umístěních.  
  
 Rozhraní .NET Framework a .NET Core poskytují komplexní podporu pro vytváření a lokalizace prostředků. Kromě toho .NET podporuje jednoduchý model pro vytváření balíčků a nasazení lokalizované prostředky.  
  
 Informace o prostředcích v technologii ASP.NET, naleznete v tématu [webové stránky ASP.NET: Přehled prostředků](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
## <a name="creating-and-localizing-resources"></a>Vytváření a lokalizace prostředků  

V aplikaci nelokalizovaný můžete použít zdrojové soubory jako úložiště pro data aplikací, zejména pro řetězce, která se můžou v opačném případě pevně zakódované v několika umístěních ve zdrojovém kódu. Nejčastěji, můžete vytvářet prostředky jako text (TXT) nebo soubory XML (.resx) a použít [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pro jejich zkompilování do binárních souborů .resources. Tyto soubory může být potom vložen do spustitelného souboru aplikace pomocí kompilátoru jazyka. Další informace o vytváření prostředků najdete v tématu [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  

Také je možné lokalizovat prostředky vaší aplikace pro specifické jazykové verze. To vám umožní sestavovat lokalizované verze (přeloženého) vaší aplikace. Když vyvíjíte aplikaci, která využívá lokalizované prostředky, určíte jazykovou verzi, která slouží jako neutrální nebo záložní jazykovou verzi, jehož prostředky se použijí, pokud jsou k dispozici žádné vhodné prostředky. Ve spustitelném souboru aplikace se obvykle ukládají prostředky neutrální jazykové verze. Zbývající prostředky pro jednotlivé lokalizované jazykové verze jsou uloženy v samostatné satelitních sestavení. Další informace najdete v tématu [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
## <a name="packaging-and-deploying-resources"></a>Zabalení a nasazení prostředků  
 Nasazení aplikace lokalizované prostředky v [satelitní sestavení](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Satelitní sestavení obsahuje prostředky jednu kulturu; neobsahuje žádný kód aplikace. V modelu nasazení satelitního sestavení vytvoříte aplikaci s jedno sestavení (což je obvykle hlavní sestavení) a jeden satelitní sestavení pro jednotlivé jazykové verze, který aplikace podporuje. Protože satelitní sestavení nejsou součástí hlavní sestavení, můžete snadno nahradit nebo aktualizují prostředky s odpovídající konkrétní jazykovou verzi bez nutnosti vyměnit sestavení hlavní aplikace.  
  
 Pečlivě určete, které prostředky budou použity k vytvoření sestavení výchozích prostředků vaší aplikace. Protože je součástí hlavní sestavení, všechny změny nutné k nahrazení hlavní sestavení. Pokud nezadáte výchozí prostředek, bude vyvolána výjimka při [proces získávání náhradních prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) pokusí se ji najít. V dobře navržená aplikace by měl použití prostředků nikdy nevyvolají výjimku.  
  
 Další informace najdete v tématu [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) článku.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  
 V době běhu aplikace načte odpovídající lokalizované prostředky na základě vlákno podle jazykové verze určený poskytovatelem <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost. Hodnota této vlastnosti je odvozen následovně:  
  
-   Přímo přiřazením <xref:System.Globalization.CultureInfo> objekt, který reprezentuje lokalizovanou jazykovou verzi <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Pokud není explicitně přiřazeny jazykovou verzi, načtením výchozí jazyková verze vlákna uživatelského rozhraní z <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Pokud vlákno výchozí jazyková verze uživatelského rozhraní není explicitně přiřazeny, načtením jazykovou verzi pro aktuálního uživatele v místním počítači. Implementace .NET běžící na Windows to provést pomocí volání Windows [ `GetUserDefaultUILanguage` ](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) funkce.  
  
 Další informace o tom, jak je nastavena aktuální jazyková verze uživatelského rozhraní, najdete v článku <xref:System.Globalization.CultureInfo> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> odkazují na stránky.  
  
 Potom můžete načíst prostředky pro aktuální jazykové verze uživatelského rozhraní nebo pro konkrétní jazykovou verzi pomocí <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídy. I když <xref:System.Resources.ResourceManager> třídy se nejčastěji používá pro načítání prostředků, <xref:System.Resources?displayProperty=nameWithType> obor názvů obsahuje další typy, které slouží k načtení prostředků. Zde jsou některé z nich:  
  
-   <xref:System.Resources.ResourceReader> Třídu, která umožňuje vytvořit výčet prostředků vloženy do sestavení nebo uložená v samostatných binárního souboru .resources. To je užitečné, pokud si nejste jisti přesné názvy prostředků, které jsou k dispozici v době běhu.  
  
-   <xref:System.Resources.ResXResourceReader> Třídu, která vám umožňuje načíst prostředky ze souboru XML (.resx).  
  
-   <xref:System.Resources.ResourceSet> Třídu, která vám umožňuje načíst prostředky specifické jazykové verze bez sledování pravidla pro použití náhradní lokality. Prostředky mohou být uloženy v sestavení nebo samostatné binárního souboru .resources. Můžete také vyvíjet <xref:System.Resources.IResourceReader> implementace, která vám umožní použít <xref:System.Resources.ResourceSet> třídy pro načtení prostředků z nějakého jiného zdroje.  
  
-   <xref:System.Resources.ResXResourceSet> Třídu, která vám umožňuje načíst všechny položky v souboru prostředků jazyka XML do paměti.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Základy vytváření aplikací](../../../docs/standard/application-essentials.md)
- [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Načítání prostředků](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
