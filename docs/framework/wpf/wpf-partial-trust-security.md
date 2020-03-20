---
title: Částečné zabezpečení důvěryhodnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 99c7d9cfae2b137053ca77d9e3d7055b4674ce5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174573"
---
# <a name="wpf-partial-trust-security"></a>Částečné zabezpečení důvěryhodnosti WPF
<a name="introduction"></a>Obecně platí, že internetové aplikace by měly být omezeny v přímém přístupu ke kritickým systémovým prostředkům, aby se zabránilo škodlivému poškození. Ve výchozím nastavení nemají jazyky skriptování HTML a na straně klienta přístup ke kritickým systémovým prostředkům. Vzhledem k tomu, že aplikace hostované prohlížečem Windows Presentation Foundation (WPF) lze spustit z prohlížeče, měly by splňovat podobnou sadu omezení. Chcete-li vynutit tato omezení, WPF spoléhá na zabezpečení přístupu ke kódu (CAS) a ClickOnce (viz [WPF bezpečnostní strategie - zabezpečení platformy).](wpf-security-strategy-platform-security.md) Ve výchozím nastavení požadují aplikace hostované prohlížečem sadu oprávnění CAS v zóně Internet bez ohledu na to, zda jsou spuštěna z Internetu, místnísítě intranet nebo místního počítače. Aplikace, které běží s méně než úplnou sadu oprávnění jsou prý spuštěny s částečným vztahem důvěryhodnosti.  
  
 WPF poskytuje širokou škálu podpory, která zajišťuje, že co nejvíce funkcí lze bezpečně používat v částečném vztahu důvěryhodnosti a spolu s CAS poskytuje další podporu pro částečné programování důvěryhodnosti.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Podpora částečnédůvěryhodnosti funkce WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Částečné programování důvěryhodnosti](#Partial_Trust_Programming)  
  
- [Správa oprávnění](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>
## <a name="wpf-feature-partial-trust-support"></a>Podpora částečnédůvěryhodnosti funkce WPF  
 V následující tabulce jsou uvedeny funkce wpf (high-level level" systému Windows Presentation Foundation, které jsou bezpečné pro použití v rámci limitů sady oprávnění zóny Internet.  
  
 Tabulka 1: WPF funkce, které jsou bezpečné v částečné moru důvěryhodnosti  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno prohlížeče<br /><br /> Místo původu Přístup<br /><br /> Izolované úložiště (limit 512 KB)<br /><br /> Poskytovatelé uživatelské ho automatizační hospo-<br /><br /> Velící<br /><br /> Editory IME<br /><br /> Stylus tabletu a inkoust<br /><br /> Simulované přetažení pomocí událostí zachycení a přesunutí myši<br /><br /> Openfiledialog<br /><br /> Deserializace XAML (přes XamlReader.Load)|  
|Webová integrace|Dialogové okno Ke stažení prohlížeče<br /><br /> Navigace iniciovná uživatelem nejvyšší úrovně<br /><br /> mailto:odkazy<br /><br /> Parametry identifikátoru jednotného prostředku<br /><br /> HTTPWebRequest<br /><br /> WPF obsah hostovaný v prvku IFRAME<br /><br /> Hostování stránek HTML se stejným webem pomocí rámce<br /><br /> Hostování stejných stránek HTML stránek pomocí webového prohlížeče<br /><br /> Webové služby (ASMX)<br /><br /> Webové služby (pomocí windows communication foundation)<br /><br /> Skriptování<br /><br /> Objektový model dokumentu|  
|Vizuály|2D a 3D<br /><br /> Animace<br /><br /> Média (místo původu a mezidoména)<br /><br /> Zobrazování/Zvuk/Video|  
|Čtení|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Vložená & systémová písma<br /><br /> Písma CFF & TrueType|  
|Úprava|Kontrolu pravopisu<br /><br /> RichTextBox<br /><br /> Podpora schránky prostého textu a inkoustu<br /><br /> Vložení iniciované uživatelem<br /><br /> Kopírování vybraného obsahu|  
|Ovládací prvky|Obecné ovládací prvky|  
  
 Tato tabulka popisuje funkce WPF na vysoké úrovni. Podrobnější informace sada Windows SDK dokumentuje oprávnění, která jsou vyžadována jednotlivými členy wpf. Následující funkce mají navíc podrobnější informace týkající se částečného spuštění důvěryhodnosti, včetně zvláštních důvodů.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](viz [Přehled XAML (WPF).](../../desktop-wpf/fundamentals/xaml.md)  
  
- Vyskakovací okno (viz). <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>  
  
- Přetažení (viz [Přehled přetažení).](./advanced/drag-and-drop-overview.md)  
  
- Schránka (viz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
- Zobrazování (viz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serializace <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>(viz <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>, ).  
  
- Otevřít dialogové okno <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>Soubor (viz ).  
  
 Následující tabulka popisuje funkce WPF, které nejsou bezpečné pro spuštění v rámci nastavení oprávnění zóny Internet.  
  
 Tabulka 2: WPF funkce, které nejsou bezpečné v částečném vztahu důvěryhodnosti  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno (okna definovaná aplikací a dialogová okna)<br /><br /> Savefiledialog<br /><br /> Systém souborů<br /><br /> Přístup k registru<br /><br /> Přetažení<br /><br /> Serializace XAML (pomocí xamlwriter.save)<br /><br /> Klienti UIAutomation<br /><br /> Přístup ke zdrojovému oknu (HwndHost)<br /><br /> Plná podpora řeči<br /><br /> Interoperabilita formulářů systému Windows|  
|Vizuály|Bitmapové efekty<br /><br /> Kódování obrazu|  
|Úprava|Schránka formátu RTF<br /><br /> Podpora úplného XAML|  
  
<a name="Partial_Trust_Programming"></a>
## <a name="partial-trust-programming"></a>Částečné programování důvěryhodnosti  
 U aplikací XBAP bude mít kód, který překračuje výchozí sadu oprávnění, odlišné chování v závislosti na zóně zabezpečení. V některých případech se uživateli zobrazí upozornění při pokusu o jeho instalaci. Uživatel se může rozhodnout pokračovat v instalaci nebo ji zrušit. Následující tabulka popisuje chování aplikace pro každou zónu zabezpečení a co musíte udělat, aby aplikace získala plnou důvěryhodnost.  
  
|Zóna zabezpečení|Chování|Získání plné důvěry|  
|-------------------|--------------|------------------------|  
|Místní počítač|Automatická plná důvěryhodnost|Není nutná žádná akce.|  
|Intranet a důvěryhodné servery|Výzva k úplnému vztahu důvěryhodnosti|Podepište XBAP certifikátem tak, aby uživatel viděl zdroj v výzvě.|  
|Internet|Selže s "Důvěra není udělena"|Podepište XBAP certifikátem.|  
  
> [!NOTE]
> Chování popsané v předchozí tabulce je pro úplné důvěryhodnosti XBAPs, které nenásledují ClickOnce Trusted Deployment modelu.  
  
 Obecně platí, že kód, který může překročit povolená oprávnění, je pravděpodobně společný kód, který je sdílen mezi samostatnými aplikacemi a aplikacemi hostovanými v prohlížeči. CAS a WPF nabízejí několik technik pro správu tohoto scénáře.  
  
<a name="Detecting_Permissions_using_CAS"></a>
### <a name="detecting-permissions-using-cas"></a>Zjišťování oprávnění pomocí casu  
 V některých situacích je možné pro sdílený kód v sestaveníknihovny, které mají být použity jak samostatné aplikace a XBAPs. V těchto případech může kód spustit funkce, které mohou vyžadovat více oprávnění, než umožňuje sada udělených oprávnění aplikace. Aplikace může zjistit, zda má určitá oprávnění pomocí zabezpečení Microsoft .NET Framework. Konkrétně může otestovat, zda má konkrétní <xref:System.Security.CodeAccessPermission.Demand%2A> oprávnění voláním metody na instanci požadované oprávnění. To je znázorněno v následujícím příkladu, který má kód, který se dotazuje, zda má možnost uložit soubor na místní disk:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Pokud aplikace nemá požadovaná oprávnění, volání <xref:System.Security.CodeAccessPermission.Demand%2A> vyvolá výjimku zabezpečení. V opačném případě bylo uděleno oprávnění. `IsPermissionGranted`zapouzdřuje toto chování a vrátí `true` nebo `false` podle potřeby.  
  
<a name="Graceful_Degradation_of_Functionality"></a>
### <a name="graceful-degradation-of-functionality"></a>Elegantní degradace funkčnosti  
 Být schopen zjistit, zda kód má oprávnění k tomu, co je třeba udělat, je zajímavé pro kód, který lze spustit z různých zón. Zatímco detekce zóny je jedna věc, je mnohem lepší poskytnout alternativu pro uživatele, pokud je to možné. Například aplikace s úplnou důvěryhodností obvykle umožňuje uživatelům vytvářet soubory kdekoli chtějí, zatímco aplikace s částečnou důvěryhodností může vytvářet soubory pouze v izolovaném úložišti. Pokud kód pro vytvoření souboru existuje v sestavení, které je sdíleno aplikacemi s úplným vztahem důvěryhodnosti (samostatné) a aplikacemi s částečnou důvěryhodností (hostované v prohlížeči) a obě aplikace chtějí, aby uživatelé mohli vytvářet soubory, měl by sdílený kód zjistit, zda je spuštění v částečné nebo úplné důvěryhodnosti před vytvořením souboru v příslušném umístění. Následující kód ukazuje oba.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 V mnoha případech byste měli být schopni najít alternativu částečnédůvěryhodnosti.  
  
 V řízeném prostředí, jako je například intranet, vlastní spravované architektury lze nainstalovat přes klientskou základnu do globální mezipaměti sestavení (GAC). Tyto knihovny lze spustit kód, který vyžaduje úplný vztah důvěryhodnosti, a <xref:System.Security.AllowPartiallyTrustedCallersAttribute> odkazovat z aplikací, které jsou povoleny pouze částečný vztah důvěryhodnosti pomocí (další informace naleznete v [tématu zabezpečení](security-wpf.md) a [WPF bezpečnostní strategie - zabezpečení platformy](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>
### <a name="browser-host-detection"></a>Detekce hostitele prohlížeče  
 Použití CAS ke kontrole oprávnění je vhodná technika, když potřebujete zkontrolovat na základě oprávnění. Ačkoli tato technika závisí na zachycení výjimky jako součást normální zpracování, což se nedoporučuje obecně a může mít problémy s výkonem. Místo toho, pokud vaše aplikace prohlížeče XAML (XBAP) běží pouze v <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> izolovaném prostoru zóny Internet, můžete použít vlastnost, která vrátí true pro aplikace prohlížeče XAML (XBAPs).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>pouze rozlišuje, zda je aplikace spuštěna v prohlížeči, nikoli jakou sadu oprávnění aplikace používá.  
  
<a name="Managing_Permissions"></a>
## <a name="managing-permissions"></a>Správa oprávnění  
 Ve výchozím nastavení běží XBAPs s částečným vztahem důvěryhodnosti (výchozí sada oprávnění zóny Internet). V závislosti na požadavcích aplikace je však možné změnit sadu oprávnění z výchozího nastavení. Například pokud XBAPs je spuštěn z místního intranetu, může využít sadu oprávnění zvýšené, která je uvedena v následující tabulce.  
  
 Tabulka 3: Oprávnění sítě LocalIntranet a Internet  
  
|Oprávnění|Atribut|Localintranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Přístup k serverům DNS|Ano|Ne|  
|Proměnné prostředí|Čtení|Ano|Ne|  
|Dialogy souborů|Otevřít|Ano|Ano|  
|Dialogy souborů|Neomezené|Ano|Ne|  
|Izolované úložiště|Izolace sestavení podle uživatele|Ano|Ne|  
|Izolované úložiště|Neznámá izolace|Ano|Ano|  
|Izolované úložiště|Neomezená uživatelská kvóta|Ano|Ne|  
|Média|Bezpečný zvuk, video a obrázky|Ano|Ano|  
|Tisk|Výchozí tisk|Ano|Ne|  
|Tisk|Bezpečný tisk|Ano|Ano|  
|Reflexe|Vydávat|Ano|Ne|  
|Zabezpečení|Spuštění spravovaného kódu|Ano|Ano|  
|Zabezpečení|Uplatnit udělená oprávnění|Ano|Ne|  
|Uživatelské rozhraní|Neomezené|Ano|Ne|  
|Uživatelské rozhraní|Bezpečná okna nejvyšší úrovně|Ano|Ano|  
|Uživatelské rozhraní|Vlastní schránka|Ano|Ano|  
|Webový prohlížeč|Bezpečná navigace s rámcem do HTML|Ano|Ano|  
  
> [!NOTE]
> Vyjmout a vložit je povoleno pouze v částečném vztahu důvěryhodnosti, když je uživatel iniciován.  
  
 Pokud potřebujete zvýšit oprávnění, je třeba změnit nastavení projektu a manifest aplikace ClickOnce. Další informace naleznete v tématu [Přehled prohlížečů WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md). Následující dokumenty mohou být také užitečné.  
  
- [Mage.exe (Nástroj pro generování a úpravy manifestu).](../tools/mage-exe-manifest-generation-and-editing-tool.md)  
  
- [MageUI.exe (Nástroj pro generování a úpravy manifestu, grafický klient)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Zabezpečení clickonce aplikací](/visualstudio/deployment/securing-clickonce-applications).  
  
 Pokud váš XBAP vyžaduje plnou důvěryhodnost, můžete použít stejné nástroje ke zvýšení požadovaných oprávnění. I když xbap obdrží plnou důvěryhodnost pouze v případě, že je nainstalován a spuštěn z místního počítače, intranetu nebo z adresy URL, která je uvedena v důvěryhodných nebo povolených webech prohlížeče. Pokud je aplikace nainstalována z intranetu nebo důvěryhodného webu, uživatel obdrží standardní výzvu ClickOnce s upozorněním na zvýšená oprávnění. Uživatel se může rozhodnout pokračovat v instalaci nebo ji zrušit.  
  
 Alternativně můžete použít model clickonce důvěryhodného nasazení pro úplné nasazení důvěryhodnosti z libovolné zóny zabezpečení. Další informace naleznete v tématu Přehled a [zabezpečení](security-wpf.md) [nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview) .  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení](security-wpf.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
