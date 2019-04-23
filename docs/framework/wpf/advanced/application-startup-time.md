---
title: Rychlejší spuštění aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
ms.openlocfilehash: 72207861850875f08786401aacf7b911b2a5b1f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173027"
---
# <a name="application-startup-time"></a>Rychlejší spuštění aplikace
Množství času, který je požadován pro spuštění aplikace WPF může značně lišit. Toto téma popisuje různé postupy pro zkrácení doby spuštění vnímaná, ve skutečnosti pro aplikace Windows Presentation Foundation (WPF).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Principy úplné spuštění a po teplé spuštění  
 Při spuštění aplikace poprvé po restartu systému dojde k úplné spuštění nebo při spuštění aplikace, zavřete ho a spusťte ji znovu po dlouhou dobu. Při spuštění aplikace, pokud nejsou k dispozici v seznamu Správce paměti Windows požadované stránky (kód, statická data, registru atd.), dojde k stránkování. Přístup k disku je potřeba uvést stránek v paměti.  
  
 Horké spuštění nastane, pokud většina těchto stránek pro hlavní komponenty společného jazykového modulu runtime (CLR) jsou už načtené v paměti, což šetří čas přístupu nákladné disku. To je důvod, proč spravované aplikace spouští rychleji, když je spuštěna jednou.  
  
