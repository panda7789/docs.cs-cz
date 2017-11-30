---
title: "Rychlejší spuštění aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1e39bf6db28290b7cba600ea1d2012c58633587
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="application-startup-time"></a>Rychlejší spuštění aplikace
Množství času, která je požadována pro aplikaci WPF zahájíte se může značně lišit. Toto téma popisuje různé postupy pro snížení času spuštění dosahovaný a aktuálních pro aplikaci Windows Presentation Foundation (WPF).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Principy Cold spuštění a záložním spuštění  
 Studené spuštění nastane, když vaše aplikace spustí poprvé po restartování systému, nebo při spuštění aplikace, zavřete je a pak spusťte znovu po dlouhé časové období. Když se aplikace spustí, pokud nejsou k dispozici v seznamu Správce paměti Windows pohotovostní požadované stránky (kód, statických dat, registru atd.), dojde k stránkování. Přístup k disku je nezbytné k přivedení stránek do paměti.  
  
 Záložním spuštění nastane, když většina stránek pro hlavní společné součásti language runtime (CLR) jsou již načtena v paměti, což šetří čas přístup nákladné disku. To je důvod, proč spravované aplikaci spustí rychleji, když běží ještě jednou.  
  
## <a name="implement-a-splash-screen"></a>Implementace úvodní obrazovky  
 V případech, kde je důležité, nevyhnutelné zpoždění mezi spuštění aplikace a zobrazení první uživatelského rozhraní, optimalizovat dosahovaný spuštění s použitím *úvodní obrazovka*. Tento přístup zobrazí obrázek téměř okamžitě po spuštění aplikace. Když je aplikace připravená k zobrazení jeho první uživatelského rozhraní, zmenšuje úvodní obrazovka. Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], můžete použít <xref:System.Windows.SplashScreen> třídu pro implementaci úvodní obrazovka. Další informace najdete v tématu [úvodní obrazovka přidání do aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Můžete taky implementovat vlastní úvodní obrazovka pomocí nativní grafiky Win32. Zobrazení vaší implementace před <xref:System.Windows.Application.Run%2A> metoda je volána.  
  
## <a name="analyze-the-startup-code"></a>Analyzovat kód spuštění  
 Zjistěte, proč pomalé cold spuštění. Vstupně-výstupní diskové může být zodpovědná, ale není to vždy. Obecně platí měli byste minimalizovat použití externím prostředkům, jako je například síť, webové služby nebo disk.  
  
 Před zahájením testovacího, ověřte, zda žádná jiná spuštěné aplikace nebo služby pomocí spravovaného kódu nebo WPF kódu.  
  
 Spusťte aplikaci WPF okamžitě po restartování systému a určit, jak dlouho trvalo k zobrazení. Všechny následné spustí aplikace (záložním spuštění) je mnohem rychlejší, problém cold spuštění je pravděpodobně způsobená vstupně-výstupní operace.  
  
 Pokud vaše aplikace je cold spuštění problém nesouvisí s vstupně-výstupních operací, je pravděpodobné, že aplikace provádí některé zdlouhavé inicializace nebo výpočtů, počká pro některé události k dokončení, nebo vyžaduje spoustu JIT – kompilace při spuštění. Následující části popisují některé z těchto situací podrobněji.  
  
## <a name="optimize-module-loading"></a>Optimalizace načítání modulu  
 Použití nástroje například Průzkumníka procesů (Procexp.exe) a Tlist.exe určení, které moduly aplikace načte. Příkaz `Tlist <pid>` ukazuje všechny moduly, které se zavádějí procesem.  
  
 Pokud se nedaří připojit k webu a uvidíte, že je načtený System.Web.dll, a potom je-li modul v aplikaci, například odkazuje toto sestavení. Zkontrolujte, že odkaz je nezbytné.  
  
 Pokud aplikace obsahuje více modulů, je sloučit do jediného modulu. Tento přístup vyžaduje menší nároky na načtení sestavení CLR. Méně sestavení také znamená, že modulu CLR udržovat méně stav.  
  
## <a name="defer-initialization-operations"></a>Odložení operace inicializace  
 Vezměte v úvahu odložení inicializace kódu až po vykreslení hlavního okna aplikace.  
  
 Uvědomte si, že inicializace může provést uvnitř konstruktoru třídy, a pokud kód inicializace odkazuje na jiné třídy, může to způsobit kaskádových vliv, ve kterém jsou prováděny mnoho konstruktory – třída.  
  
## <a name="avoid-application-configuration"></a>Vyhněte se konfigurace aplikace  
 Zvažte vyloučení konfigurace aplikace. Například pokud aplikace má požadavky na konfiguraci jednoduché a má cílových dob striktní spuštění, registru nebo jednoduchý soubor INI může být rychlejší alternativní spuštění.  
  
## <a name="utilize-the-gac"></a>Využívat GAC  
 Pokud sestavení není nainstalována v globální mezipaměti sestavení (GAC), je způsobených hash ověření sestavení se silným názvem a ověřování Ngen bitové kopie, pokud nativních bitových kopií pro toto sestavení. je k dispozici v počítači. Ověření silného názvu je pro instalaci do GAC ve všech sestaveních přeskočeno. Další informace najdete v tématu [Gacutil.exe (Global Assembly Cache Tool)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Použití nástroje Ngen.exe  
 Zvažte použití generátor (Ngen.exe) ve vaší aplikaci. Pomocí Ngen.exe znamená obchodování spotřeby procesoru pro další přístup k disku, protože je pravděpodobné, musí být větší než MSIL image nativních bitových kopií generované Ngen.exe.  
  
 Pokud chcete zlepšit záložním spuštění, byste měli vždycky používat Ngen.exe ve vaší aplikaci, protože tím je zabráněno procesoru náklady JIT – kompilace kódu aplikace.  
  
 V některých scénářích cold spuštění pomocí Ngen.exe může být také užitečné. To je proto není nutné jej načíst kompilátoru za běhu (mscorjit.dll).  
  
 S moduly Ngen a JIT může mít nejhorší vliv. Je to proto musí být načteny mscorjit.dll a při JIT kompilátoru funguje na kód, pokud JIT kompilátor čte metadata sestavení musí se přístup počet stránek v Ngen bitové kopie.  
  
### <a name="ngen-and-clickonce"></a>Ngen a ClickOnce  
 Způsob, jak máte v plánu pro nasazení aplikace lze také nastavit rozdíl v čase zatížení. [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]nasazení aplikace nepodporuje Ngen. Pokud se rozhodnete použít Ngen.exe pro vaši aplikaci, je nutné použít jiný mechanismus pro nasazení, jako je například Instalační služba systému Windows.  
  
 Další informace najdete v tématu [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Rebasing a kolizí adresy knihovny DLL  
 Pokud používáte Ngen.exe, mějte na paměti, že rebasing může dojít, když jsou načteny nativní bitové kopie v paměti. Pokud knihovna DLL nebyla načtena v jeho upřednostňovaná základní adresa, protože je již přidělena tohoto rozsahu adres, načte se zavaděč systému Windows na jiné adrese, což může být časově náročná operace.  
  
 Nástroj virtuální adresu Dump (Vadump.exe) můžete zkontrolujte, jestli jsou moduly, ve kterých jsou soukromá všechny stránky. Pokud je to tento případ, modul může byla rebased na jinou adresu. Proto se nedají sdílet jeho stránky.  
  
 Další informace o tom, jak nastavit základní adresu najdete v tématu [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Optimalizace Authenticode  
 Ověření Authenticode přidá čas spuštění. Authenticode podepsané sestavení muset ověřit s certifikační autoritou (CA). Toto ověření může být časově náročné, protože ho může vyžadovat připojení k síti několikrát stáhnout aktuální seznamy odvolaných certifikátů. Také zajišťuje, že je řetězec úplné platné certifikáty na cestě k důvěryhodnému kořenovému certifikátu. Tento fakt může projevit na několik sekund zpoždění při načítání sestavení.  
  
 Zvažte možnost instalace certifikátu certifikační Autority na klientském počítači, nebo nepoužívejte Authenticode, pokud je to možné. Pokud víte, že vaše aplikace není nutné důkaz vydavatele, nemusí platit náklady na ověření podpisu.  
  
 Počínaje [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], je možnost konfigurace, která umožňuje ověření Authenticode byla vynechána. K tomu, přidejte do souboru app.exe.config následující nastavení:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Další informace najdete v tématu [ \<generatePublisherEvidence > Element](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Porovnání výkonu v systému Windows Vista  
 Správce paměti v systému Windows Vista má technologii nazvanou SuperFetch. SuperFetch analyzuje vzory využití paměti v čase kvůli určení obsahu optimální paměti pro konkrétního uživatele. Funguje nepřetržitě Pořizujte tohoto obsahu.  
  
 Tento postup se liší od technického před načtením v systému Windows XP, který automaticky načte data do paměti bez analýza vzorce používání. V čase pokud uživatel použije aplikaci WPF často v systému Windows Vista, cold spuštění vaší aplikace zvýšit.  
  
## <a name="use-appdomains-efficiently"></a>Efektivně používat domén  
 Pokud je to možné načtení sestavení do domény neutrální kód oblasti a ujistěte se, že nativních bitových kopií, pokud existuje, je používat ve všech domén, které jsou vytvořené v aplikaci.  
  
 Nejlepšího výkonu dosáhnete vynuťte efektivní komunikace mezi doménami snížením volání mezi doménami. Pokud je to možné, použijte volání bez argumentů nebo primitivní typ argumentů.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Pomocí atributu NeutralResourcesLanguage  
 Použití <xref:System.Resources.NeutralResourcesLanguageAttribute> k určení neutrální jazykovou verzi pro <xref:System.Resources.ResourceManager>. Tento přístup zabraňuje hledání úspěšné sestavení.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Použití třídy BinaryFormatter pro serializaci  
 Pokud musíte použít serializace, použijte <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> místo <xref:System.Xml.Serialization.XmlSerializer> třídy. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Třída je implementována v třídy knihovny základní (BCL) v mscorlib.dll sestavení. <xref:System.Xml.Serialization.XmlSerializer> Je implementovaná v sestavení System.Xml.dll, což může být další knihovny DLL pro načtení.  
  
 Pokud je nutné použít <xref:System.Xml.Serialization.XmlSerializer> třídu, můžete dosáhnout lepšího výkonu Pokud předběžnému generování sestavení serializace.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Po spuštění nastavit ClickOnce ke kontrole aktualizací  
 Pokud vaše aplikace používá [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], vyhněte se přístup k síti na spuštění nakonfigurováním [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] na serveru nasazení pro aktualizace po spuštění aplikace.  
  
 Pokud používáte model aplikace (XBAP) prohlížeče XAML, mějte na paměti, [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] kontroluje lokality nasazení aktualizací i v případě, že XBAP se již [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] mezipaměti. Další informace najdete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Automaticky konfigurovat službu PresentationFontCache spuštění  
 První aplikaci WPF má spustit po restartování je služba PresentationFontCache. Tato služba ukládá do mezipaměti systémová písma, zlepšuje přístup písma a se zvýší celkový výkon. Je režijní náklady v spouštění služby a v některých prostředích s řízené, zvažte nakonfigurování service pro automatické spouštění, když dojde k restartování systému.  
  
## <a name="set-data-binding-programmatically"></a>Nastavit datové vazby prostřednictvím kódu programu  
 Místo použití XAML pro nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> deklarativně pro hlavní okno, zvažte jeho prostřednictvím kódu programu v nastavení <xref:System.Windows.Application.OnActivated%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.SplashScreen>  
 <xref:System.AppDomain>  
 <xref:System.Resources.NeutralResourcesLanguageAttribute>  
 <xref:System.Resources.ResourceManager>  
 [Úvodní obrazovka přidání do aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)  
 [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [\<generatePublisherEvidence > elementu](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
