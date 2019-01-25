---
title: Dokumenty v platformě WPF
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: 00e983c907c0376b45d2342f393569d045cbf98b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517731"
---
# <a name="documents-in-wpf"></a>Dokumenty v platformě WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nabízí širokou škálu funkce dokumentu, které umožňují vytvářet a věrného obsah, který je navržena jako snadno používaná a čtení než v předchozích generací [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Kromě poznat široké možnosti a kvality [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje integrované služby pro zobrazení dokumentu, balení a zabezpečení. Toto téma obsahuje úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typů dokumentů a balení dokumentů.  
  
  
<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokumenty rozdělí do dvou rozsáhlých kategorií podle zamýšleného použití; Tyto kategorie dokumentu jsou označovány jako "oprava dokumentů" a "dokumenty toku."  
  
 Oprava dokumentů jsou určené pro aplikace, které vyžadují přesné [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] prezentace, nezávisle na zobrazení nebo tiskárny hardware používá. Obvyklá využití pro pevné dokumenty zahrnují DTP, zpracování textu a rozložení formuláře, ve kterém je velmi důležité dodržování původní návrh stránek. Jako součást její rozložení pevné dokumentu udržuje přesné poziční umístění obsahu prvků nezávislé zobrazení nebo tisk zařízení používá. Například stránku pevné dokument zobrazit v zobrazení 96 dpi zobrazí přesně stejné je výstup laserová tiskárna 600 rozlišení dpi jako když se výstup phototypesetter 4800 dpi. Rozložení stránky zůstává stejná ve všech případech, zatímco kvalitu dokumentu maximalizuje možnosti jednotlivých zařízení.  
  
 Dokumenty toku naproti tomu jsou určená k optimalizaci pro zobrazení a čitelnost a jsou co nejlépe využít v případě snadné čtení je scénář využití primární dokumentu. Dokumenty toku místo nastavování jedno předdefinované rozložení dynamicky upravit a přeformátování jejich obsah na základě proměnných za běhu, jako je například velikost okna, rozlišení zařízení a volitelné uživatelských předvoleb. Webová stránka je jednoduchý příklad plovoucí dokument, kde je obsah stránky dynamicky formátovaný podle aktuálního okna. Dokumenty toku optimalizovat zobrazení a čtení prostředí pro uživatele, založené na prostředí modulu runtime. Stejný tok dokument bude dynamicky přeformátovat pro optimální čitelnost na zobrazení s vysokým rozlišením 19 palce nebo malé 2 x 3, 5palcová PDA obrazovky. Kromě toho mají dokumenty toku počet integrované funkce, včetně vyhledávání, zobrazování režimy, které optimalizují čitelnost a umožňuje změnit velikost a vzhled písma.  Zobrazit [přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pro obrázky, ukázky a podrobné informace o toku dokumentů.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Ovládacích prvků dokumentu a rozložení textu  
 Rozhraní .NET Framework poskytuje sadu předdefinovaných ovládacích prvků, které usnadňují použití oprava dokumentů, dokumenty toku a obecné textu v rámci vaší aplikace.  Zobrazení obsahu pevné dokumentu je podporována při použití <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.  Zobrazení obsahu toku dokumentu se podporuje tři různé prvky: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> které mapují na jiného uživatelského scénáře (viz části níže).  Další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky poskytují používá zjednodušené rozložení, které podporují obecného textu (naleznete v tématu [Text v uživatelském rozhraní](#text_in_the_user_interface)níže).  
  
### <a name="fixed-document-control---documentviewer"></a>Oprava DocumentViewer – ovládací prvek dokumentu –  
 <xref:System.Windows.Controls.DocumentViewer> Ovládací prvek slouží k zobrazení <xref:System.Windows.Documents.FixedDocument> obsah. <xref:System.Windows.Controls.DocumentViewer> Poskytuje intuitivní uživatelské rozhraní, která poskytuje integrovanou podporu pro běžné operace, včetně tiskový výstup, zkopírujte do schránky, Lupa a funkcí pro hledání textového ovládacího prvku. Ovládací prvek poskytuje přístup k obsahu stránky prostřednictvím známých posouvací mechanismus. Stejně jako všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, <xref:System.Windows.Controls.DocumentViewer> podporuje úplné nebo částečné vytvoření nového stylu, což umožňuje ovládacího prvku vizuálně integrovat do prakticky jakékoli aplikaci nebo prostředí.  
  
 <xref:System.Windows.Controls.DocumentViewer> slouží k zobrazení obsahu v režimu jen pro čtení; úpravy nebo úpravy obsahu není k dispozici a není podporována.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Ovládací prvky toků dokumentu  
 **Poznámka:** Podrobnější informace o toku dokumentu funkcí a postupů pro jejich vytváření najdete v článku [přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 Zobrazení obsahu toku dokumentu se podporuje tři prvky: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> obsahuje funkce, které uživateli umožňuje dynamicky vybrat mezi různých režimů zobrazení, včetně zobrazení (stránka na-time) jednostránkové režimu, dvě--na stránkách (formát čtení adresáře) zobrazení režimu a režimu kontinuálního rolování (neomezené) zobrazení.  Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Pokud nepotřebujete umožňuje dynamicky přepnout mezi režimy různých zobrazení <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> poskytují nenáročný tok prohlížeče obsahu, které jsou opravené v režimu konkrétní zobrazení.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>Prohlížeč FlowDocumentPageViewer a prohlížeče FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Zobrazí obsah stránky v čase režimu zobrazení, zatímco <xref:System.Windows.Controls.FlowDocumentScrollViewer> ukazuje obsahu v režimu kontinuálního rolování.  Obě <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> jsou pevně režimu konkrétní zobrazení. Porovnat s <xref:System.Windows.Controls.FlowDocumentReader>, který obsahuje funkce, které uživateli umožňuje dynamicky vybrat mezi různé režimy zobrazení (podle <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> výčet), za cenu se náročnější než <xref:System.Windows.Controls.FlowDocumentPageViewer> nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Ve výchozím nastavení je vždy zobrazen svislý posuvník a vodorovný posuvník se zobrazí v případě potřeby. Výchozí hodnota [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro <xref:System.Windows.Controls.FlowDocumentScrollViewer> nezahrnuje panel nástrojů, nicméně <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> vlastnost slouží k povolení integrovaných nástrojů.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Text v uživatelském rozhraní  
 Kromě přidání textu do dokumentů, text je samozřejmě možné v uživatelském rozhraní aplikace, jako jsou formuláře. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje více ovládacích prvků pro vykreslení textu na obrazovce. Každý ovládací prvek je zacílený na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně platí <xref:System.Windows.Controls.TextBlock> element by měl použít, pokud je text omezená podpora vyžadovat, například stručný větu v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> lze použít, když je nutné podporovat minimální text. Další informace najdete v tématu [TextBlock – přehled](../../../../docs/framework/wpf/controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Balení dokumentů  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Poskytují efektivní způsob, jak uspořádat data aplikací, obsah dokumentu a související prostředky v jeden kontejner, který se snadno přístup, přenosných a snadno distribuovat. Příkladem je soubor ZIP <xref:System.IO.Packaging.Package> typ schopný obsahující více objektů jako jeden celek. Balení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] poskytnutí výchozí <xref:System.IO.Packaging.ZipPackage> implementace určená pomocí standardu Open Packaging Conventions s architekturou souboru XML a ZIP. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Balení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] se dají jednoduše vytvořit balíčky a k ukládání a přístup k objektům v nich. Objekt uložený v <xref:System.IO.Packaging.Package> se označuje jako <xref:System.IO.Packaging.PackagePart> ("součást"). Balíčky mohou zahrnovat také digitální certifikáty podepsané držitelem, které lze použít k identifikaci odesílatel požadavku dostane informaci část a ověřit, že nebyly upraveny obsahu balíčku.  Balíčky také zahrnout <xref:System.IO.Packaging.PackageRelationship> funkce, která umožňuje dodatečné informace, které se přidal do balíčku nebo ve spojení s konkrétní části beze změny ve skutečnosti obsah existujícího částí.  Balíček služby také podporu [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Architektura balíčku slouží jako základ pro počet klíčových technologií:  
  
-   [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty, které odpovídají [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Aplikace Microsoft Office "12" Otevřít formátu dokumentů XML (.docx).  
  
-   Formátuje text vlastního úložiště pro návrh aplikací.  
  
 Založené na rozhraní API pro balení <xref:System.Windows.Xps.Packaging.XpsDocument> je navržená speciálně pro ukládání [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oprava obsah dokumentů. <xref:System.Windows.Xps.Packaging.XpsDocument> Se samostatným dokumentem, který lze otevřít v prohlížeči se zobrazí v <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku, směrovat do zařazování tisku nebo přímo do výstupu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-kompatibilní tiskárny.  
  
 Následující části obsahují další informace o <xref:System.IO.Packaging.Package> a <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Balení komponent  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Balení rozhraní API umožňují data aplikací a dokumenty, které uspořádány do jedné přenosné jednotky. Soubor ZIP je jedním z nejběžnějších typů balíčků a je výchozí typ balíčku se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> sám o sobě představuje abstraktní třídu, ze které <xref:System.IO.Packaging.ZipPackage> je implementována pomocí otevřené standardní XML a ZIP soubor architektury.  <xref:System.IO.Packaging.Package.Open%2A> Používá metoda <xref:System.IO.Packaging.ZipPackage> vytvořit a používat soubory ZIP ve výchozím nastavení. Balíček může obsahovat tři základní typy položek:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Soubory obsahu, data, dokumenty a prostředků aplikace.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certifikát X.509] pro identifikaci, ověřování a ověřování.|  
|<xref:System.IO.Packaging.PackageRelationship>|Byly přidané informace vztahující se k balíčku nebo určitou část.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("součást") je abstraktní třída, která odkazuje na objekt uložený v <xref:System.IO.Packaging.Package>. Jako soubor ZIP balíčku částí odpovídají jednotlivé soubory, které jsou uloženy v souboru ZIP.  <xref:System.IO.Packaging.ZipPackagePart> poskytuje výchozí implementaci pro serializovatelné objekty uložené v <xref:System.IO.Packaging.ZipPackage>.  Jako systém souborů části obsažené v balíčku jsou uložené v hierarchické nebo "složku stylu" organizace.  Použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balení rozhraní API, aplikace může zapisovat, ukládání a číst více <xref:System.IO.Packaging.PackagePart> objektů pomocí jednoho kontejneru soubor ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Pro zabezpečení <xref:System.IO.Packaging.PackageDigitalSignature> ("digitální podpis") můžou být spojené s částí v rámci balíčku. A <xref:System.IO.Packaging.PackageDigitalSignature> zahrnuje [509], který poskytuje dvě funkce:  
  
1.  Identifikuje a ověřuje odesílatel požadavku dostane informaci části.  
  
2.  Ověřuje, že byl změněn části.  
  
 Digitální podpis část nebrání upravovat, ale ověření proti digitálního podpisu selže, pokud části žádným způsobem změněn. Aplikace potom může provést příslušnou akci, například blokovat otevření části nebo upozornit uživatele, že součásti se změnila a není bezpečná.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("relace") poskytuje mechanismus pro přidružení k balíčku nebo jeho části v rámci balíčku Další informace. Relace je úrovni balíčku zařízení, které můžete přidružit další informace o části beze změny obsahu skutečné části. Vkládání nových dat přímo do části obsah obvykle není praktické v mnoha případech:  
  
-   Skutečný typ části a jeho obsah schématu není znám.  
  
-   I v případě, že známé, nemusí schéma obsahu poskytují prostředky pro přidání nové informace.  
  
-   Části mohou být digitálně podepsána nebo zašifrována, vyloučí všechny změny.  
  
 Balíček relace umožňují zjistitelné pro přidání a přiřazení další informace o jednotlivých částí nebo celý balíček. Balíček relací se používají pro dvě primární funkce:  
  
1.  Definování vztahů závislosti z jedné části do jiné části.  
  
2.  Definování relací informace, které přidat poznámky nebo jiná data související s části.  
  
 A <xref:System.IO.Packaging.PackageRelationship> zajišťuje rychlá, zjistitelné definování závislostí a přidat další informace o přidružené k součástí balíčku nebo balíčku jako celek.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Vztahů závislosti  
 Vztahů závislosti se používají k popisu závislosti, které provádí jednou ze součástí jiné části. Balíček může obsahovat například část, která obsahuje jeden nebo více \<img > obrázku značky. Obrázek značky odkazovat na Image, které se nachází buď jako jiné části do balíčku interní nebo externí do balíčku (například přístupné přes Internet). Vytváření <xref:System.IO.Packaging.PackageRelationship> spojené s HTML soubor provede zjišťování a přístup k závislé prostředky rychlý a snadný. Prohlížeči nebo prohlížeč aplikace může přímý přístup k části vztahy a okamžitě začít sestavovat závislé prostředky bez znalosti schématu nebo analýzy dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Informace o vztahy  
 Poznámky a anotace, podobně jako <xref:System.IO.Packaging.PackageRelationship> lze také ukládat jiné typy informací, které mají být spojen s část bez nutnosti skutečně upravit samotný obsah části.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS – dokumenty  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dokument je balíček, který obsahuje jeden nebo více oprava – dokumenty společně s prostředky a informace požadované pro vykreslení.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] je také nativní [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] formát zařazování tisku souboru.  <xref:System.Windows.Xps.Packaging.XpsDocument> Je uložena v datové sadě standardní ZIP a může obsahovat kombinaci XML a binární komponenty, jako jsou soubory bitové kopie a písma. [PackageRelationships](#PackageRelationships) se používají k definování závislosti mezi obsahu a prostředků potřebných pro plně vykreslení dokumentu.  <xref:System.Windows.Xps.Packaging.XpsDocument> Design poskytuje jednotné, vysoce věrné dokument řešení, které podporuje více:  
  
-   Čtení, zápisu a ukládání-document obsah a prostředky jako jednu, přenosných a snadno distribuovat souboru.  
  
-   Zobrazování dokumentů [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] prohlížeč.  
  
-   Výstupu dokumentů v nativní zařazování tisku výstupního formát [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Směrování přímo na dokumenty [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-kompatibilní tiskárny.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
- [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)
- [Serializace a úložiště dokumentů](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)