## <a name="implement-a-splash-screen"></a>Implementace úvodní obrazovky  
 V případech, kde je důležité, nevyhnutelné zpoždění mezi spuštěním aplikace a zobrazení první uživatelského rozhraní, optimalizujte vnímaná spuštění pomocí *úvodní obrazovka*. Tento přístup téměř okamžitě zobrazí obrázek po spuštění aplikace uživatelem. Když je připravený k zobrazení jeho první uživatelského rozhraní aplikace, zmenšuje se na úvodní obrazovce. Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], můžete použít <xref:System.Windows.SplashScreen> třídu pro implementaci úvodní obrazovky. Další informace najdete v tématu [přidání úvodní obrazovky do aplikace WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Můžete také implementovat vlastní úvodní obrazovky pomocí nativní grafické Win32. Zobrazit vaši implementaci před <xref:System.Windows.Application.Run%2A> metoda je volána.  
  
## <a name="analyze-the-startup-code"></a>Analýza kódu po spuštění  
 Zjistěte příčinu pomalé úplné spuštění. Disk vstupně-výstupní operace může být zodpovědná, ale není to vždy. Obecně platí měli byste minimalizovat použití externím prostředkům, jako je například síť, webové služby nebo disk.  
  
 Před testováním, ověřte, že žádná jiná spuštěné aplikace nebo služby použít spravovaný kód nebo kód WPF.  
  
 Spustit aplikaci WPF ihned po restartování a zjistit, jak dlouho trvá zobrazení. Všechny následné spuštění vaší aplikace (teplý spuštění) jsou mnohem rychlejší, úplné spuštění problém je pravděpodobně způsobeno vstupně-výstupních operací.  
  
 Pokud je vaše aplikace úplné spuštění problém nesouvisí s vstupně-výstupních operací, je pravděpodobné, že vaše aplikace provádí některé zdlouhavé inicializace nebo výpočet, čeká na dokončení, některé události nebo vyžaduje velké množství kompilace JIT za spuštění. Následující části popisují některé z těchto situací podrobněji.  
  
## <a name="optimize-module-loading"></a>Optimalizace načítání modulů  
 Použití nástroje jako je například Process Explorer (Procexp.exe) a určit, které moduly Tlist.exe aplikace načte. Příkaz `Tlist <pid>` zobrazí všechny moduly, které jsou načteny procesem.  
  
 Například pokud nejsou připojení k webu a objeví se, že je načten System.Web.dll a pak je-li modul v aplikaci, která odkazuje na toto sestavení. Zkontrolujte, že odkaz je nezbytné.  
  
 Pokud aplikace obsahuje více modulů, sloučit do jediného modulu. Tento přístup vyžaduje méně režie na načtení sestavení CLR. Méně sestavení také znamená, že modul CLR spravuje méně stavu.  
  
## <a name="defer-initialization-operations"></a>Odložení inicializace operací  
 Vezměte v úvahu odložení inicializace kódu až po vykreslení hlavního okna aplikace.  
  
 Mějte na paměti, že inicializace mohou být provedeny v konstruktoru třídy, a pokud inicializační kód odkazuje na jiné třídy, může to způsobit požadovaného kaskádového efektu, ve kterém jsou spouštěny mnoho konstruktor třídy.  
  
## <a name="avoid-application-configuration"></a>Vyhněte se konfigurace aplikace  
 Zvažte, jak se vyhnout konfigurace aplikace. Například pokud aplikace má požadavky na jednoduchou konfiguraci a má striktní spuštění dob, položky registru nebo jednoduchý soubor INI může být rychlejší spouštění alternativu.  
  
## <a name="utilize-the-gac"></a>Využívat GAC  
 Pokud sestavení není nainstalováno v globální mezipaměti sestavení (GAC), je způsobena ověření algoritmu hash sestavení se silným názvem a ověření image Ngen nativní bitové kopie sestavení je k dispozici v počítači. U všech sestavení nainstalovaná v GAC je přeskočeno ověřování silného názvu. Další informace najdete v tématu [Gacutil.exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Použití nástroje Ngen.exe  
 Zvažte použití Native Image Generator (Ngen.exe) ve své aplikaci. Pomocí Ngen.exe znamená, že obchodování spotřeby procesoru pro přístup na disk, protože nativní bitové kopie generované Ngen.exe by mohla být větší než image jazyka MSIL.  
  
 Chcete-li zvýšit rychlost spuštění horké, byste měli použít Ngen.exe vždy ve své aplikaci, protože předejdete tak náklady na využití procesoru JIT kompilaci kódu aplikace.  
  
 V některých scénářích úplné spuštění pomocí Ngen.exe může být také užitečné. Je to proto, že kompilátor JIT (mscorjit.dll) nemusí být načteny.  
  
 S moduly lineární Ngen a JIT může mít nejhorší vliv. Toto je vzhledem k tomu mscorjit.dll musí být načten, když kompilátor JIT pracuje na vašem kódu, mnoho stránek v obrázků Ngen musí nadřazenosti a podřízenosti kompilátor JIT čtení metadat na sestavení.  
  
### <a name="ngen-and-clickonce"></a>Ngen a ClickOnce  
 Způsob, jak máte v úmyslu nasadit vaše aplikace provést také rozdíl v okamžiku načtení. [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] nasazení aplikace nepodporuje Ngen. Pokud se rozhodnete použít Ngen.exe pro vaši aplikaci, budete muset použít jiný mechanismus nasazení, jako je například Instalační služby systému Windows.  
  
 Další informace najdete v tématu [Ngen.exe (Generátor nativních obrázků)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Rebasing a kolize adresy knihovny DLL  
 Pokud používáte Ngen.exe, mějte na paměti, že probíhá přenesení změn může dojít, když jsou nativní bitové kopie načtena do paměti. Pokud knihovna DLL není na jeho upřednostňované základní adrese načíst, protože je už přidělená daného rozsahu adres, zavaděč Windows bude načten na jinou adresu, která může být časově náročná operace.  
  
 Vám pomůže nástroj virtuální adresu výpisu paměti (Vadump.exe) zkontrolujte, jestli jsou moduly, ve kterých jsou privátní všechny stránky. Pokud je to tento případ, modul může mít se přenese se změnami do jinou adresu. Proto není možné sdílet jeho stránky.  
  
 Další informace o tom, jak nastavit základní adresu najdete v tématu [Ngen.exe (Generátor nativních obrázků)](../../tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Optimalizace Authenticode  
 Ověřování Authenticode přidává na dobu spuštění. Sestavení s podpisem Authenticode muset ověřit s certifikační autoritou (CA). Toto ověřování může být časově náročné, protože to může vyžadovat připojení k síti několikrát stáhnout aktuální seznamy odvolaných certifikátů. Je také zajišťuje, že je úplným řetězem platné certifikáty na cestě pro důvěryhodného kořenového. Tento fakt může projevit na několik sekund prodlevy při načítání sestavení.  
  
 Zvažte instalaci certifikátu certifikační Autority v klientském počítači, nebo nepoužívejte Authenticode, pokud je to možné. Pokud víte, že vaše aplikace nemusí důkazy vydavatele, není nutné platit náklady na ověření podpisu.  
  
 Počínaje [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], existuje možnost konfigurace, která umožňuje ověření pomocí technologie Authenticode byla vynechána. Chcete-li to provést, přidejte do souboru app.exe.config následující nastavení:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Další informace najdete v tématu [ \<generatePublisherEvidence > Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Porovnání výkonu v systému Windows Vista  
 Správce paměti v systému Windows Vista se nazývá SuperFetch technologie. SuperFetch analyzuje vzory používání paměti průběžným monitorováním určete obsah paměti optimální pro konkrétního uživatele. Funguje neustále udržovat daný obsah za všech okolností.  
  
 Tento přístup se liší od před načtením technika používaná ve Windows XP, které automaticky načte data do paměti bez analýza vzorů využití. V čase pokud uživatel použije aplikaci WPF často v systému Windows Vista, čas úplné spuštění vaší aplikace zvýšit.  
  
## <a name="use-appdomains-efficiently"></a>Použití objektů třídy AppDomains efektivně  
 Pokud je to možné načtení sestavení do doménově neutrální kód oblasti, abyste měli jistotu, že nativní bitové kopie, pokud existuje, se používá ve všech objektů třídy AppDomains v aplikaci.  
  
 Pro zajištění nejlepšího výkonu vynuťte efektivní komunikaci mezi doménami snížením volání mezi doménami. Pokud je to možné, použijte volání bez argumentů nebo primitivní typ argumentů.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Použijte atribut pro NeutralResourcesLanguage  
 Použití <xref:System.Resources.NeutralResourcesLanguageAttribute> k určení pro neutrální jazykovou verzi <xref:System.Resources.ResourceManager>. Tento přístup se vyhnete vyhledávání neúspěšné sestavení.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Použití BinaryFormatter třídy pro serializaci  
 Pokud je nutné použít serializaci, použijte <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> místo na třídě <xref:System.Xml.Serialization.XmlSerializer> třídy. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Třídy je implementována v třída Library Base (BCL) v sestavení mscorlib.dll. <xref:System.Xml.Serialization.XmlSerializer> Je implementované v sestavení System.Xml.dll, což může být další knihovny DLL pro načtení.  
  
 Pokud je nutné použít <xref:System.Xml.Serialization.XmlSerializer> třídy, které můžete dosáhnout lepší výkon Pokud předběžně generovat sestavení serializace.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Konfigurace technologie ClickOnce pro kontrolu aktualizací po spuštění  
 Pokud vaše aplikace používá [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], vyhněte se přístup k síti při spuštění tím, že nakonfigurujete [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] ke kontrole lokality nasazení aktualizací po spuštění aplikace.  
  
 Pokud používáte model aplikace (XBAP) prohlížeče XAML, mějte na paměti, která [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] i v případě, XBAP, který je již v zkontroluje web pro nasazení aktualizací [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] mezipaměti. Další informace najdete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Automaticky konfigurovat službu PresentationFontCache Start  
 První aplikace WPF pro spuštění po restartování je služba PresentationFontCache. Služba ukládá do mezipaměti systémových písem, zlepšuje písma přístup a celkový výkon. Je další režií při spouštění služby a v některých prostředích řízené, zvažte možnost nakonfigurovat automatické spouštění, při restartování služby.  
  
## <a name="set-data-binding-programmatically"></a>Nastavení datové vazby prostřednictvím kódu programu  
 Namísto použití XAML nastavit <xref:System.Windows.FrameworkElement.DataContext%2A> deklarativně pro hlavní okno, zvažte nastavení prostřednictvím kódu programu v <xref:System.Windows.Application.OnActivated%2A> metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [Přidání úvodní obrazovky do aplikace WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (generátor nativních obrázků)](../../tools/ngen-exe-native-image-generator.md)
- [\<generatePublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
