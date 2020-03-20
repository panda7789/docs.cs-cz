---
title: Dokumenty
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
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174677"
---
# <a name="documents-in-wpf"></a>Dokumenty v platformě WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Nabízí širokou škálu funkcí dokumentů, které umožňují vytváření obsahu s vysokou věrností, který je navržen tak, aby byl snadněji přístupný a čitelný než v předchozích generacích systému Windows. Kromě rozšířených funkcí a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kvality poskytuje také integrované služby pro zobrazení dokumentů, balení a zabezpečení. Toto téma obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] úvod k typům dokumentů a balení dokumentů.  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>Typy dokumentů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rozdělí dokumenty do dvou širokých kategorií na základě jejich zamýšleného použití; Tyto kategorie dokumentů se nazývají "pevné dokumenty" a "dokumenty toku".  
  
 Pevné dokumenty jsou určeny pro aplikace, které vyžadují přesnou prezentaci "co vidíte, je to, co dostanete" (WYSIWYG), nezávisle na použitém displeji nebo hardwaru tiskárny. Mezi typické použití pevných dokumentů patří publikování na ploše, zpracování textu a rozložení formuláře, kde je důležité přilnavost k původnímu návrhu stránky. V rámci svého rozvržení zachovává pevný dokument přesné polohové umístění prvků obsahu nezávisle na displeji nebo tiskovém zařízení, které se používá. Například stránka pevného dokumentu zobrazená na displeji 96 dpi se zobrazí přesně stejně, když je výstupem na laserovou tiskárnu 600 dpi, jako když je výstupem na fototypizér 4800 dpi. Rozložení stránky zůstává ve všech případech stejné, zatímco kvalita dokumentu maximalizuje možnosti každého zařízení.  
  
 Pro srovnání, tok dokumenty jsou navrženy tak, aby optimalizovat zobrazení a čitelnost a jsou nejlépe využít, když snadnost čtení je primární scénář spotřeby dokumentu. Místo toho, aby byly nastaveny na jedno předdefinované rozložení, dokumenty toku dynamicky upravují a přeformátují jejich obsah na základě proměnných za běhu, jako je velikost okna, rozlišení zařízení a volitelné uživatelské předvolby. Webová stránka je jednoduchý příklad toku dokumentu, kde je obsah stránky dynamicky formátován tak, aby odpovídal aktuálnímu oknu. Tok dokumenty optimalizovat zobrazení a čtení pro uživatele na základě runtime prostředí. Například stejný tok dokumentu bude dynamicky přeformátovat pro optimální čitelnost buď s vysokým rozlišením 19 palcový displej nebo malé 2x3-palcový PDA obrazovky. Kromě toho mají dokumenty toku řadu vestavěných funkcí, včetně vyhledávání, režimů zobrazení, které optimalizují čitelnost, a schopnosti měnit velikost a vzhled písem.  Obrázky, příklady a podrobné informace o dokumentech toku najdete v tématu [Přehled tokového dokumentu.](flow-document-overview.md)  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>Ovládací prvky dokumentů a rozložení textu  
 Rozhraní .NET Framework poskytuje sadu předem vytvořených ovládacích prvků, které zjednodušují používání pevných dokumentů, dokumentů toku a obecného textu v rámci vaší aplikace.  Zobrazení pevného obsahu dokumentu je <xref:System.Windows.Controls.DocumentViewer> podporováno pomocí ovládacího prvku.  Zobrazení obsahu tokového dokumentu je <xref:System.Windows.Controls.FlowDocumentReader>podporováno třemi různými ovládacími prvky: , <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> které se mapují na různé uživatelské scénáře (viz části níže).  Další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky poskytují zjednodušené rozložení pro podporu obecných použití textu (viz [Text v uživatelském rozhraní](#text_in_the_user_interface)níže).  
  
### <a name="fixed-document-control---documentviewer"></a>Opraveno řízení dokumentů - DocumentViewer  
 Ovládací <xref:System.Windows.Controls.DocumentViewer> prvek je <xref:System.Windows.Documents.FixedDocument> určen k zobrazení obsahu. Ovládací <xref:System.Windows.Controls.DocumentViewer> prvek poskytuje intuitivní uživatelské rozhraní, které poskytuje integrovanou podporu pro běžné operace, včetně tiskového výstupu, kopírování do schránky, přiblížení a funkcí pro vyhledávání textu. Ovládací prvek poskytuje přístup ke stránkám obsahu prostřednictvím známého posouvání mechanismus. Stejně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako <xref:System.Windows.Controls.DocumentViewer> všechny ovládací prvky podporuje kompletní nebo částečný restyling, který umožňuje vizuální integraci ovládacího prvku do prakticky libovolné aplikace nebo prostředí.  
  
 <xref:System.Windows.Controls.DocumentViewer>je navržen tak, aby zobrazoval obsah jen pro čtení; úpravy nebo úpravy obsahu nejsou k dispozici a nejsou podporovány.  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>Ovládací prvky dokumentu toku  

> [!NOTE]
> Podrobnější informace o funkcích toku dokumentu a jejich vytváření naleznete v [tématu Přehled dokumentu toku](flow-document-overview.md).  
  
 Zobrazení obsahu dokumentu toku je <xref:System.Windows.Controls.FlowDocumentReader>podporováno třemi ovládacími prvky: , <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>obsahuje funkce, které uživateli umožňují dynamicky si vybrat mezi různými režimy zobrazení, včetně režimu zobrazení na jednu stránku (po stránce) , režimu zobrazení se dvěma stránkami za čas (formát čtení knih) a režimu nepřetržitého posouvání (bezedné).  Další informace o těchto režimech zobrazení naleznete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Pokud nepotřebujete možnost dynamicky přepínat mezi <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> různými režimy zobrazení a poskytovat prohlížeče obsahu s nižší hmotností, které jsou opraveny v určitém režimu zobrazení.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer a FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>zobrazuje obsah v režimu zobrazení po celou <xref:System.Windows.Controls.FlowDocumentScrollViewer> dobu, zatímco zobrazuje obsah v režimu nepřetržitého posouvání.  Obě <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> a jsou upevněny do určitého režimu zobrazení. Porovnat <xref:System.Windows.Controls.FlowDocumentReader>s , který zahrnuje funkce, které umožňují uživateli dynamicky volit <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> mezi různými režimy zobrazení (jak <xref:System.Windows.Controls.FlowDocumentPageViewer> je <xref:System.Windows.Controls.FlowDocumentScrollViewer>stanoveno ve výčtu), za cenu, že jsou náročnější na prostředky než nebo .  
  
 Ve výchozím nastavení je vždy zobrazen svislý posuvník a v případě potřeby se zobrazí vodorovný posuvník. Výchozí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hodnota <xref:System.Windows.Controls.FlowDocumentScrollViewer> pro neobsahuje panel nástrojů; <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> vlastnost však lze použít k povolení předdefinovaného panelu nástrojů.  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>Text v uživatelském rozhraní  
 Kromě přidávání textu do dokumentů lze text samozřejmě použít v unovém formuláři aplikace, jako jsou formuláře. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje více ovládacích prvků pro kreslení textu na obrazovku. Každý ovládací prvek je zaměřen na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně by <xref:System.Windows.Controls.TextBlock> měl být prvek použit v případě, že je vyžadována omezená textová podpora, například stručná věta v rozhraní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>lze použít v případě, že je vyžadována minimální podpora textu. Další informace naleznete v tématu [Přehled textových bloků](../controls/textblock-overview.md).  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>Balení dokumentů  
 Api <xref:System.IO.Packaging> poskytují efektivní prostředky pro uspořádání dat aplikací, obsahu dokumentů a souvisejících prostředků v jednom kontejneru, který je jednoduchý na přístup, přenosný a snadno distribuovatelný. Soubor ZIP je příkladem <xref:System.IO.Packaging.Package> typu, který může ukládat více objektů jako jednu jednotku. Rozhraní API balení poskytují <xref:System.IO.Packaging.ZipPackage> výchozí implementaci navrženou pomocí standardu Open Packaging Conventions s architekturou souborů XML a ZIP. Balení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API usnadňují vytváření balíčků a ukládání a přístup k objektům v nich. Objekt uložený <xref:System.IO.Packaging.Package> v a se <xref:System.IO.Packaging.PackagePart> označuje jako ("část"). Balíčky mohou také obsahovat podepsané digitální certifikáty, které lze použít k identifikaci původce dílu a k ověření, zda obsah balíčku nebyl změněn.  Balíčky také <xref:System.IO.Packaging.PackageRelationship> obsahují funkci, která umožňuje přidat další informace do balíčku nebo přidružené k určitým částem bez skutečné úpravy obsahu existujících částí.  Služby balíčků také podporují správu práv systému Microsoft Windows (RM).  
  
 Architektura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balíčku slouží jako základ pro řadu klíčových technologií:  
  
- dokumenty XPS odpovídající specifikaci papíru XML (XPS).  
  
- Dokumenty ve formátu Microsoft Office "12" ve formátu XML (.docx).  
  
- Vlastní formáty úložiště pro vlastní návrh aplikace.  
  
 Na základě balení API, <xref:System.Windows.Xps.Packaging.XpsDocument> je speciálně navržen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro ukládání dokumentů s pevným obsahem. A <xref:System.Windows.Xps.Packaging.XpsDocument> je samostatný dokument, který lze otevřít v prohlížeči, <xref:System.Windows.Controls.DocumentViewer> zobrazit v ovládacím prvku, směrovat do tiskové cívky nebo výstup přímo do tiskárny kompatibilní se systémem XPS.  
  
 V následujících částech jsou <xref:System.IO.Packaging.Package> <xref:System.Windows.Xps.Packaging.XpsDocument> uvedeny další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]informace o a api dodaný s .  
  
<a name="packages"></a>
### <a name="package-components"></a>Komponenty balíčku  
 Balicí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] api umožňují uspořádat data aplikací a dokumenty do jedné přenosné jednotky. Soubor ZIP je jedním z nejběžnějších typů balíčků a je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]výchozím typem balíčku dodávaného s aplikací .  <xref:System.IO.Packaging.Package>sama o sobě je <xref:System.IO.Packaging.ZipPackage> abstraktní třída, ze které je implementována pomocí otevřené standardní architektury XML a ZIP souborů.  Metoda <xref:System.IO.Packaging.Package.Open%2A> používá <xref:System.IO.Packaging.ZipPackage> k vytvoření a použití souborů ZIP ve výchozím nastavení. Balíček může obsahovat tři základní typy položek:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Obsah aplikace, data, dokumenty a soubory prostředků.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certifikát X.509] pro identifikaci, ověření a ověření.|  
