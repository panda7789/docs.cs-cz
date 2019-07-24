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
ms.openlocfilehash: 259db84c8ab3b9bbad809b9636ba18537dd6fe62
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400733"
---
# <a name="wpf-partial-trust-security"></a>Částečné zabezpečení důvěryhodnosti WPF
<a name="introduction"></a>Obecně platí, že internetové aplikace by měly mít přímý přístup k důležitým systémovým prostředkům, aby se zabránilo škodlivým škodám. Ve výchozím nastavení [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] a skriptovací jazyky na straně klienta nemají přístup k důležitým systémovým prostředkům. Vzhledem k tomu, že aplikace hostované v prohlížeči Windows Presentation Foundation (WPF) mohou být spouštěny z prohlížeče, měly by odpovídat podobné sadě omezení. K vykonání těchto [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] omezení spoléhá na zabezpečení přístupu kódu (CAS) i ClickOnce (viz téma [strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)). Ve výchozím nastavení aplikace hostované v prohlížeči požadují sadu oprávnění CAS Internet Zone, bez ohledu na to, jestli se spouští z Internetu, místního intranetu nebo místního počítače. U aplikací, které běží s méně než úplnými oprávněními, se říká, že mají běžet s částečným vztahem důvěryhodnosti.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]poskytuje širokou škálu podpory, aby bylo zajištěno, že je možné v částečném vztahu důvěryhodnosti a společně s certifikačními autoritami používat co nejvíc funkcí, a navíc poskytuje další podporu pro programování s částečným vztahem důvěryhodnosti.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Podpora částečné důvěryhodnosti funkcí WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programování s částečným vztahem důvěryhodnosti](#Partial_Trust_Programming)  
  
- [Správa oprávnění](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Podpora částečné důvěryhodnosti funkcí WPF  
 V následující tabulce jsou uvedeny nejdůležitější funkce Windows Presentation Foundation (WPF), které se bezpečně používají v rámci omezení sady oprávnění zóny Internet.  
  
 Tabulka 1: Funkce WPF, které jsou v částečném vztahu důvěryhodnosti bezpečné  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno prohlížeče<br /><br /> Přístup k webu původu<br /><br /> IsolatedStorage (512 kB limit)<br /><br /> UIAutomation poskytovatelé<br /><br /> Příkazů<br /><br /> Editory IME<br /><br /> Tablet stylus a rukopis<br /><br /> Simulované přetahování pomocí myši při zachycení a přesunutí událostí<br /><br /> OpenFileDialog<br /><br /> Deserializace XAML (přes XamlReader. Load)|  
|Integrace webu|Dialogové okno pro stažení prohlížeče<br /><br /> Navigace iniciovaná uživatelem na nejvyšší úrovni<br /><br /> mailto: odkazy<br /><br /> Parametry identifikátoru Uniform prostředků<br /><br /> HTTPWebRequest<br /><br /> Obsah WPF hostovaný v prvku IFRAME<br /><br /> Hostování stránek HTML stejné lokality pomocí rámce<br /><br /> Hostování stejných stránek HTML webu pomocí ovládacího prvku WebBrowser<br /><br /> Webové služby (ASMX)<br /><br /> Webové služby (pomocí Windows Communication Foundation)<br /><br /> Skriptování<br /><br /> model DOM (Document Object Model)|  
|Vizuály|2D a 3D<br /><br /> Animace<br /><br /> Médium (lokalita původu a mezi doménami)<br /><br /> Imaging/audio/video|  
|Čtení|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Vložená & systémová písma<br /><br /> CFF & písma TrueType|  
|Úprava|Kontrola pravopisu<br /><br /> RichTextBox<br /><br /> Podpora schránky ve formátu prostého textu a rukopisu<br /><br /> Vložení iniciované uživatelem<br /><br /> Kopírování vybraného obsahu|  
|Ovládací prvky|Obecné ovládací prvky|  
  
 Tato tabulka obsahuje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkce na nejvyšší úrovni. Podrobnější informace najdete [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] v dokumentu oprávnění, která jsou vyžadována každým členem v [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Kromě toho následující funkce obsahují podrobnější informace týkající se provádění částečné důvěryhodnosti, včetně zvláštních otázek.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](viz [XAML Overview (WPF)](./advanced/xaml-overview-wpf.md)).  
  
- Automaticky otevíraná okna ( <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>viz).  
  
- Přetažení (viz [Přehled](./advanced/drag-and-drop-overview.md)přetažení).  
  
- Schránka ( <xref:System.Windows.Clipboard?displayProperty=nameWithType>viz).  
  
- Imaging (viz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serializace ( <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>viz <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>,).  
  
- Dialogové okno otevřít soubor (viz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 V následující tabulce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jsou uvedené funkce, které není bezpečné spouštět v rámci omezení sady oprávnění zóny Internetu.  
  
 Tabulka 2: Funkce WPF, které nejsou bezpečné v částečném vztahu důvěryhodnosti  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno (okna definovaná aplikací a dialogová okna)<br /><br /> SaveFileDialog<br /><br /> Systém souborů<br /><br /> Přístup k registru<br /><br /> Přetažení<br /><br /> Serializace XAML (přes XamlWriter. Save)<br /><br /> UIAutomation klienti<br /><br /> Přístup ke zdrojovému oknu (HwndHost)<br /><br /> Plná podpora řeči<br /><br /> Spolupráce model Windows Forms|  
|Vizuály|Bitmapové efekty<br /><br /> Kódování obrázku|  
|Úprava|Schránka formátu RTF (Rich Text Format)<br /><br /> Plná podpora jazyka XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programování s částečným vztahem důvěryhodnosti  
 V [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] případě aplikací má kód, který překračuje výchozí sadu oprávnění, jiné chování v závislosti na zóně zabezpečení. V některých případech se uživateli při pokusu o instalaci zobrazí upozornění. Uživatel může zvolit pokračování nebo instalaci zrušit. Následující tabulka popisuje chování aplikace pro každou zónu zabezpečení a to, co je třeba udělat, aby aplikace přijímala úplný vztah důvěryhodnosti.  
  
|Zóna zabezpečení|Chování|Získání úplné důvěryhodnosti|  
|-------------------|--------------|------------------------|  
|Místní počítač|Automatický úplný vztah důvěryhodnosti|Není nutné provádět žádnou akci.|  
|Intranetové a důvěryhodné weby|Dotázat se na úplný vztah důvěryhodnosti|Přihlaste se k aplikaci XBAP pomocí certifikátu, aby se uživateli zobrazila výzva ke zdroji v příkazovém řádku.|  
|Internet|Neúspěch s "důvěryhodným neuděleným"|Podepište aplikaci XBAP pomocí certifikátu.|  
  
> [!NOTE]
>  Chování popsané v předchozí tabulce je pro úplný vztah důvěryhodnosti aplikace XBAP, který nedodržuje model důvěryhodného nasazení ClickOnce.  
  
 Obecně platí, že kód, který může překročit povolená oprávnění, bude pravděpodobně běžný kód, který je sdílen mezi samostatnou aplikací a aplikacemi hostovanými v prohlížeči. CAS a [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] nabízí několik postupů pro správu tohoto scénáře.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Zjišťování oprávnění pomocí certifikačních autorit  
 V některých situacích je možné, aby sdílený kód v sestavení knihovny používaly obě samostatné aplikace i [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. V těchto případech může kód provádět funkce, které by mohly vyžadovat více oprávnění, než povoluje sada oprávnění udělená aplikaci. Vaše aplikace může určit, jestli má určité oprávnění, pomocí Microsoft .NET Framework Security. Konkrétně může otestovat, zda má konkrétní oprávnění voláním <xref:System.Security.CodeAccessPermission.Demand%2A> metody na instanci požadovaného oprávnění. To je znázorněno v následujícím příkladu, který obsahuje kód, který se dotazuje na to, jestli má možnost Uložit soubor na místní disk:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Pokud aplikace nemá požadované oprávnění, volání metody <xref:System.Security.CodeAccessPermission.Demand%2A> vyvolá výjimku zabezpečení. V opačném případě bylo uděleno oprávnění. `IsPermissionGranted`Zapouzdřuje toto chování a `true` vrátí `false` nebo podle potřeby vrátí.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Řádné snížení funkčnosti  
 Schopnost zjistit, jestli kód má oprávnění k tomu, aby měl, co je potřeba udělat, je zajímavou pro kód, který se dá spustit z různých zón. Při zjišťování zóny je jedna věc mnohem lepší pro uživatele, pokud je to možné, nabídnout alternativu. Například plná důvěryhodná aplikace obvykle umožňuje uživatelům vytvářet soubory kdekoli, zatímco aplikace s částečnou důvěryhodností může vytvářet pouze soubory v izolovaném úložišti. Pokud kód pro vytvoření souboru existuje v sestavení, které je sdíleno jak v aplikacích s částečným vztahem důvěryhodnosti (samostatné), tak s částečnou důvěryhodností (v prohlížeči), a obě aplikace chtějí, aby uživatelé mohli vytvářet soubory, sdílený kód by měl zjistit, zda je spuštění v částečném nebo úplném vztahu důvěryhodnosti před vytvořením souboru v příslušném umístění. Následující kód ukazuje obojí.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 V mnoha případech byste měli být schopni najít alternativu s částečným vztahem důvěryhodnosti.  
  
 V kontrolovaném prostředí, jako je intranet, se vlastní spravovaná rozhraní dají instalovat v rámci klientské základny do [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Tyto knihovny mohou spouštět kód, který vyžaduje úplný vztah důvěryhodnosti a na základě aplikací, které jsou povoleny pouze s částečným <xref:System.Security.AllowPartiallyTrustedCallersAttribute> vztahem důvěryhodnosti (Další informace naleznete [v tématu Security](security-wpf.md) and [WPF Security strategie-Platform Security](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Detekce hostitele v prohlížeči  
 Použití CAS ke kontrole oprávnění je vhodná technika, pokud potřebujete kontrolovat jednotlivá oprávnění. I když tato technika závisí na zachycení výjimek jako součásti normálního zpracování, což se obecně nedoporučuje a může mít problémy s výkonem. Místo toho, pokud [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] vaše aplikace běží v karanténě zóny Internet Zone, můžete <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> použít vlastnost, která vrací hodnotu true pro [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>rozlišuje pouze to, jestli aplikace běží v prohlížeči, a ne na které sadě oprávnění aplikace běží.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Správa oprávnění  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] běží s částečnou důvěryhodností (výchozí sada oprávnění zóny Internet). V závislosti na požadavcích aplikace je však možné změnit sadu oprávnění z výchozí hodnoty. Například pokud [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] se spustí z místního intranetu, může využít vyšší sadu oprávnění, která je uvedená v následující tabulce.  
  
 Tabulka 3: LocalIntranet a Internetová oprávnění  
  
|Oprávnění|Atribut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Přístup k serverům DNS|Ano|Ne|  
|Proměnné prostředí|Číst|Ano|Ne|  
|Dialogy souborů|Otevřít|Ano|Ano|  
|Dialogy souborů|Neomezený|Ano|Ne|  
|Izolované úložiště|Izolace sestavení podle uživatele|Ano|Ne|  
|Izolované úložiště|Neznámá izolace|Ano|Ano|  
|Izolované úložiště|Neomezená kvóta uživatelů|Ano|Ne|  
|Média|Bezpečný zvuk, video a obrázky|Ano|Ano|  
|Tisk|Výchozí tisk|Ano|Ne|  
|Tisk|Bezpečný tisk|Ano|Ano|  
|Reflexe|Obor|Ano|Ne|  
|Zabezpečení|Spuštění spravovaného kódu|Ano|Ano|  
|Zabezpečení|Vyhodnocení udělených oprávnění|Ano|Ne|  
|Uživatelské rozhraní|Neomezený|Ano|Ne|  
|Uživatelské rozhraní|Bezpečná okna nejvyšší úrovně|Ano|Ano|  
|Uživatelské rozhraní|Vlastní schránka|Ano|Ano|  
|Webový prohlížeč|Bezpečná navigace mezi snímky a HTML|Ano|Ano|  
  
> [!NOTE]
>  Operace vyjmutí a vložení je povolena pouze při částečném vztahu důvěryhodnosti při zahájení uživatelem.  
  
 Potřebujete-li zvýšit oprávnění, je třeba změnit nastavení projektu a manifest aplikace ClickOnce. Další informace naleznete v tématu [Přehled aplikací prohlížeče WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md). Následující dokumenty mohou být užitečné také v následujících dokumentech.  
  
- [Mage. exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI. exe (Manifest Generation and Editing Tool, grafický klient)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Zabezpečování aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] Pokud vyžadujete úplný vztah důvěryhodnosti, můžete ke zvýšení požadovaných oprávnění použít stejné nástroje. I když [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] bude k instalaci a spuštění z místního počítače, intranetu nebo z adresy URL, která je uvedena v seznamu důvěryhodných nebo povolených lokalit prohlížeče, obdrží jenom úplný vztah důvěryhodnosti. Pokud je aplikace nainstalována z intranetu nebo z důvěryhodného webu, bude uživatel dostávat standardní výzvu ClickOnce s upozorněním na oprávnění vyšší úrovně. Uživatel může zvolit pokračování nebo instalaci zrušit.  
  
 Alternativně můžete použít model důvěryhodných nasazení ClickOnce pro nasazení s úplným vztahem důvěryhodnosti z jakékoli zóny zabezpečení. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview) a [zabezpečení](security-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](security-wpf.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
