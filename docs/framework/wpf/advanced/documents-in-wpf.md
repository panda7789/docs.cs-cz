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
ms.openlocfilehash: ced65795c66ab7c3b7eb6c25b225ec551c3969ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="documents-in-wpf"></a>Dokumenty v platformě WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nabízí širokou škálu funkcí dokumentu, které umožňují vytváření zachováním obsahu, který je navržený jako snadněji přístupu a čtení než v předchozích generací [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Kromě široké možnosti a kvalitu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje integrované služby pro zobrazení dokumentu, balení a zabezpečení. Toto téma obsahuje úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typů dokumentů a balení dokumentu.  
  
  
<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozdělí dokumenty na dvě rozsáhlé kategorie podle zamýšleného použití; Tyto kategorie dokumentu se říká "pevné dokumenty" a "toku dokumentů."  
  
 Opravené dokumenty jsou určené pro aplikace, které vyžadují přesné [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] prezentace, zobrazení nebo tiskárny hardwaru používaného nezávisle. Typické použití pevné dokumenty zahrnují publikování plochy, zpracování textu a rozložení formuláře, kde je velmi důležité a původní návrh stránek. V rámci jeho rozložení pevné dokumentu udržuje přesné poziční umístění obsahu elementů nezávislé na zobrazení nebo tisku zařízení používá. Například pevnou dokument zobrazit na 96 dpi zobrazení se zobrazí stránka přesně stejné při je výstup 600 dpi laserová tiskárna jako když je výstup do phototypesetter 4800 dpi. Rozložení stránky zůstává stejná ve všech případech, zatímco kvalitu dokumentu maximalizuje na možnosti jednotlivých zařízení.  
  
 Pro srovnání dokumenty toku slouží k optimalizaci zobrazení a přehlednosti a jsou nejlépe využít v případě, že snadnější čtení je tento scénář spotřeby primární dokumentu. Místo je nastavená na jednu předdefinované rozložení, dokumenty toku dynamicky upravit a přeformátování obsah na základě proměnných runtime například volitelné uživatelské předvolby, řešení zařízení a velikost okna. Webová stránka je jednoduchý příklad toku dokumentu, kde je obsah stránky dynamicky naformátovaný podle aktuální okna. Tok dokumenty optimalizovat zobrazení a čtení prostředí pro uživatele, na základě prostředí runtime. Například stejného toku dokumentu se dynamicky přeformátovat optimální čitelnější na zobrazení s vysokým rozlišením 19 palců nebo obrazovky PDA malé palců 2 × 3. Kromě toho mít toku dokumenty počet součástí funkce včetně vyhledávání, zobrazování režimy, které optimalizovat přehlednosti a možnost změny velikosti a vzhled písma.  V tématu [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pro obrázky, příklady a podrobné informace o toku dokumenty.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Ovládací prvky dokumentu a rozložení textu  
 Rozhraní .NET Framework poskytuje sadu předdefinovaných ovládacích prvků, které zjednodušují pomocí pevné dokumenty, tok dokumenty a obecné text v rámci vaší aplikace.  Zobrazení obsahu pevné dokumentu je podporována při použití <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.  Zobrazení obsahu dokumentu toku podporuje tři různé ovládacích prvků: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> který mapování na jiné scénáře uživatelů (viz níže uvedených částech).  Další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky poskytují používá zjednodušené rozložení, které podporují obecné text (najdete v části [Text v uživatelském rozhraní](#text_in_the_user_interface), níže).  
  
### <a name="fixed-document-control---documentviewer"></a>Ovládací prvek pevné dokumentu - třídy DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer> Řízení slouží k zobrazení <xref:System.Windows.Documents.FixedDocument> obsahu. <xref:System.Windows.Controls.DocumentViewer> Řízení poskytuje intuitivní uživatelské rozhraní, které poskytuje integrovanou podporu pro běžné operace, včetně tiskový výstup, zkopírujte do schránky, přiblížení a text vyhledávacích funkcí. Ovládací prvek poskytuje přístup k stránky obsahu prostřednictvím známých posouvací mechanismus. Všechny jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, <xref:System.Windows.Controls.DocumentViewer> podporuje úplné nebo částečné vytvoření nového stylu, které umožňuje kontrolu vizuálně integraci do prakticky jakékoli aplikaci nebo prostředí.  
  
 <xref:System.Windows.Controls.DocumentViewer> slouží k zobrazení obsahu v režimu jen pro čtení; úpravy nebo změna obsah není k dispozici a není podporována.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Ovládací prvky toku dokumentu  
 **Poznámka:** podrobnější informace o toku dokumentu funkce a jak je lze vytvořit, najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 Zobrazení obsahu dokumentu toku podporuje tři ovládacích prvků: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> obsahuje funkce, které uživateli umožňuje dynamicky zvolit různé režimy zobrazení, včetně režimu zobrazení jednostránkové (-na stránkách), dva--na stránkách (formát čtení kniha) zobrazení a průběžné posouvání režimu zobrazení (neomezené).  Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Pokud nepotřebujete schopnost dynamicky přepínání mezi režimy jiné zobrazení, <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> poskytují světlejšího váhy toku obsahu prohlížeče, opravené v režimu konkrétní zobrazení.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer a třídy FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Zobrazuje obsah stránky na čas režimu zobrazení při <xref:System.Windows.Controls.FlowDocumentScrollViewer> ukazuje obsahu v průběžném režimu posouvání.  Obě <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> opravě do režimu konkrétní zobrazení. Porovnání <xref:System.Windows.Controls.FlowDocumentReader>, což zahrnuje funkce, které uživateli umožňuje dynamicky zvolit různé režimy zobrazení (jako poskytované <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> – výčet), za cenu probíhá další náročné než <xref:System.Windows.Controls.FlowDocumentPageViewer> nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Ve výchozím nastavení je vždy zobrazen svislý posuvník a vodorovný posuvník se zobrazí v případě potřeby. Výchozí hodnota [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro <xref:System.Windows.Controls.FlowDocumentScrollViewer> nezahrnuje panel nástrojů, nicméně <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> vlastnost slouží k povolení integrované panelu nástrojů.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Text v uživatelském rozhraní  
 Kromě přidávání textu do dokumentů, text samozřejmě slouží v aplikaci uživatelského rozhraní, například formuláře. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje více ovládacích prvků pro kreslení textu na obrazovce. Každý ovládací prvek je zaměřena na jiný scénář a má svou vlastní seznam funkcí a omezení. Obecně <xref:System.Windows.Controls.TextBlock> element byste měli použít, pokud text omezenou podporu vyžadovat, například stručný věty v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> můžete použít, když je potřebná podpora minimální text. Další informace najdete v tématu [TextBlock přehled](../../../../docs/framework/wpf/controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Balení dokumentu  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Poskytují efektivní způsob, jak uspořádat data aplikací, obsah dokumentu a související prostředky v jednom kontejneru, který je jednoduchý k přístupu, přenosných a usnadňuje distribuci. Příkladem je soubor ZIP <xref:System.IO.Packaging.Package> typ schopná podržíte více objektů jako na jednu jednotku. Balení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] poskytnutí výchozí <xref:System.IO.Packaging.ZipPackage> implementace určená pomocí standardu Open Packaging Conventions architektura souboru XML a ZIP. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Balení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zjednodušují vytváření balíčků a k ukládání a přístup k objektům v nich. Objekt uložený v <xref:System.IO.Packaging.Package> se označuje jako <xref:System.IO.Packaging.PackagePart> ("část"). Balíčky můžou taky patřit digitální certifikáty podepsané držitelem, které lze použít k identifikaci odesílatel součástí a ověřit, zda nebyly upraveny obsah balíčku.  Balíčky také obsahovat <xref:System.IO.Packaging.PackageRelationship> funkce, která umožňuje dodatečné informace, které se přidal do balíčku nebo ve spojení s konkrétní části beze změny ve skutečnosti obsah existující částí.  Balíček služby také podpora [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Balíček architektura slouží jako základ pro počet klíčové technologie:  
  
-   [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty vyhovující [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Aplikace Microsoft Office "12" otevřete formátu dokumentů XML (.docx).  
  
-   Vlastní úložiště naformátuje pro návrhu aplikace.  
  
 Podle balení rozhraní API, <xref:System.Windows.Xps.Packaging.XpsDocument> je určená speciálně pro ukládání [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pevné obsahu dokumenty. <xref:System.Windows.Xps.Packaging.XpsDocument> Je úplný a samostatný dokumentu, který lze otevřít v prohlížeči se zobrazí v <xref:System.Windows.Controls.DocumentViewer> řízení, směruje na zařazování tisku, nebo přímo na výstup [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-kompatibilní tiskárny.  
  
 Následující části obsahují další informace na <xref:System.IO.Packaging.Package> a <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Součásti balíčku  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Balení rozhraní API umožňují data aplikací a dokumenty, které se uspořádají do jediné přenosné jednotky. Soubor ZIP je jedním z nejběžnějších typů balíčků a je výchozí typ balíčku se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> samotný je abstraktní třída, ze kterého <xref:System.IO.Packaging.ZipPackage> je implementovaná pomocí otevřete standardní XML a ZIP souboru architekturu.  <xref:System.IO.Packaging.Package.Open%2A> Používá metoda <xref:System.IO.Packaging.ZipPackage> vytvořit a používat soubory ZIP. ve výchozím nastavení. Balíček může obsahovat tři základní typy položek:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Soubory obsahu, data, dokumenty a prostředků aplikace.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certifikát X.509] pro identifikaci, ověřování a ověřování.|  
|<xref:System.IO.Packaging.PackageRelationship>|Přidané informace týkající se balíček nebo v určité části.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("část") je abstraktní třída, která odkazuje na objekt uložen v <xref:System.IO.Packaging.Package>. V souboru ZIP součásti balíčků odpovídají jednotlivé soubory uložené v souboru ZIP.  <xref:System.IO.Packaging.ZipPackagePart> poskytuje výchozí implementaci pro serializovatelné objekty uložené v <xref:System.IO.Packaging.ZipPackage>.  Jako systém souborů části obsažené v balíčku jsou uložené v hierarchické nebo organizace "složky stylu".  Pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balení rozhraní API, aplikace můžete zapsat, ukládání a čtení více <xref:System.IO.Packaging.PackagePart> objekty pomocí jediný kontejner souboru ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Pro zabezpečení <xref:System.IO.Packaging.PackageDigitalSignature> (dále jen "digitální podpis") může být přidružen části v rámci balíčku. A <xref:System.IO.Packaging.PackageDigitalSignature> zahrnuje [509], který poskytuje dvě funkce:  
  
1.  Identifikuje a ověřuje původce části.  
  
2.  Ověří, že části nebyl změněn.  
  
 Digitální podpis nebrání součástí upravována, ale kontrolu ověření proti digitálního podpisu selže, pokud části žádným způsobem změněn. Aplikace může potom proveďte příslušné akce – například blokovat otevření části nebo upozornit uživatele, že část byla změněna a není zabezpečený.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("vztah") poskytuje mechanismus pro přidružení k balíčku nebo její část v rámci balíčku Další informace. Relace je budovy úrovni balíčku, který můžete přidružit další informace s částí beze změny obsahu skutečné části. Vkládání nových dat přímo do části obsah není praktické v mnoha případech:  
  
-   Skutečný typ části a jeho obsahu schématu není znám.  
  
-   I když označuje, nemusí schéma obsahu poskytují prostředky pro přidání nové informace.  
  
-   Část může být digitálně podepsána nebo zašifrována, aby vyloučil žádné změny.  
  
 Balíček vztahy poskytují zjistitelný prostředky pro přidávání a přidružení Další informace o jednotlivých částí nebo s celý balíček. Balíček relací se používají pro dvě primární funkce:  
  
1.  Definování relací závislost z jedné části k další části.  
  
2.  Definování relací informace, které přidat poznámky nebo jiná data související s části.  
  
 A <xref:System.IO.Packaging.PackageRelationship> poskytuje rychlý a zjistitelný znamená definovat závislosti a přidat další informace související s součástí balíčku nebo balíček jako celek.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Vztahy závislostí  
 Závislost relací se používají k popisu závislosti, které provádí jednou ze součástí v další části. Například balíček může obsahovat části aplikace HTML, který zahrnuje jednu nebo více \<img > obrázku značky. Obrázek značky odkazovat na bitové kopie, které se nachází buď jako ostatní části balíčku interních nebo externích do balíčku (například přístupné přes Internet). Vytváření <xref:System.IO.Packaging.PackageRelationship> přidružené díky soubor HTML zjišťování a závislé prostředky rychlý a snadný přístup. Aplikace prohlížeče nebo prohlížeč můžete přímý přístup k části vztahy a okamžitě začít sestavovat závislé prostředky bez vědomí schématu nebo analýzy dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Informace o relacích  
 Podobně jako poznámka nebo poznámky, <xref:System.IO.Packaging.PackageRelationship> lze také použít k uložení jiné typy informací, které mají být spojeny s částí bez nutnosti ve skutečnosti upravte samotný obsah část.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Dokumenty XPS  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dokument je balíček, který obsahuje jeden nebo více pevné dokumentů spolu s prostředky a informace požadované pro vykreslení.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] je také nativního [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] formát zařazování tisku souboru.  <xref:System.Windows.Xps.Packaging.XpsDocument> Je uložený v datové sadě standardní ZIP a může obsahovat kombinaci XML a binární součásti, jako jsou soubory bitové kopie a písma. [PackageRelationships](#PackageRelationships) slouží k definování závislostí mezi obsahem a prostředky potřebné k vykreslení plně dokumentu.  <xref:System.Windows.Xps.Packaging.XpsDocument> Design poskytuje řešení zachováním dokumentu, které podporuje více používá:  
  
-   Čtení, zápisu a ukládání obsahu-document a prostředky jako soubor jeden, přenosných a snadno distribuovat.  
  
-   Zobrazování dokumentů [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] prohlížeč aplikace.  
  
-   Formát výstupu dokumentů v nativní zařazování tisku výstup [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Směrování přímo na dokumenty [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-kompatibilní tiskárny.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.FixedDocument>  
 <xref:System.Windows.Documents.FlowDocument>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.IO.Packaging.ZipPackage>  
 <xref:System.IO.Packaging.ZipPackagePart>  
 <xref:System.IO.Packaging.PackageRelationship>  
 <xref:System.Windows.Controls.DocumentViewer>  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Serializace a úložiště dokumentů](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)
