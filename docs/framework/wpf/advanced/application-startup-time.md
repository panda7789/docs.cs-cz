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
ms.openlocfilehash: 0fae3ac1769163101dcdb183f4c5c2135354b1fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145420"
---
# <a name="application-startup-time"></a>Rychlejší spuštění aplikace
Množství času, který je nutný pro wpf aplikace ke spuštění se může značně lišit. Toto téma popisuje různé techniky pro zkrácení vnímané a skutečné doby spuštění aplikace WPF (Windows Presentation Foundation).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Principy studeného spuštění a teplého spuštění  
 Studené spuštění nastane při prvním spuštění aplikace po restartování systému nebo při spuštění aplikace, zavřete ji a potom ji znovu spustit po dlouhé době. Při spuštění aplikace, pokud požadované stránky (kód, statická data, registr, atd.) nejsou k dispozici v pohotovostním seznamu správce paměti systému Windows, dojde k chybám stránky. Přístup k disku je nutné přenést stránky do paměti.  
  
 Teplé spuštění nastane, když většina stránek pro hlavní součásti CLR (COMMON Language Runtime) jsou již načteny v paměti, což šetří nákladné čas přístupu na disk. To je důvod, proč se spravovaná aplikace spustí rychleji, když se spustí podruhé.  
  
