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
ms.openlocfilehash: fbd4df8820073a3cdf2a8d5aad9c56bd7ca751df
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460525"
---
# <a name="documents-in-wpf"></a>Dokumenty v platformě WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nabízí široké spektrum funkcí dokumentu, které umožňují vytvářet obsah s vysokou přesností, který je navržený tak, aby byl snadněji přistupný a čtený než v předchozích generacích systému Windows. Kromě rozšířených možností a kvality [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taky nabízí integrované služby pro zobrazení dokumentů, balení a zabezpečení. Toto téma poskytuje Úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typů dokumentů a balení dokumentu.  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozděluje dokumenty do dvou rozsáhlých kategorií na základě zamýšleného použití; Tyto kategorie dokumentů jsou označovány jako "pevné dokumenty" a "Flow Documents".  
  
 Pevné dokumenty jsou určené pro aplikace, které vyžadují přesný popis "co vidíte" (WYSIWYG) prezentace, nezávisle na používaném zobrazovacím nebo tiskovém hardwaru. Typické použití pro pevné dokumenty zahrnuje publikování desktopů, zpracování slov a rozložení formuláře, kde je důležité, aby bylo dodržování původního návrhu stránky kritické. V rámci jeho rozložení pevný dokument udržuje přesné umístění prvků obsahu nezávisle na zobrazovacím nebo tiskovém zařízení. Například pevná stránka dokumentu zobrazená na 96 dpi se zobrazí přesně stejně, jako je výstup na laserovou tiskárnu 600 dpi, jako když se jedná o výstup na 4800 dpi Phototypesetter. Rozložení stránky zůstane stejné ve všech případech, ale kvalita dokumentu se maximalizuje na možnosti jednotlivých zařízení.  
  
 Díky porovnání jsou dokumenty Flow navrženy tak, aby optimalizované zobrazení a čitelnost a byly nejlépe využívány, když je snadné čtení scénářem využití primárních dokumentů. Místo toho, aby se nastavily na jedno předdefinované rozložení, dokumenty Flow dynamicky upravují a přenášejí svůj obsah na základě proměnných run-time, jako je velikost okna, rozlišení zařízení a volitelné předvolby uživatele. Webová stránka je jednoduchý příklad dokumentu toku, ve kterém se obsah stránky dynamicky naformátuje tak, aby odpovídal aktuálnímu oknu. Flow Documents optimalizuje možnosti zobrazení a čtení pro uživatele na základě běhového prostředí. Například stejný flowový dokument bude dynamicky přeformátovat pro optimální čitelnost na displejích s vysokým rozlišením nebo na malé 2x3 obrazovky PDA. Kromě toho mají dokumenty Flow řadu integrovaných funkcí, včetně vyhledávání, zobrazení režimů, které optimalizují čitelnost, a možnosti měnit velikost a vzhled písem.  Přečtěte si [Přehled dokumentů Flow](flow-document-overview.md) pro ilustrace, příklady a podrobné informace o dokumentech Flow.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Ovládací prvky dokumentu a rozložení textu  
 .NET Framework poskytuje sadu předem připravených ovládacích prvků, které zjednodušují použití pevných dokumentů, toků dokumentů a obecného textu v rámci aplikace.  Zobrazení pevného obsahu dokumentu je podporováno pomocí ovládacího prvku <xref:System.Windows.Controls.DocumentViewer>.  Zobrazení obsahu dokumentu toku je podporováno třemi různými ovládacími prvky: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer>, které se mapují k různým uživatelským scénářům (viz část níže).  Jiné ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytují zjednodušené rozložení pro podporu obecného používání textu (viz [text v uživatelském rozhraní](#text_in_the_user_interface)níže).  
  
### <a name="fixed-document-control---documentviewer"></a>Pevný ovládací prvek dokumentu – DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer> ovládací prvek je navržen pro zobrazení obsahu <xref:System.Windows.Documents.FixedDocument>. Ovládací prvek <xref:System.Windows.Controls.DocumentViewer> poskytuje intuitivní uživatelské rozhraní, které poskytuje integrovanou podporu pro běžné operace, včetně výstupu tisku, kopírování do schránky, přiblížení a funkcí vyhledávání textu. Ovládací prvek poskytuje přístup k stránkám obsahu prostřednictvím známého rolovacího mechanismu. Stejně jako všechny ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.DocumentViewer> podporuje kompletní nebo částečné překládání, což umožňuje, aby byl ovládací prvek vizuálně integrován do prakticky jakékoli aplikace nebo prostředí.  
  
 <xref:System.Windows.Controls.DocumentViewer> je navržena pro zobrazení obsahu způsobem jen pro čtení; Úprava nebo úprava obsahu není k dispozici a není podporována.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Ovládací prvky dokumentu toku  

> [!NOTE]
> Podrobnější informace o funkcích dokumentů Flow a o tom, jak je vytvořit, najdete v tématu [Přehled dokumentů Flow](flow-document-overview.md).  
  
 Zobrazení obsahu dokumentu toku je podporováno třemi ovládacími prvky: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> obsahuje funkce, které umožňují uživateli dynamicky volit mezi různými režimy zobrazení, včetně jednostránkového režimu pro zobrazení na stránce (na úrovni stránky), režimu zobrazení na dvě stránky (formát pro čtení knih) a průběžného posouvání (bez dolního okraje). režim zobrazení.  Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Pokud nepotřebujete, aby bylo možné dynamicky přepínat mezi různými režimy zobrazení, <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> poskytují velmi náročné prohlížeče obsahu toku, které jsou opraveny v určitém režimu zobrazení.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>Prohlížeč FlowDocumentPageViewer a FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> zobrazuje obsah v režimu zobrazení stránky v čase, zatímco <xref:System.Windows.Controls.FlowDocumentScrollViewer> zobrazuje obsah v režimu nepřetržitého posouvání.  <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> jsou pevně dané pro určitý režim zobrazení. Porovnejte <xref:System.Windows.Controls.FlowDocumentReader>, které zahrnují funkce, které umožňují uživateli dynamicky volit mezi různými režimy zobrazení (poskytované <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> výčtu), a to za cenu většího množství prostředků než <xref:System.Windows.Controls.FlowDocumentPageViewer> nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Ve výchozím nastavení je vždy zobrazen svislý posuvník a v případě potřeby bude vodorovný posuvník viditelný. Výchozí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro <xref:System.Windows.Controls.FlowDocumentScrollViewer> neobsahují panel nástrojů. vlastnost <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> však lze použít k povolení integrovaného panelu nástrojů.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Text v uživatelském rozhraní  
 Kromě přidávání textu do dokumentů lze text zjevně použít v uživatelském rozhraní aplikace, jako jsou například formuláře. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje několik ovládacích prvků pro vykreslení textu na obrazovku. Každý ovládací prvek je zaměřený na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně platí, že element <xref:System.Windows.Controls.TextBlock> by měl být použit, pokud je vyžadována podpora omezeného textu, jako je například krátká věta v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> lze použít, pokud je požadována minimální podpora textu. Další informace najdete v tématu [TextBlock Overview](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Balení dokumentu  
 Rozhraní API pro <xref:System.IO.Packaging> poskytují efektivní způsob organizace dat aplikací, obsahu dokumentů a souvisejících prostředků v jediném kontejneru, který je jednoduchý pro přístup, přenos a snadné distribuci. Soubor ZIP je příkladem <xref:System.IO.Packaging.Package> typu, který dokáže podržet více objektů jako jednu jednotku. Rozhraní API pro balíčky poskytují výchozí <xref:System.IO.Packaging.ZipPackage> implementaci navrženou pomocí konvencí Open balení Standard s příponou souboru XML a ZIP. Rozhraní API pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balíčky usnadňují vytváření balíčků a ukládání a přístup k objektům v nich. Objekt uložený v <xref:System.IO.Packaging.Package> je označován jako <xref:System.IO.Packaging.PackagePart> ("část"). Balíčky mohou také obsahovat podepsané digitální certifikáty, které lze použít k identifikaci původce součásti a k ověření, že obsah balíčku nebyl změněn.  Balíčky také obsahují funkci <xref:System.IO.Packaging.PackageRelationship>, která umožňuje přidání dalších informací do balíčku nebo souvisejících s konkrétními částmi, aniž by došlo ke skutečné změně obsahu existujících částí.  Služba balíčků také podporuje Microsoft Windows Rights Management (RM).  
  
 Architektura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balíčku slouží jako základ pro řadu klíčových technologií:  
  
- Dokumenty XPS, které odpovídají specifikaci XPS (XML Paper Specification).  
  
- Systém Microsoft Office "12" otevřených dokumentů formátu XML (. docx).  
  
- Vlastní formáty úložiště pro vlastní návrh aplikace  
  
 Na základě rozhraní API pro balíčky je <xref:System.Windows.Xps.Packaging.XpsDocument> specificky navrženo pro ukládání [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokumentů s pevným obsahem. <xref:System.Windows.Xps.Packaging.XpsDocument> je samostatný dokument, který se dá otevřít v prohlížeči, který se zobrazuje v ovládacím prvku <xref:System.Windows.Controls.DocumentViewer>, směrován do tiskové fronty nebo na výstup přímo do tiskárny kompatibilní s XPS.  
  
 Následující části poskytují další informace o rozhraních API <xref:System.IO.Packaging.Package> a <xref:System.Windows.Xps.Packaging.XpsDocument> poskytovaných pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Součásti balíčku  
 Rozhraní API pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balíčky umožňují uspořádat data a dokumenty aplikace do jedné přenosné jednotky. Soubor ZIP je jedním z nejběžnějších typů balíčků a je výchozím typem balíčku, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> sám o sobě abstraktní třídu, ze které <xref:System.IO.Packaging.ZipPackage> implementována pomocí Open standard XML a architektury souboru ZIP.  Metoda <xref:System.IO.Packaging.Package.Open%2A> používá <xref:System.IO.Packaging.ZipPackage> k vytváření a používání souborů ZIP ve výchozím nastavení. Balíček může obsahovat tři základní typy položek:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Obsah aplikace, data, dokumenty a soubory prostředků.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certifikát X. 509] pro identifikaci, ověřování a ověřování.|  
|<xref:System.IO.Packaging.PackageRelationship>|Přidané informace týkající se balíčku nebo konkrétní části.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>Třídy PackagePart  
 <xref:System.IO.Packaging.PackagePart> ("část") je abstraktní třída, která odkazuje na objekt uložený ve <xref:System.IO.Packaging.Package>. V souboru ZIP součásti balíčku odpovídají jednotlivým souborům uloženým v souboru ZIP.  <xref:System.IO.Packaging.ZipPackagePart> poskytuje výchozí implementaci serializovatelných objektů uložených v <xref:System.IO.Packaging.ZipPackage>.  Podobně jako u systému souborů jsou části obsažené v balíčku uloženy v hierarchickém adresáři nebo v organizaci "styl složky".  Pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API pro balení můžou aplikace zapisovat, ukládat a číst víc objektů <xref:System.IO.Packaging.PackagePart> pomocí jediného kontejneru souboru ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Z důvodu zabezpečení lze <xref:System.IO.Packaging.PackageDigitalSignature> ("digitální podpis") přidružit k součástem v rámci balíčku. <xref:System.IO.Packaging.PackageDigitalSignature> zahrnuje [509], které poskytují dvě funkce:  
  
1. Identifikuje a ověřuje původce části.  
  
2. Ověřuje, že část nebyla upravena.  
  
 Digitální podpis nevylučuje součást, která by se dala měnit, ale ověření proti digitálnímu podpisu selže, pokud se část změní jakýmkoli způsobem. Aplikace potom může provést příslušnou akci – například blokovat otevření části nebo upozorňovat uživatele, že část byla upravena a není zabezpečená.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 <xref:System.IO.Packaging.PackageRelationship> ("relace") poskytuje mechanismus pro přidružení dalších informací k balíčku nebo části v rámci balíčku. Relace je zařízení na úrovni balíčku, které může k součásti přidružit další informace, aniž by bylo potřeba měnit obsah samotné části. Vkládání nových dat přímo do obsahu součásti není většinou praktické v mnoha případech:  
  
- Skutečný typ součásti a její schéma obsahu nejsou známy.  
  
- I v případě, že je známo, schéma obsahu nemusí poskytovat prostředky pro přidávání nových informací.  
  
- Část může být digitálně podepsaná nebo šifrovaná a bude tak zajímat změny.  
  
 Vztahy balíčku poskytují zjistitelný způsob přidávání a přiřazování dalších informací s jednotlivými částmi nebo celým balíčkem. Vztahy balíčku se používají pro dvě primární funkce:  
  
1. Definování vztahů závislosti z jedné části do jiné části.  
  
2. Definování vztahů s informacemi, které přidávají poznámky nebo jiná data související s částí.  
  
 <xref:System.IO.Packaging.PackageRelationship> poskytuje rychlé, zjistitelné prostředky k definování závislostí a přidání dalších informací přidružených k části balíčku nebo balíčku jako celku.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Vztahy závislosti  
 Vztahy závislostí se používají k popisu závislostí, které jedna část provede na jiné části. Balíček může například obsahovat část HTML, která obsahuje jednu nebo více \<značek > obrázku img. Značky image odkazují na obrázky, které se nacházejí buď jako jiné části, které jsou pro balíček interní, nebo jsou pro balíček externí (například přístupné přes Internet). Vytvoření <xref:System.IO.Packaging.PackageRelationship> přidruženého k souboru HTML usnadňuje a usnadňuje vyhledávání závislých prostředků a jejich přístup k nim. Aplikace prohlížeče nebo prohlížeče může přímý přístup k vztahům k částem a hned začít sestavovat závislé prostředky bez znalosti schématu nebo analýzy dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Informační vztahy  
 Podobně jako Poznámka nebo anotace lze <xref:System.IO.Packaging.PackageRelationship> použít také k ukládání dalších typů informací, které mají být přidruženy k části, aniž by bylo nutné skutečně upravovat samotný obsah součásti.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Dokumenty XPS  
 Dokument XPS (XML Paper Specification) je balíček, který obsahuje jeden nebo více pevných dokumentů společně se všemi prostředky a informacemi potřebnými pro vykreslování.  XPS je také nativní [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] formát souboru tiskové fronty.  <xref:System.Windows.Xps.Packaging.XpsDocument> je uložený ve standardní datové sadě ZIP a může zahrnovat kombinaci XML a binárních komponent, jako jsou obrázky a soubory písem. [PackageRelationships](#PackageRelationships) slouží k definování závislostí mezi obsahem a prostředky potřebnými k úplnému vygenerování dokumentu.  <xref:System.Windows.Xps.Packaging.XpsDocument> design poskytuje jedno řešení dokumentu s vysokou přesností, které podporuje více použití:  
  
- Čtení, zápis a ukládání obsahu a prostředků s pevným dokumentem jako jednoho, přenosného a snadno distribuovaného souboru.  
  
- Zobrazení dokumentů v aplikaci prohlížeč XPS.  
  
- Probíhá výstup dokumentů do nativního formátu výstupu tiskové fronty [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
- Směrování dokumentů přímo do tiskárny kompatibilní s XPS.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Text](optimizing-performance-text.md)
- [Přehled toku dokumentů](flow-document-overview.md)
- [Přehled tisku](printing-overview.md)
- [Serializace a úložiště dokumentů](document-serialization-and-storage.md)
