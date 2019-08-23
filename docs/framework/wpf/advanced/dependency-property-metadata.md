---
title: Metadata vlastností závislosti
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 154a2543c62de545e8b2df711d6ad51989d0689d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964852"
---
# <a name="dependency-property-metadata"></a>Metadata vlastností závislosti
Systém [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastností zahrnuje systém vytváření sestav metadat, který překračuje, co může být oznámeno o vlastnosti prostřednictvím reflexe nebo obecných vlastností modulu CLR (Common Language Runtime). Metadata pro vlastnost závislosti lze také jednoznačně přiřadit třídou, která definuje vlastnost závislosti, lze změnit při přidání vlastnosti závislosti do jiné třídy a lze ji konkrétně přepsat všemi odvozenými třídami, které dědí vlastnost závislosti z definující základní třídy.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a přečetli jste si [Přehled vlastností závislosti](dependency-properties-overview.md). Chcete-li postupovat podle příkladů v tomto tématu, měli byste také [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pochopit a vědět, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] psát aplikace.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Jak se používají metadata vlastnosti závislosti  
 Metadata vlastnosti závislosti existují jako objekt, na který lze dotazovat, aby bylo možné zjistit vlastnosti závislosti. K těmto metadatům se také často používá systém vlastností při zpracovávání všech daných vlastností závislosti. Objekt metadat pro vlastnost závislosti může obsahovat následující typy informací:  
  
- Výchozí hodnota pro vlastnost závislosti, pokud nelze určit jinou hodnotu pro vlastnost závislosti podle místní hodnoty, stylu, dědičnosti atd. Důkladnou diskuzi o tom, jak se výchozí hodnoty účastní priority používané systémem vlastností při přiřazování hodnot pro vlastnosti závislosti, najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).  
  
- Odkazy na implementace zpětného volání, které mají vliv na chování při vynucení nebo změnách v oznámení na základě typu vlastníka. Všimněte si, že tato zpětná volání jsou často definována s úrovní přístupu NonPublic, takže získání skutečných odkazů z metadat obecně není možné, pokud odkazy nejsou v rámci povoleného oboru přístupu. Další informace o zpětných voláních vlastností závislosti naleznete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md).  
  
