---
title: "Prostředky v aplikacích klasické pracovní plochy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 24b23d3fd4d3c318fd2fad36bbbbe0cb065db453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resources-in-desktop-apps"></a>Prostředky v aplikacích klasické pracovní plochy
Téměř každý produkční kvality aplikace má využívat prostředky. Prostředek je nespustitelná část dat, který je logicky nasazen s aplikací. Prostředek mohou být zobrazeny v aplikaci jako chybové zprávy nebo jako součást uživatelského rozhraní. Prostředků může obsahovat data v různých formách, včetně řetězce, Image a trvalé objekty. (K zápisu do souboru prostředků trvalé objekty, tyto objekty musí být serializovatelný.) Ukládání dat do souboru prostředků, můžete změnit data bez nutnosti rekompilace celou aplikaci. Také umožňuje ukládat data na jednom místě a eliminuje potřebu spoléhají na pevně data uložená na více místech.  
  
 Rozhraní .NET Framework poskytuje komplexní podporu pro vytváření a lokalizace prostředků v aplikacích klasické pracovní plochy. Kromě toho rozhraní .NET Framework podporuje jednoduchý model pro balení a nasazení těchto lokalizovaných prostředků v aplikacích klasické pracovní plochy.  
  
 Informace o prostředcích v technologii ASP.NET najdete v tématu [webové stránky ASP.NET: Přehled prostředků](http://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd) v Centru pro vývojáře aplikace Internet Explorer.  
  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikace používá model různých prostředků z aplikace klasické pracovní plochy a uložit jejich prostředky do souboru indexu (PRI) jeden balíček prostředků. Informace o prostředcích v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v části [vytváření a načítání prostředků v aplikacích pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=241674) ve službě Windows Dev Center.  
  
## <a name="creating-and-localizing-resources"></a>Vytváření a lokalizace prostředků  
 V aplikaci Nelokalizováno můžete soubory prostředků jako úložiště pro data aplikací, platí to hlavně o řetězce, které by jinak byla pevně zakódovaná na více místech ve zdrojovém kódu. Nejčastěji, můžete vytvořit prostředky jako text (TXT) nebo soubory XML (RESX) a pomocí [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) jejich kompilace do binární soubory RESOURCES. Tyto soubory můžete pak vloží ve spustitelném souboru aplikace kompilátorem jazyka. Další informace o vytváření prostředků najdete v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Také je možné lokalizovat prostředky vaší aplikace pro konkrétní jazykové verze. To vám umožní sestavovat lokalizované (přeložené) verze aplikací. Při vývoji aplikace, která používá lokalizované prostředky, které označíte jazykovou verzi, která slouží jako neutrální nebo záložní jazykovou verzi, jejichž zdroje se použijí, pokud jsou k dispozici žádný vhodný prostředky. Prostředky neutrální jazykové verze obvykle ukládají na spustitelný soubor aplikace. Zbývající prostředky pro jednotlivé lokalizované jazykové verze jsou uloženy v samostatné satelitní sestavení. Další informace najdete v tématu [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
## <a name="packaging-and-deploying-resources"></a>Zabalení a nasazení prostředků  
 Nasazení aplikace lokalizované prostředky v [satelitní sestavení](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Satelitní sestavení obsahuje prostředky jednu kulturu; neobsahuje žádný kód aplikace. V modelu nasazení satelitní sestavení vytvoříte aplikaci s jedno sestavení (což je většinou hlavní sestavení) a jeden satelitní sestavení pro každou jazykovou verzi, která podporuje aplikace. Protože satelitní sestavení nejsou součástí hlavní sestavení, můžete snadno nahradit nebo aktualizují prostředky s odpovídající konkrétní jazykové verze bez nahrazení hlavní sestavení aplikace.  
  
 Pečlivě určete, které prostředky budou použity k vytvoření sestavení prostředků výchozí vaší aplikace. Protože je součástí hlavní sestavení, bude vyžadovat změny k němu k nahrazení hlavní sestavení. Pokud není zadán výchozí prostředek, bude vyvolána výjimka při [nouzové procesy prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) pokusí se ho najít. Dobře navržených aplikace pomocí prostředků by nikdy výjimku.  
  
 Další informace najdete v tématu [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) článku.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  
 V době běhu aplikace načte vhodné lokalizované prostředky na základě podle vláken, na základě jazykové verze určeného <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost. Hodnota této vlastnosti je odvozený následujícím způsobem:  
  
-   Přímo přiřazením <xref:System.Globalization.CultureInfo> objekt, který reprezentuje lokalizované jazykovou verzi, která <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Pokud není explicitně přiřazovat jazykovou verzi, načtením výchozí jazykovou verzi vlákna uživatelského rozhraní z <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Pokud výchozí vlákno jazyková verze uživatelského rozhraní není explicitně přiřazeny, načtením jazykovou verzi pro aktuální uživatel v místním počítači voláním Windows `GetUserDefaultUILanguage` funkce.  
  
 Další informace o nastavení aktuální jazykové verze uživatelského rozhraní, najdete v článku <xref:System.Globalization.CultureInfo> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> referenční stránky.  
  
 Prostředky pro aktuální jazykové verze uživatelského rozhraní nebo konkrétní jazykové verze potom můžete načíst pomocí <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídy. I když <xref:System.Resources.ResourceManager> třída se nejčastěji používá pro načítání prostředků v aplikacích klasické pracovní plochy, <xref:System.Resources?displayProperty=nameWithType> obor názvů obsahuje další typy, které můžete použít k načtení prostředků. Mezi ně patří:  
  
-   <xref:System.Resources.ResourceReader> Třídy, která umožňuje provést výčet prostředků vložené do sestavení nebo uložené v souboru samostatné binární Resources. Je užitečná při neznáte přesné názvy prostředků, které jsou k dispozici v době běhu.  
  
-   <xref:System.Resources.ResXResourceReader> Třídy, která vám umožňuje načíst prostředky ze souboru XML (RESX).  
  
-   <xref:System.Resources.ResourceSet> Třídy, která vám umožňuje načíst prostředky konkrétní jazykové verze bez sledování záložní pravidla. Prostředky mohou být uloženy v sestavení nebo samostatný .resources binární soubor. Také můžete vyvíjet <xref:System.Resources.IResourceReader> implementace, která umožňuje používat <xref:System.Resources.ResourceSet> třída pro načítání prostředků z z jiného zdroje.  
  
-   <xref:System.Resources.ResXResourceSet> Třídy, která vám umožňuje načíst všechny položky v souboru prostředků jazyka XML do paměti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>  
 [Základy vytváření aplikací](../../../docs/standard/application-essentials.md)  
 [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [Načítání prostředků](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