|<xref:System.IO.Packaging.PackageRelationship>|Byly přidány informace týkající se balíčku nebo konkrétní části.|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>BalíčekSoučásti  
 A <xref:System.IO.Packaging.PackagePart> ("část") je abstraktní třída, která odkazuje <xref:System.IO.Packaging.Package>na objekt uložený v . V souboru ZIP odpovídají části balíčku jednotlivým souborům uloženým v souboru ZIP.  <xref:System.IO.Packaging.ZipPackagePart>Poskytuje výchozí implementaci pro serializovatelné objekty uložené v aplikaci <xref:System.IO.Packaging.ZipPackage>.  Podobně jako v systému souborů jsou díly obsažené v balíčku uloženy v hierarchickém adresáři nebo v organizaci ve stylu složky.  Pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balení API aplikace můžete psát, ukládat <xref:System.IO.Packaging.PackagePart> a číst více objektů pomocí jednoho kontejneru souborů ZIP.  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>Balíček digitálních podpisů  
 Z bezpečnostních <xref:System.IO.Packaging.PackageDigitalSignature> důvodů lze ("digitální podpis") přidružit k součástem v rámci balíčku. A <xref:System.IO.Packaging.PackageDigitalSignature> obsahuje [509], který poskytuje dvě funkce:  
  