- Pokud je vlastnost závislosti považována za vlastnost na úrovni architektury WPF, metadata mohou obsahovat vlastnosti závislostí na úrovni architektury WPF, které hlásí informace a stav pro služby, jako je například WPF Framework-Level logika rozložení a dědičnosti vlastností. Další informace o tomto aspektu metadat vlastností závislosti najdete v tématu [Metadata vlastností rozhraní](framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Rozhraní API pro metadata  
 Typ, který hlásí většinu informací o metadatech používaných systémem vlastností, <xref:System.Windows.PropertyMetadata> je třída. Instance metadat jsou volitelně zadány, pokud jsou vlastnosti závislosti registrovány v systému vlastností a lze je zadat znovu pro další typy, které se buď přidají sami sebe jako vlastníci, nebo přepisují metadata, která dědí ze závislosti základní třídy. definice vlastnosti (Pro případy, kdy registrace vlastnosti neurčuje metadata, je výchozí hodnota <xref:System.Windows.PropertyMetadata> vytvořena s výchozími hodnotami pro tuto třídu.) Registrovaná metadata se vrátí jako <xref:System.Windows.PropertyMetadata> při volání různých <xref:System.Windows.DependencyProperty.GetMetadata%2A> přetížení, která získávají metadata z vlastnosti závislosti v <xref:System.Windows.DependencyObject> instanci.  
  
 <xref:System.Windows.PropertyMetadata> Třída je pak odvozena z, aby poskytovala konkrétnější metadata pro divize architektury, jako jsou třídy na úrovni architektury WPF. <xref:System.Windows.UIPropertyMetadata>Přidá vytváření sestav animace a <xref:System.Windows.FrameworkPropertyMetadata> poskytuje vlastnosti úrovně rozhraní WPF, které jsou uvedené v předchozí části. Pokud jsou vlastnosti závislosti registrovány, mohou být registrovány s <xref:System.Windows.PropertyMetadata> těmito odvozenými třídami. Při zkoumání metadat může být základní <xref:System.Windows.PropertyMetadata> typ potenciálně převeden na odvozené třídy, takže můžete prozkoumat konkrétnější vlastnosti.  
  
> [!NOTE]
> Charakteristiky vlastností, které lze zadat v <xref:System.Windows.FrameworkPropertyMetadata> , jsou v této dokumentaci někdy označovány jako "Příznaky". Když vytváříte nové instance metadat pro použití v registrech vlastností závislosti nebo přepsání metadat, určíte tyto hodnoty pomocí výčtu <xref:System.Windows.FrameworkPropertyMetadataOptions> flagwise a potom zadáte pravděpodobně zřetězené hodnoty výčtu do <xref:System.Windows.FrameworkPropertyMetadata> konstruktor. Po sestavení jsou však tyto charakteristiky možností zveřejněny v rámci <xref:System.Windows.FrameworkPropertyMetadata> jako série logických vlastností namísto konstrukce hodnoty výčtu. Logické vlastnosti umožňují kontrolu všech podmíněných hodnot a nevyžadují, abyste použili masku na hodnotu výčtu flagwise, abyste získali informace, které vás zajímají. Konstruktor používá zřetězení <xref:System.Windows.FrameworkPropertyMetadataOptions> , aby zachovala délku signatury konstruktoru, zatímco skutečná vytvořená metadata zpřístupňují diskrétní vlastnosti, aby bylo možné dotazování metadat intuitivnější.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Kdy přepsat metadata, kdy se má odvodit třída  
 Systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností má navázané možnosti pro změnu některých vlastností závislosti, aniž by bylo nutné je zcela znovu implementovat. Toho je možné dosáhnout vytvořením jiné instance metadat vlastnosti pro vlastnost závislosti, protože existuje pro konkrétní typ. Všimněte si, že většina existujících vlastností závislosti není virtuálními vlastnostmi, takže naprosto řečeno "opakované implementace" na zděděných třídách by mohla být zajištěna pouze pomocí stínování stávajícího člena.  
  
 Pokud scénář, který se pokoušíte povolit pro vlastnost závislosti na typu, nelze dosáhnout úpravou vlastností existujících vlastností závislosti, může být pak nutné vytvořit odvozenou třídu a následně deklarovat vlastní vlastnost závislosti. v odvozené třídě. Vlastní vlastnost závislosti se chová stejně jako vlastnosti závislosti definované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraními API. Další informace o vlastnostech vlastní závislosti najdete v tématu [vlastnosti vlastních závislostí](custom-dependency-properties.md).  
  
 Jednou z významných charakteristik vlastnosti závislosti, kterou nelze přepsat, je její typ hodnoty. Pokud jste zdědili vlastnost závislosti, která má přibližné chování, které požadujete, ale pro něj budete potřebovat jiný typ, budete muset implementovat vlastní vlastnost závislosti a možná propojit vlastnosti prostřednictvím konverze typu nebo jiného. implementace na vlastní třídě. Nelze také nahradit existující <xref:System.Windows.ValidateValueCallback>, protože toto zpětné volání existuje v samotném poli pro registraci a nikoli v rámci jeho metadat.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Scénáře změny stávajících metadat  
 Pokud pracujete s metadaty existující vlastnosti závislosti, jednou z běžných scénářů pro změnu metadat vlastností závislosti je Změna výchozí hodnoty. Změna nebo přidání zpětných volání systému vlastností je pokročilejší scénář. To může být vhodné, pokud vaše implementace odvozené třídy má různé vztahy mezi vlastnostmi závislosti. Jedna z podmíněných prvků s programovacím modelem, který podporuje jak kód, tak deklarativní použití je, že vlastnosti musí být nastaveny v libovolném pořadí. Proto musí být všechny závislé vlastnosti nastaveny za běhu bez kontextu a nemůžou se spoléhat na znalosti pořadí nastavení, jako je třeba najít v konstruktoru. Další informace o tomto aspektu systému vlastností naleznete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md). Všimněte si, že zpětná volání ověřování nejsou součástí metadat; jsou součástí identifikátoru vlastnosti závislosti. Proto nejde zpětná volání ověřování změnit přepsáním metadat.  
  
 V některých případech můžete také změnit možnosti metadat na úrovni rozhraní WPF Framework u existujících vlastností závislosti. Tyto možnosti sdělují určité známé podmíněné podmínky týkající se vlastností na úrovni WPF Frameworku na jiné procesy na úrovni architektury WPF, jako je například systém rozložení.  Nastavení možností se obvykle provádí pouze při registraci nové vlastnosti závislosti, ale je také možné změnit metadata <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> vlastností na úrovni architektury WPF v rámci volání nebo. <xref:System.Windows.DependencyProperty.AddOwner%2A> Konkrétní hodnoty, které se mají použít, a další informace najdete v tématu [Metadata vlastností rozhraní](framework-property-metadata.md). Další informace, které se týkají způsobu nastavení těchto možností pro nově registrovanou vlastnost závislosti, najdete v tématu [vlastnosti vlastních závislostí](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Přepsání metadat  
 Účelem přepsání metadat je primárně, abyste mohli změnit různá chování odvozená od metadat, která jsou použita na vlastnost závislosti, protože existuje pro váš typ. Důvody pro tento popis jsou podrobněji vysvětleny v části [metadata](#dp_metadata_contents) . Další informace, včetně některých příkladů kódu, najdete v tématu [přepis metadat pro vlastnost závislosti](how-to-override-metadata-for-a-dependency-property.md).  
  
 Metadata vlastnosti lze zadat pro vlastnost závislosti během volání registrace (<xref:System.Windows.DependencyProperty.Register%2A>). V mnoha případech však můžete chtít zadat metadata pro třídu specifická pro typ, pokud zdědí tuto vlastnost závislosti. To lze provést voláním <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody.  Například z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API <xref:System.Windows.FrameworkElement> třída je <xref:System.Windows.UIElement.Focusable%2A> typ, který nejprve zaregistruje vlastnost Dependency. Ale třída Přepisuje metadata pro vlastnost závislosti tak, aby poskytovala vlastní počáteční výchozí hodnotu, změnu z `false` na `true`a jinak znovu použije původní <xref:System.Windows.UIElement.Focusable%2A> implementaci. <xref:System.Windows.Controls.Control>  
  
 Při přepsání metadat jsou jednotlivé charakteristiky metadat sloučeny nebo nahrazeny.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>je sloučena. Pokud přidáte nové <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání nezadáte, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> hodnota se zvýší jako odkaz z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- Skutečným chováním systémových vlastností <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> pro je, že implementace všech vlastníků metadat v hierarchii jsou zachovány a přidány do tabulky, s pořadím provádění se systémem vlastností, které jsou vyvolány nejvíce odvozeného zpětného volání třídy.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>je nahrazen. Pokud <xref:System.Windows.PropertyMetadata.DefaultValue%2A> v přepsání nezadáte, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> hodnota se dostane z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementace jsou nahrazeny. Pokud přidáte nové <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání nezadáte, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hodnota se zvýší jako odkaz z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- Chování vlastností systému je pouze <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v případě, že je vyvolána pouze v bezprostředních metadatech. Neuchovávají se žádné <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> odkazy na jiné implementace v hierarchii.  
  
 Toto chování je implementováno <xref:System.Windows.PropertyMetadata.Merge%2A>nástrojem a lze je přepsat na odvozených třídách metadat.  
  
#### <a name="overriding-attached-property-metadata"></a>Přepsání připojených metadat vlastností  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]se jako vlastnosti závislosti implementují připojené vlastnosti. To znamená, že mají také metadata vlastností, které mohou jednotlivé třídy přepsat. Omezení rozsahu pro připojenou vlastnost v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou obecně taková, že pro každý <xref:System.Windows.DependencyObject> může být nastavená připojená vlastnost. Proto jakákoli <xref:System.Windows.DependencyObject> odvozená třída může přepsat metadata pro jakoukoli připojenou vlastnost, jak je možné ji nastavit na instanci třídy. Můžete přepsat výchozí hodnoty, zpětná volání nebo vlastnosti pro vytváření sestav na úrovni architektury WPF. Pokud je připojená vlastnost nastavená na instanci vaší třídy, použijí se tyto charakteristiky přepsání metadat vlastností. Můžete například přepsat výchozí hodnotu, což znamená, že hodnota přepsání je hlášena jako hodnota připojené vlastnosti v instancích třídy, pokaždé, když vlastnost není jinak nastavena.  
  
> [!NOTE]
> <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Vlastnost není relevantní pro připojené vlastnosti.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Přidání třídy jako vlastníka existující vlastnosti závislosti  
 Třída může přidat samu sebe jako vlastníka vlastnosti závislosti, která je již zaregistrována, pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metody. To umožňuje, aby třída používala vlastnost závislosti, která byla původně registrována pro jiný typ. Třída přidání není obvykle odvozenou třídou typu, který nejprve zaregistroval tuto vlastnost závislosti jako vlastníka. To umožňuje, aby vaše třída a její odvozené třídy zdědily implementaci vlastnosti závislosti bez původní třídy vlastníka a přidání třídy je ve stejné skutečné hierarchii třídy. Kromě toho může přidat třídu (a také všechny odvozené třídy) zadat metadata specifická pro typ původní vlastnosti závislosti.  
  
 Stejně jako vlastníkem prostřednictvím metod obslužného programu systému vlastností by třída přidání měla deklarovat další veřejné členy sám o sobě, aby mohla vlastnost závislosti] úplného účastníka v systému vlastností, aby se vydávala kód a kód. . Třída, která přidává existující vlastnost závislosti, má stejné zodpovědnosti jako v případě vystavení objektového modelu pro tuto vlastnost závislosti jako třída, která definuje novou vlastní vlastnost závislosti. První takový člen, který má být vystavení, je pole identifikátoru vlastnosti závislosti. Toto pole by mělo být `public static readonly` pole typu <xref:System.Windows.DependencyProperty>, které je přiřazeno k vrácené hodnotě <xref:System.Windows.DependencyProperty.AddOwner%2A> volání. Druhý člen, který má být definován, je vlastnost "wrapper" modulu CLR (Common Language Runtime). Obálka je mnohem pohodlnější pro manipulaci s vlastností závislosti v kódu (vyhnete se voláním <xref:System.Windows.DependencyObject.SetValue%2A> pokaždé a může provést volání pouze jednou v obálce samotné). Obálka je implementována stejně, jako by byla implementována v případě, že jste zaregistrovali vlastní vlastnost závislosti. Další informace o implementaci vlastnosti závislosti najdete v tématu [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [Přidání typu vlastníka pro vlastnost závislosti](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner a připojené vlastnosti  
 Můžete zavolat <xref:System.Windows.DependencyProperty.AddOwner%2A> na vlastnost závislosti, která je definována jako připojená vlastnost třídou Owner. Obecně je důvodem důvod k vystavení dříve připojené vlastnosti jako nepřipojené vlastnosti závislostí. Následně vystavíte <xref:System.Windows.DependencyProperty.AddOwner%2A> vrácenou hodnotu `public static readonly` jako pole jako identifikátor vlastnosti závislosti a definujete příslušné vlastnosti "Obálka" tak, aby se vlastnost zobrazila v tabulce členové a podporovala vlastnost, která není připojena. využití ve vaší třídě.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastnosti architektury](framework-property-metadata.md)