## <a name="implement-a-splash-screen"></a>Implementace úvodní obrazovky  
 V případech, kdy je významné, nevyhnutelné zpoždění mezi spuštěním aplikace a zobrazení prvního ui, optimalizovat vnímané spuštění čas pomocí *úvodní obrazovky*. Tento přístup zobrazí obrázek téměř okamžitě po spuštění aplikace uživatelem. Když je aplikace připravena k zobrazení prvního uhlavního nastavení, úvodní obrazovka zmizí. Počínaje rozhraním .NET Framework 3.5 SP1 <xref:System.Windows.SplashScreen> můžete použít třídu k implementaci úvodní obrazovky. Další informace naleznete [v tématu Přidání úvodní obrazovky do aplikace WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Můžete také implementovat vlastní úvodní obrazovku pomocí nativní grafiky Win32. Zobrazí implementaci před <xref:System.Windows.Application.Run%2A> voláním metody.  
  
## <a name="analyze-the-startup-code"></a>Analýza spouštěcího kódu  
 Určete důvod pomalého studeného spuštění. Disk I/O může být zodpovědný, ale to není vždy případ. Obecně byste měli minimalizovat využití externích prostředků, jako je síť, webové služby nebo disk.  
  
 Před testováním ověřte, zda žádné jiné spuštěné aplikace nebo služby nepoužívají spravovaný kód nebo kód WPF.  
  
 Spusťte aplikaci WPF ihned po restartování počítače a zjistěte, jak dlouho trvá zobrazení. Pokud jsou všechny následné spuštění aplikace (teplé spuštění) mnohem rychlejší, je problém studeného spuštění s největší pravděpodobností způsoben vstupně-nevstupněm/va.  
  
 Pokud problém studeného spuštění aplikace nesouvisí s vstupně-v, je pravděpodobné, že aplikace provede zdlouhavé inicializace nebo výpočtu, čeká na dokončení některé události nebo vyžaduje hodně kompilace JIT při spuštění. Následující části popisují některé z těchto situací podrobněji.  
  
## <a name="optimize-module-loading"></a>Optimalizace načítání modulu  
 Pomocí nástrojů, jako je Process Explorer (Procexp.exe) a Tlist.exe k určení, které moduly aplikace načte. Příkaz `Tlist <pid>` zobrazuje všechny moduly, které jsou načteny procesem.  
  
 Pokud se například nepřipojujete k webu a zjistíte, že je načten soubor System.Web.dll, je v aplikaci modul, který odkazuje na toto sestavení. Zkontrolujte, zda je odkaz nezbytný.  
  
 Pokud vaše aplikace obsahuje více modulů, sloučit do jednoho modulu. Tento přístup vyžaduje méně CLR zatížení sestavení režie. Méně sestavení také znamená, že CLR udržuje menší stav.  
  
## <a name="defer-initialization-operations"></a>Odložit inicializační operace  
 Zvažte odložení inicializačního kódu až po vykreslení hlavního okna aplikace.  
  
 Uvědomte si, že inicializace může být provedena uvnitř konstruktoru třídy a pokud inicializační kód odkazuje na jiné třídy, může způsobit kaskádový efekt, ve kterém je spuštěno mnoho konstruktorů třídy.  
  
## <a name="avoid-application-configuration"></a>Vyhněte se konfiguraci aplikace  
 Zvažte možnost vyhnout se konfiguraci aplikace. Například pokud aplikace má jednoduché požadavky na konfiguraci a má přísné cíle času spuštění, položky registru nebo jednoduchý soubor INI může být rychlejší alternativou spuštění.  
  
## <a name="utilize-the-gac"></a>Využijte GAC  
 Pokud sestavení není nainstalován v globální mezipaměti sestavení (GAC), dochází ke zpoždění způsobené ověření hash sestavení se silným názvem a ověření image Ngen, pokud nativní bitová kopie pro toto sestavení je k dispozici v počítači. Ověření silného názvu je přeskočeno pro všechna sestavení nainstalovaná v gac. Další informace najdete v tématu [Gacutil.exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Použití nástroje Ngen.exe  
 Zvažte použití generátoru nativního obrazu (Ngen.exe) v aplikaci. Použití programu Ngen.exe znamená obchodování spotřeby procesoru pro větší přístup k disku, protože nativní bitová kopie generovaná programem Ngen.exe bude pravděpodobně větší než bitová kopie MSIL.  
  
 Chcete-li zlepšit teplý čas spuštění, měli byste vždy použít Ngen.exe v aplikaci, protože tím se zabrání cpu náklady na kompilaci JIT kódu aplikace.  
  
 V některých scénářích studené spuštění pomocí Ngen.exe může být také užitečné. Důvodem je, že kompilátor JIT (mscorjit.dll) není třeba načíst.  
  
 S moduly Ngen i JIT může mít nejhorší účinek. Důvodem je, že mscorjit.dll musí být načtena a při kompilátor jit pracuje na váš kód, mnoho stránek v ngen obrazy musí být přístupné při kompilátoru JIT čte metadata sestavení.  
  
### <a name="ngen-and-clickonce"></a>Ngen a ClickOnce  
 Způsob, jakým plánujete nasadit aplikaci, může také změnit dobu načítání. ClickOnce nasazení aplikace nepodporuje Ngen. Pokud se rozhodnete použít ngen.exe pro vaši aplikaci, budete muset použít jiný mechanismus nasazení, jako je například Instalační služba systému Windows.  
  
 Další informace naleznete v [tématu Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Rebasing a DLL adresy kolize  
 Pokud používáte Ngen.exe, uvědomte si, že rebasing může dojít při nativní obrazy jsou načteny do paměti. Pokud dll není načten na jeho upřednostňované základní adresu, protože tento rozsah adres je již přidělena, zavaděč systému Windows načte ji na jinou adresu, která může být časově náročná operace.  
  
 Pomocí nástroje Výpis virtuální chod adresy (Vadump.exe) můžete zkontrolovat, zda existují moduly, ve kterých jsou všechny stránky soukromé. Pokud se jedná o tento případ, modul může být rebased na jinou adresu. Proto jeho stránky nelze sdílet.  
  
 Další informace o nastavení základní adresy naleznete v tématu [Ngen.exe (Native Image Generator).](../../tools/ngen-exe-native-image-generator.md)  
  
## <a name="optimize-authenticode"></a>Optimalizace Authenticode  
 Ověření authenticode přidá k času spuštění. Sestavení podepsaná ověřením podle autentičnosti musí být ověřena certifikačním úřadem .) Toto ověření může být časově náročné, protože může vyžadovat několikrát připojení k síti ke stažení aktuálních seznamů odvolaných certifikátů. Také zajišťuje, že je celý řetězec platných certifikátů na cestě k důvěryhodnému kořenovému adresáři. To může přeložit na několik sekund zpoždění při načítání sestavení.  
  
 Zvažte instalaci certifikátu certifikační autority do klientského počítače nebo se vyhněte použití aplikace Authenticode, pokud je to možné. Pokud víte, že vaše aplikace nepotřebuje důkaz vydavatele, nemusíte platit náklady na ověření podpisu.  
  
 Počínaje rozhraním .NET Framework 3.5 existuje možnost konfigurace, která umožňuje obejít ověření Authenticode. Chcete-li to provést, přidejte do souboru app.exe.config následující nastavení:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>
    </runtime>  
</configuration>  
```  
  
 Další informace naleznete v [ \<tématu generatePublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Porovnat výkon v systému Windows Vista  
 Správce paměti v systému Windows Vista má technologii nazvanou SuperFetch. SuperFetch analyzuje vzory využití paměti v průběhu času k určení optimální ho obsahu paměti pro konkrétního uživatele. Neustále pracuje na udržování tohoto obsahu po celou dobu.  
  
 Tento přístup se liší od techniky předběžného načtení používané v systému Windows XP, která předem načítá data do paměti bez analýzy vzorců využití. V průběhu času, pokud uživatel používá aplikaci WPF často v systému Windows Vista, může se zlepšit doba studeného spuštění aplikace.  
  
## <a name="use-appdomains-efficiently"></a>Efektivní používání domén aplikací  
 Pokud je to možné, načtěte sestavení do oblasti neutrální kód domény a ujistěte se, že nativní image, pokud existuje, se používá ve všech AppDomains vytvořených v aplikaci.  
  
 Pro dosažení nejlepšího výkonu vynucujte efektivní komunikaci mezi doménami snížením volání mezi doménami. Pokud je to možné, použijte volání bez argumentů nebo s argumenty primitivního typu.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Použití atributu NeutralResourcesLanguage  
 Použití <xref:System.Resources.NeutralResourcesLanguageAttribute> k určení neutrální jazykové <xref:System.Resources.ResourceManager>verze pro . Tento přístup zabraňuje neúspěšným vyhledáváním sestavení.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Pro serializaci použijte třídu BinaryFormatter.  
 Pokud je nutné použít serializaci, použijte třídu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> namísto třídy. <xref:System.Xml.Serialization.XmlSerializer> Třída <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> je implementována v knihovně základní třídy (BCL) v sestavení mscorlib.dll. Je <xref:System.Xml.Serialization.XmlSerializer> implementována v sestavení System.Xml.dll, což může být další dll načíst.  
  
 Pokud je nutné <xref:System.Xml.Serialization.XmlSerializer> použít třídu, můžete dosáhnout lepšího výkonu, pokud předgenerujete sestavení serializace.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Konfigurace funkce ClickOnce pro kontrolu aktualizací po spuštění  
 Pokud vaše aplikace používá ClickOnce, vyhněte se přístupu k síti při spuštění konfigurací ClickOnce ke kontrole lokality nasazení pro aktualizace po spuštění aplikace.  
  
 Pokud používáte model aplikace prohlížeče XAML (XBAP), mějte na paměti, že ClickOnce kontroluje lokalitu nasazení pro aktualizace i v případě, že XBAP je již v mezipaměti ClickOnce. Další informace naleznete v [tématu ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Konfigurace automatického spuštění služby PresentationFontCache  
 První wpf aplikace, která se spustí po restartu, je služba PresentationFontCache. Služba ukládá systémová písma do mezipaměti, zlepšuje přístup k písmům a zlepšuje celkový výkon. Spuštění služby je režii a v některých řízených prostředích zvažte konfiguraci služby tak, aby se automaticky spouštěla při restartování systému.  
  
## <a name="set-data-binding-programmatically"></a>Programově nastavit datovou vazbu  
 Namísto použití XAML <xref:System.Windows.FrameworkElement.DataContext%2A> k nastavení deklarativně pro hlavní okno, <xref:System.Windows.Application.OnActivated%2A> zvažte nastavení programově v metodě.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [Přidání úvodní obrazovky do aplikace WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (generátor nativních obrázků)](../../tools/ngen-exe-native-image-generator.md)
- [\<generatePublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
