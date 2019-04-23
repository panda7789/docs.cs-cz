---
title: Částečné zabezpečení důvěryhodnosti WPF
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
ms.openlocfilehash: 75ebf605e9abb844e7a713b448aefe2ec4cd1a27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218378"
---
# <a name="wpf-partial-trust-security"></a>Částečné zabezpečení důvěryhodnosti WPF
<a name="introduction"></a> Obecně platí by měly být omezené Internetové aplikace nebudou mít přímý přístup k důležité systémové prostředky, aby se zabránilo škodlivým poškození. Ve výchozím nastavení [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] a pro přístup k důležité systémové prostředky nemají skriptovací jazyky na straně klienta. Protože aplikace hostované prohlížečem Windows Presentation Foundation (WPF) může být spuštěn z prohlížeče, by měl odpovídat podobnou sadu omezení. Vynutit tato omezení [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] spoléhá na obě [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] a [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (viz [strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)). Ve výchozím nastavení, aplikace hostované prohlížečem požádat o zóně Internet [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] sadu oprávnění, bez ohledu na to, zda jsou spouštěny z Internetu, místní intranet nebo místním počítači. Aplikace, které běží s nic méně než úplnou sadu oprávnění se říká, že běží s částečnou důvěryhodností.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] poskytuje širokou podporu k zajištění, že co nejvíce funkcí co je možné bezpečně v částečném vztahu důvěryhodnosti a společně s [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], poskytuje další podporu pro programování v částečném vztahu důvěryhodnosti.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Podpora funkce částečné důvěryhodnosti WPF](#WPF_Feature_Partial_Trust_Support)  
  
-   [Programování v částečném vztahu důvěryhodnosti](#Partial_Trust_Programming)  
  
-   [Správa oprávnění](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Podpora funkce částečné důvěryhodnosti WPF  
 V následující tabulce jsou uvedeny mezi důležité funkce Windows Presentation Foundation (WPF), které lze bezpečně použít v rámci omezení sady oprávnění zóny Internet.  
  
 Tabulka 1: Funkce WPF, které jsou bezpečné v částečném vztahu důvěryhodnosti  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno prohlížeče<br /><br /> Lokality původu přístupu<br /><br /> IsolatedStorage (omezeno na 512KB)<br /><br /> Vlastnosti UIAutomation zprostředkovatelů<br /><br /> Příkazů<br /><br /> Editory IME<br /><br /> Pero tabletu a inkoustu<br /><br /> Simulované přetažení pomocí myši zachycení a přesunout událostí<br /><br /> OpenFileDialog<br /><br /> Deserializace XAML (prostřednictvím XamlReader.Load)|  
|Integrace Web|Dialogové okno Stažení prohlížeče<br /><br /> Navigace nejvyšší úrovně zahájená uživatelem<br /><br /> mailto:Links<br /><br /> Parametry identifikátoru URI<br /><br /> HTTPWebRequest<br /><br /> Obsah WPF hostované v elementu IFRAME<br /><br /> Hostování stejný web HTML stránek pomocí rámce<br /><br /> Hostování stejné stránek HTML pomocí WebBrowser<br /><br /> Web Services (ASMX)<br /><br /> Webové služby (s použitím Windows Communication Foundation)<br /><br /> Skriptování<br /><br /> Modelu Document Object Model|  
|Vizuály|2D a 3D<br /><br /> Animace<br /><br /> Média (lokalita původu a mezi doménami)<br /><br /> Vytvoření bitové kopie/Audio/Video|  
|Čtení|FlowDocuments<br /><br /> XPS – dokumenty<br /><br /> Vložený & systémových písem<br /><br /> Vývojového diagramu křížového procesu & písma TrueType|  
|Úprava|Kontrola pravopisu<br /><br /> RichTextBox<br /><br /> Ve formátu prostého textu a podpora schránky inkoustu<br /><br /> Vložit uživatelem iniciované<br /><br /> Kopírování vybraný obsah|  
|Ovládací prvky|Obecné ovládacích prvků|  
  
 Tato tabulka popisuje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkce na vysoké úrovni. Podrobnější informace, [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] dokumenty oprávnění, které vyžaduje každý člen [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Kromě toho tyto funkce mít podrobnější informace týkající se provádění částečným vztahem důvěryhodnosti, včetně zvláštní požadavky.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (viz [přehled XAML (WPF)](./advanced/xaml-overview-wpf.md)).  
  
-   Automaticky otevíraná okna (viz <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
-   Přetažení (viz [vyřadit přehled a přetáhněte](./advanced/drag-and-drop-overview.md)).  
  
-   Schránka (viz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
-   Vytvořením bitové kopie (viz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
-   Serializace (viz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
-   Otevřete dialogové okno souboru (viz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 V následující tabulce jsou podrobněji popsány dále [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkce, které nejsou bezpečné pro spuštění v rámci Internetu oprávnění sady zón.  
  
 Tabulka 2: WPF funkce, které jsou v částečném vztahu důvěryhodnosti není bezpečný.  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno (Windows definované aplikací a dialogová okna)<br /><br /> SaveFileDialog<br /><br /> Systém souborů<br /><br /> Přístup k registru<br /><br /> Přetažení<br /><br /> Serializace XAML (přes funkci XamlWriter.Save)<br /><br /> Vlastnosti UIAutomation klientů<br /><br /> Přístup ke zdrojovému kódu okno (HwndHost)<br /><br /> Podpora úplné řeči<br /><br /> Windows Forms Interoperability|  
|Vizuály|Bitmapové efekty<br /><br /> Kódování obrázků|  
|Úprava|Formát schránky formátovaného textu<br /><br /> Plná podpora XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programování v částečném vztahu důvěryhodnosti  
 Pro [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] aplikace, kód, který překračuje výchozí sady oprávnění budou mít různé chování v závislosti na zóně zabezpečení. V některých případech se uživateli zobrazí upozornění při pokusu o jeho instalaci. Uživatel můžete rozhodnout pokračovat nebo zrušit instalaci. Následující tabulka popisuje chování aplikací pro každou zónu zabezpečení a co musíte udělat pro aplikaci pro příjem úplný vztah důvěryhodnosti.  
  
|Zóna zabezpečení|Chování|Získávání úplný vztah důvěryhodnosti|  
|-------------------|--------------|------------------------|  
|Místní počítač|Automatické úplný vztah důvěryhodnosti|Není vyžadována žádná akce.|  
|Intranet a důvěryhodných serverů|Výzva k zadání úplný vztah důvěryhodnosti|Podepište XBAP pomocí certifikátu tak, aby se uživateli zobrazí zdroj v příkazovém řádku.|  
|Internet|Selže a zobrazí se "Důvěryhodnost nebyla udělena"|Podepište XBAP s certifikátem.|  
  
> [!NOTE]
>  Chování popsané v předchozí tabulce je úplný vztah důvěryhodnosti aplikací XBAP, které se neřídí modelu důvěryhodných nasazení ClickOnce.  
  
 Obecně platí je pravděpodobné, že společný kód, který je sdílen mezi samostatnou a aplikace hostované prohlížečem kód, který může být delší než povolená oprávnění. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] a [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] nabízí několik postupů pro správu tohoto scénáře.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Zjištění oprávnění pomocí certifikační Autority  
 V některých případech je možné sdílený kód v sestavení knihovny používané i samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. V těchto případech se může spustit kód funkce, které by mohly vyžadovat více oprávnění než sada obnovený oprávnění aplikace umožňuje. Vaše aplikace může zjistit, jestli má určitá oprávnění s použitím rozhraní Microsoft .NET Framework zabezpečení. Konkrétně můžete otestovat, zda má konkrétní oprávnění voláním <xref:System.Security.CodeAccessPermission.Demand%2A> metodu instance požadované oprávnění. To je ukázáno v následujícím příkladu, který má kód tohoto dotazy na, jestli má možnost uložit soubor na místním disku:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Pokud aplikace nemá požadované oprávnění, volání <xref:System.Security.CodeAccessPermission.Demand%2A> vyvolá výjimku zabezpečení. V opačném případě bylo uděleno oprávnění. `IsPermissionGranted` zapouzdřuje toto chování a vrátí `true` nebo `false` podle potřeby.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Bezproblémové snížení úrovně funkcí  
 Schopnost rozpoznat, zda kód má oprávnění provést to, co potřebuje provést je zajímavé pro kód, který lze spustit z jiné zóny. Při zjišťování, že zóna je jednou z věcí, je mnohem lepší poskytnout alternativu pro uživatele, pokud je to možné. Například úplný vztah důvěryhodnosti aplikace obvykle umožňuje uživatelům vytvářet souborům odkudkoli chtějí, zatímco aplikace s částečnou důvěryhodností lze vytvořit pouze soubory v izolovaném úložišti. Pokud kód k vytvoření souboru existuje v sestavení, které jsou sdíleny úplný vztah důvěryhodnosti (samostatně) aplikace a aplikace s částečnou důvěryhodností (hostované v prohlížeči), a obě aplikace, aby uživatelé mohli k vytvoření souborů, sdílený kód by měl zjistit, zda je spouštění v režimu částečné nebo úplné důvěryhodnosti před vytvořením souboru do příslušného umístění. Následující kód ukazuje obě.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 V mnoha případech byste měli najít alternativu částečným vztahem důvěryhodnosti.  
  
 V kontrolovaném prostředí, jako je například intranet, je možné nainstalovat vlastní spravované rozhraní mezi základní do klienta [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Tyto knihovny může spustit kód, který vyžaduje úplný vztah důvěryhodnosti a na něj odkazovat z aplikace, které jsou povoleny pouze částečným vztahem důvěryhodnosti s použitím <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (Další informace najdete v tématu [zabezpečení](security-wpf.md) a [zabezpečení WPF Strategie – zabezpečení platformy](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Zjišťování hostitele prohlížeče  
 Pomocí [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] ke kontrole oprávnění je technika vhodný, když je potřeba zkontrolovat na základě za oprávnění. I když tato technika závisí na zachycení výjimky v rámci normálního zpracování, které se obecně nedoporučuje a může mít problémy s výkonem. Místo toho pokud vaše [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] spustí jenom v rámci sandboxu zóně Internet, můžete použít <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> vlastnost, která vrací hodnotu true pro [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> pouze rozlišuje, zda je aplikace spuštěna v prohlížeči, ne které sadu oprávnění aplikaci je spuštěn s.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Správa oprávnění  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] běží s částečnou důvěryhodností (sada oprávnění pro zónu Internetu výchozí). V závislosti na požadavcích aplikace, je možné změnit sadu oprávnění z výchozího. Například pokud [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] se spustí z místní intranet, ho můžete využít výhod sady zvýšená oprávnění, která je znázorněna v následující tabulce.  
  
 Tabulka 3: LocalIntranet a Internetová oprávnění  
  
|Oprávnění|Atribut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Servery DNS přístup|Ano|Ne|  
|Proměnné prostředí|Číst|Ano|Ne|  
|Dialogová okna souboru|Otevřít|Ano|Ano|  
|Dialogová okna souboru|Neomezená|Ano|Ne|  
|Izolované úložiště|Sestavení izolace podle uživatele|Ano|Ne|  
|Izolované úložiště|Neznámý izolace|Ano|Ano|  
|Izolované úložiště|Kvóta neomezený počet uživatelů|Ano|Ne|  
|Média|Bezpečné zvuku, videa a obrázků|Ano|Ano|  
|Tisk|Výchozí tisk|Ano|Ne|  
|Tisk|Bezpečné tisk|Ano|Ano|  
|Reflexe|Generování|Ano|Ne|  
|Zabezpečení|Spuštění spravovaného kódu|Ano|Ano|  
|Zabezpečení|Vyhodnocení udělená oprávnění|Ano|Ne|  
|Uživatelské rozhraní|Neomezená|Ano|Ne|  
|Uživatelské rozhraní|Bezpečné na nejvyšší úrovni systému windows|Ano|Ano|  
|Uživatelské rozhraní|Vlastní schránky|Ano|Ano|  
|Webový prohlížeč|Navigace bezpečné rámce do formátu HTML|Ano|Ano|  
  
> [!NOTE]
>  Vyjmout a vložit je povolený jenom v částečném vztahu důvěryhodnosti při, kterou inicioval uživatel.  
  
 Pokud potřebujete ke zvýšení oprávnění, musíte změnit nastavení projektu a ClickOnce – manifest aplikace. Další informace najdete v tématu [přehled aplikací prohlížeče WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md). Následující dokumenty můžou být také užitečné.  
  
-   [Mage.exe (generování manifestu a nástroj pro úpravy)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [Zabezpečování aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Pokud vaše [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] vyžaduje úplný vztah důvěryhodnosti, můžete použít stejné nástroje pro zvýšení požadovaná oprávnění. I když [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] budou dostávat jen úplný vztah důvěryhodnosti, pokud je nainstalovaná na a spustili z místního počítače intranetu nebo z adresy URL, která je uvedena v prohlížeči důvěryhodné nebo povolené lokality. Pokud je aplikace nainstalovaná z intranetu nebo důvěryhodných webů, uživatel dostane standardní ClickOnce řádek informující o zvýšenou úroveň oprávnění. Uživatel můžete rozhodnout pokračovat nebo zrušit instalaci.  
  
 Alternativně můžete použít model nasazení ClickOnce pro důvěryhodného nasazení úplný vztah důvěryhodnosti z jakékoli zóně zabezpečení. Další informace najdete v tématu [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) a [zabezpečení](security-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](security-wpf.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
