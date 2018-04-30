---
title: Částečné zabezpečení důvěryhodnosti WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 023de9e20206411f7dd6774553ae39eefaa508a0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-partial-trust-security"></a>Částečné zabezpečení důvěryhodnosti WPF
<a name="introduction"></a> Obecně platí Internetové aplikace by měla být omezeno mají přímý přístup k důležitým systémovým prostředkům, aby nedošlo k poškození škodlivý. Ve výchozím nastavení [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] a skriptovací jazyky klienta nejsou mít přístup k důležitým systémovým prostředkům. Protože aplikace hostované prohlížečem Windows Presentation Foundation (WPF) může být spuštěn z prohlížeče, by měl odpovídat podobnou sadu omezení. K vynucení těchto omezení [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] spoléhá na obou [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] a [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (najdete v části [strategie zabezpečení WPF - platformy zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Ve výchozím nastavení aplikace hostované prohlížečem žádostí zóně Internet [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] sadu oprávnění, bez ohledu na to, jestli jsou spouštěny z Internetu, místní intranet nebo místního počítače. Aplikace, které používají něco menší než úplnou sadu oprávnění jsou uvedená, aby byl spuštěn s částečnou důvěryhodností.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] poskytuje širokou škálu podporu k zajištění, že tolik funkce co lze bezpečně v částečné důvěryhodnosti a spolu s [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], poskytuje další podporu pro programování částečnou důvěryhodností.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Podpora částečnou důvěryhodností funkce WPF](#WPF_Feature_Partial_Trust_Support)  
  
-   [Programování s částečnou důvěryhodností](#Partial_Trust_Programming)  
  
-   [Správa oprávnění](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Podpora částečnou důvěryhodností funkce WPF  
 Následující tabulka uvádí základní funkce Windows Presentation Foundation (WPF), které jsou bezpečné pro použití v rámci omezení oprávnění sady zón Internetu.  
  
 Tabulka 1: WPF funkce, které jsou bezpečné v částečné důvěryhodnosti  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno prohlížeče<br /><br /> Lokality počátek přístupu<br /><br /> IsolatedStorage (Limit 512KB)<br /><br /> Vlastnosti UIAutomation zprostředkovatelé<br /><br /> Tvorba příkazů<br /><br /> Editory IME<br /><br /> Tablet pera a rukopisu<br /><br /> Simulované přetažením pomocí myši zachycení a přesunout událostí<br /><br /> OpenFileDialog<br /><br /> Deserializace XAML (prostřednictvím XamlReader.Load)|  
|Integrace webové|Dialogové okno Stažení prohlížeče<br /><br /> Navigace nejvyšší úrovně spuštěné uživatelem<br /><br /> mailto:Links<br /><br /> Parametry identifikátoru URI<br /><br /> HTTPWebRequest<br /><br /> Obsah WPF hostované v elementu IFRAME<br /><br /> Hostování stejné lokalitě stránek HTML pomocí rámce<br /><br /> Hostování stejné lokality stránek ve formátu HTML pomocí WebBrowser<br /><br /> Webové služby (ASMX)<br /><br /> Webové služby (s použitím Windows Communication Foundation)<br /><br /> Skriptování<br /><br /> Document Object Model|  
|Vizuální prvky|2D a 3D<br /><br /> Animace<br /><br /> Média (lokalita původu a napříč doménami)<br /><br /> Vytvoření bitové kopie, zvuku a videa|  
|Čtení|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Vložený & systému písem<br /><br /> Vývojového diagramu křížového procesu & písma TrueType|  
|Úpravy|Kontrola pravopisu<br /><br /> RichTextBox<br /><br /> Ve formátu prostého textu a podpora schránky rukopisu<br /><br /> Uživatel spustil vložení<br /><br /> Kopírování vybraný obsah|  
|Ovládací prvky|Obecné ovládací prvky|  
  
 Tato tabulka obsahuje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkce na vysoké úrovni. Podrobnější informace, [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] dokumenty oprávnění, které vyžaduje každý člen v [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Tyto funkce mají více podrobné informace o provádění částečné důvěryhodnosti, včetně zvláštní požadavky.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (viz [přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)).  
  
-   Automaticky otevíraná okna (viz <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
-   Přetažení (viz [přetažení a vyřadit přehled](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)).  
  
-   Schránka (viz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
-   Vytváření bitové kopie (viz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
-   Serializace (viz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
-   Otevřete dialogové okno souborů (viz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 V následující tabulce jsou podrobněji popsány dále [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkce, které nejsou bezpečné pro spuštění v rámci Internetu oprávnění sady zón.  
  
 Tabulka 2: WPF funkce, které není bezpečné v částečné důvěryhodnosti  
  
|Oblast funkcí|Funkce|  
|------------------|-------------|  
|Obecné|Okno (definované Windows aplikace a dialogová okna)<br /><br /> SaveFileDialog<br /><br /> Systém souborů<br /><br /> Přístup k registru<br /><br /> Přetažení<br /><br /> Serializace XAML (prostřednictvím XamlWriter.Save)<br /><br /> Vlastnosti UIAutomation klientů<br /><br /> Přístup ke zdroji okno (HwndHost)<br /><br /> Podpora úplné rozpoznávání řeči<br /><br /> Windows Forms Interoperability|  
|Vizuální prvky|Bitmapové efekty<br /><br /> Kódování bitové kopie|  
|Úpravy|Formát schránky formátovaného textu<br /><br /> Plná podpora XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programování s částečnou důvěryhodností  
 Pro [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] aplikace, kód, který je delší než výchozí sadu oprávnění, bude mít různé chování v závislosti na zóny zabezpečení. V některých případech uživatel dostane upozornění při pokusu o jeho instalaci. Uživatele můžete rozhodnout pokračovat nebo zrušit instalaci. Následující tabulka popisuje chování aplikace pro každou zónu zabezpečení a co musíte udělat pro aplikace na příjem úplný vztah důvěryhodnosti.  
  
|Zóna zabezpečení|Chování|Získávání úplný vztah důvěryhodnosti|  
|-------------------|--------------|------------------------|  
|Místní počítač|Automatické úplný vztah důvěryhodnosti|Není vyžadována žádná akce.|  
|Intranetu a důvěryhodných serverů|Výzva k zadání úplný vztah důvěryhodnosti|Podpis XBAP s certifikátem uživateli se zobrazí zdroj v řádku.|  
|Internet|Nepodaří a dojde k "Vztah důvěryhodnosti není autoritou"|Zaregistrujte XBAP s certifikátem.|  
  
> [!NOTE]
>  Chování popsané v předchozí tabulce je úplný vztah důvěryhodnosti XBAP, které neodpovídají modelu nasazení pomocí technologie ClickOnce důvěryhodné.  
  
 Obecně platí je pravděpodobné, že společný kód, jež jsou sdílena mezi samostatnou a aplikace hostované prohlížečem kód, který může být vyšší než povolené oprávnění. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] a [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] nabízí několik postupů pro správu tento scénář.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Zjišťování oprávnění pomocí certifikační Autority  
 V některých případech je možné pro sdílené kód v sestavení knihovny má být používána i samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. V těchto případech může spustit kód funkce, které by mohlo vyžadovat další oprávnění, než umožňuje sadě zadávané oprávnění aplikace. Aplikace může zjistit, zda má určitá oprávnění pomocí rozhraní Microsoft .NET Framework zabezpečení. Konkrétně můžete zkontrolovat, zda má konkrétní oprávnění voláním <xref:System.Security.CodeAccessPermission.Demand%2A> metody u instance požadované oprávnění. To je ukázáno v následujícím příkladu, který má kód této dotazy na tom, jestli má možnost uložení souboru na místní disk:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Pokud aplikace nemá požadované oprávnění, volání <xref:System.Security.CodeAccessPermission.Demand%2A> vyvolá výjimku výjimka zabezpečení. Jinak má uděleno oprávnění. `IsPermissionGranted` zapouzdří toto chování a vrátí `true` nebo `false` podle potřeby.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Řádné snížení výkonu funkce  
 Bude možné zjistit, zda kód má oprávnění k provedení, co je třeba provést je zajímavé pro kód, který lze spustit z jiné zóny. Při zjišťování zóny je jednou z věcí, je mnohem lepší zajistit alternativu pro uživatele, pokud je to možné. Například úplný vztah důvěryhodnosti aplikace obvykle umožňuje uživatelům vytvářet souborům odkudkoli chtějí, zatímco aplikace s částečnou důvěryhodností lze vytvořit pouze soubory v izolovaném úložišti. Pokud kód k vytvoření souboru existuje v sestavení, které sdílí úplný vztah důvěryhodnosti (samostatně) aplikace a aplikace s částečnou důvěryhodností (hostované prohlížečem) a obě aplikace, aby uživatelé mohli vytvářet soubory, kód sdílený by měl zjistit, jestli ho má spouštění v úplné nebo částečné důvěryhodnosti před vytvořením soubor do příslušného umístění. Následující kód ukazuje, jak.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 V mnoha případech by měl být nemůže najít alternativní částečnou důvěryhodností.  
  
 V řízeném prostředí, jako je například intranet, může být nainstalována vlastní spravované rozhraní mezi základní do klienta [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Tyto knihovny může spustit kód, který vyžaduje úplný vztah důvěryhodnosti a na něj odkazovat z aplikací, které jsou povoleny pouze částečné důvěryhodnosti pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (Další informace najdete v tématu [zabezpečení](../../../docs/framework/wpf/security-wpf.md) a [zabezpečení WPF Strategie - platformy zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Zjišťování hostitele prohlížeče  
 Pomocí [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] zkontrolujte oprávnění je vhodné technika, když je potřeba zkontrolovat na základě za oprávnění. I když tato technika závisí na zachycení výjimky jako součást normální zpracování, které se obecně nedoporučuje a může mít problémy s výkonem. Místo toho pokud vaše [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] pouze běží v rámci izolovaného prostoru zóně Internet, můžete použít <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> vlastnost, která vrátí hodnotu true pro [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> pouze rozlišuje, zda je aplikace spuštěna v prohlížeči není které sadu oprávnění aplikaci je spuštěn s.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Správa oprávnění  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] spustit s částečnou důvěryhodností (sadu oprávnění pro zónu Internetu výchozí). V závislosti na požadavcích aplikace, je však možné změnit z výchozí sadu oprávnění. Například pokud [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] se spouští z místního intranetu, ho můžete využít výhod sadu zvýšená oprávnění, které je uvedené v následující tabulce.  
  
 Tabulka 3: LocalIntranet a Internetu oprávnění  
  
|Oprávnění|Atribut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Servery DNS přístup|Ano|Ne|  
|Proměnné prostředí|Číst|Ano|Ne|  
|Dialogová okna souboru|Otevřít|Ano|Ano|  
|Dialogová okna souboru|Bez omezení|Ano|Ne|  
|Izolované úložiště|Sestavení izolace uživatelem|Ano|Ne|  
|Izolované úložiště|Neznámý izolace|Ano|Ano|  
|Izolované úložiště|Kvóta neomezený počet uživatelů|Ano|Ne|  
|Média|Bezpečné zvuk, video a obrázků|Ano|Ano|  
|Tisk|Výchozí tisk|Ano|Ne|  
|Tisk|Bezpečné tisk|Ano|Ano|  
|Reflexe|Emitování|Ano|Ne|  
|Zabezpečení|Provádění spravovaného kódu|Ano|Ano|  
|Zabezpečení|Assert – udělená oprávnění|Ano|Ne|  
|Uživatelské rozhraní|Bez omezení|Ano|Ne|  
|Uživatelské rozhraní|Bezpečné nejvyšší úrovně windows|Ano|Ano|  
|Uživatelské rozhraní|Vlastní schránky|Ano|Ano|  
|Webový prohlížeč|Navigace bezpečné rámce do formátu HTML|Ano|Ano|  
  
> [!NOTE]
>  Vyjímání a vkládání je povolené jenom v částečné důvěryhodnosti při uživatel spustil.  
  
 Pokud je potřeba zvýšit oprávnění, budete muset změnit nastavení projektu a manifest aplikace ClickOnce. Další informace najdete v tématu [přehled aplikace prohlížeče XAML WPF](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md). V následujících dokumentech může být taky užitečné.  
  
-   [Mage.exe (generování manifestu a nástroj pro úpravy)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [Zabezpečování aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Pokud vaše [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] vyžaduje úplný vztah důvěryhodnosti, můžete použít stejné nástroje ke zvýšení požadovaná oprávnění. I když [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] bude přijímat pouze úplný vztah důvěryhodnosti, pokud je nainstalován na a spustit z místního počítače, intranetu, nebo z adresy URL, která je uvedena v prohlížeče za důvěryhodné nebo povolené weby. Pokud je aplikace nainstalována z intranetu nebo důvěryhodných lokalit, uživatel dostane řádku standardní ClickOnce upozorněním zvýšenými oprávněními. Uživatele můžete rozhodnout pokračovat nebo zrušit instalaci.  
  
 Alternativně můžete použít model nasazení důvěryhodných ClickOnce pro nasazení úplný vztah důvěryhodnosti z jakékoli zóny zabezpečení. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview) a [zabezpečení](../../../docs/framework/wpf/security-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../docs/framework/wpf/security-wpf.md)  
 [Strategie zabezpečení WPF – zabezpečení platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Strategie zabezpečení WPF – engineering zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