1. Identifikuje a ověřuje původce dílu.  
  
2. Ověří, zda součást nebyla změněna.  
  
 Digitální podpis nevylučuje změnu části, ale kontrola ověření digitálního podpisu se nezdaří, pokud dojde k jakékoli změně dílu. Aplikace pak může provést příslušnou akci – například zablokovat otevření dílu nebo upozornit uživatele, že díl byl změněn a není zabezpečený.  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("vztah") poskytuje mechanismus pro přidružení další informace s balíček nebo část v rámci balíčku. Vztah je zařízení na úrovni balíčku, které může přidružit další informace k dílu bez změny skutečného obsahu součásti. Vkládání nových dat přímo do obsahu části obvykle není praktické v mnoha případech:  
  
- Skutečný typ dílu a jeho schéma obsahu není znám.  
  
- I když je známo, schéma obsahu nemusí poskytnout prostředky pro přidávání nových informací.  
  
- Část může být digitálně podepsána nebo zašifrována, což vylučuje jakékoli změny.  
  
 Vztahy balíčků poskytují zjistitelné prostředky pro přidání a sousto dalších informací s jednotlivými částmi nebo s celým balíčkem. Vztahy balíčků se používají pro dvě primární funkce:  
  
1. Definování vztahů závislostí z jedné části do druhé.  
  
2. Definování vztahů informací, které přidávají poznámky nebo jiná data související s dílem.  
  
 A <xref:System.IO.Packaging.PackageRelationship> poskytuje rychlý, zjistitelné prostředky k definování závislostí a přidat další informace spojené s částí balíčku nebo balíček jako celek.  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>Vztahy závislostí  
 Vztahy závislostí se používají k popisu závislostí, které jedna část vytváří s jinými částmi. Balíček může například obsahovat část HTML, \<která obsahuje jednu nebo více značek> obrazu img. Značky obrázků odkazují na obrázky, které jsou umístěny buď jako jiné části vnitřní balíček nebo externí balíček (například přístupné přes Internet). Vytvoření <xref:System.IO.Packaging.PackageRelationship> přidruženého souboru HTML umožňuje rychlé a snadné zjišťování závislých prostředků a přístup k nim. Prohlížeč nebo prohlížeč aplikace můžete přímo přistupovat k části vztahy a okamžitě začít sestavení závislé prostředky bez znalosti schématu nebo analýzy dokumentu.  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>Vztahy s informacemi  
 Podobně jako poznámka nebo poznámka, <xref:System.IO.Packaging.PackageRelationship> lze také použít k ukládání jiných typů informací, které mají být přidruženy k dílu, aniž by bylo nutné skutečně upravit samotný obsah součásti.  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>Dokumenty XPS  
 Dokument SPECIFIKACE PAPÍRU XML (XPS) je balíček, který obsahuje jeden nebo více pevných dokumentů spolu se všemi prostředky a informacemi potřebnými pro vykreslování.  XPS je také nativní formát souboru zařazovací služby systému Windows Vista.  A <xref:System.Windows.Xps.Packaging.XpsDocument> je uložen ve standardní datové sadě ZIP a může obsahovat kombinaci xml a binárních komponent, jako jsou soubory obrázků a písem. [PackageRelationships](#PackageRelationships) se používají k definování závislostí mezi obsahem a prostředky potřebné k úplnému vykreslení dokumentu.  Návrh <xref:System.Windows.Xps.Packaging.XpsDocument> poskytuje jediné řešení dokumentu s vysokou věrností, které podporuje více použití:  
  
- Čtení, zápis a ukládání obsahu pevného dokumentu a prostředků jako jednoho, přenosného a snadno distribuovatelného souboru.  
  
- Zobrazení dokumentů pomocí aplikace XPS Viewer.  
  
- Výstup dokumentů ve výstupním formátu nativní tiskové zařazovací služby systému Windows Vista  
  
- Směrování dokumentů přímo do tiskárny kompatibilní se systémem XPS.  
  
## <a name="see-also"></a>Viz také

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
- [Serializace a úložiště dokumentu](document-serialization-and-storage.md)
