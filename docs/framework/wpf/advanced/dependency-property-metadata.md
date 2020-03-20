---
title: Metadata vlastností závislosti
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 3d84510fce69e81929cbe9b6088e12aaf3409769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186371"
---
# <a name="dependency-property-metadata"></a>Metadata vlastností závislosti
Systém [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastností obsahuje systém vykazování metadat, který přesahuje co lze ohlásit o vlastnosti prostřednictvím reflexe nebo obecné charakteristiky clr (common language runtime). Metadata pro vlastnost závislosti mohou být také přiřazena jedinečně třídou, která definuje vlastnost závislosti, může být změněna, když je vlastnost závislosti přidána do jiné třídy a může být specificky přepsána všemi odvozenými třídami, které dědí vlastnost závislosti z definující základní třídy.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnostem závislostí z pohledu příjemce existujících vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a že jste si přečetli přehled [vlastností závislostí](dependency-properties-overview.md). Chcete-li sledovat příklady v tomto tématu, měli byste také pochopit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="dp_metadata_contents"></a>
## <a name="how-dependency-property-metadata-is-used"></a>Použití metadat vlastnosti závislostí  
 Metadata vlastnosti závislostí existuje jako objekt, který může být dotazován ke kontrole charakteristiky vlastnosti závislosti. Tato metadata je také často přístupné systému vlastností, protože zpracovává všechny dané vlastnosti závislosti. Objekt metadat pro vlastnost závislosti může obsahovat následující typy informací:  
  
- Výchozí hodnota pro vlastnost závislosti, pokud nelze určit žádnou jinou hodnotu pro vlastnost závislosti podle místní hodnoty, stylu, dědičnosti atd. Podrobné informace o tom, jak se výchozí hodnoty zaujímají do priority používané systémem vlastností při přiřazování hodnot vlastností závislostí, naleznete v [tématu Priorita hodnoty vlastnosti závislostí](dependency-property-value-precedence.md).  
  
- Odkazy na implementace zpětného volání, které ovlivňují chování nátlaku nebo oznámení změn na základě typu vlastníka. Všimněte si, že tato zpětná volání jsou často definovány s úroveň přístupu neveřejné, takže získání skutečné odkazy z metadat obecně není možné, pokud odkazy jsou v rámci oboru povolený přístup. Další informace o zpětná volání vlastností závislostí naleznete v [tématu Zpětná volání vlastností závislostí a ověření](dependency-property-callbacks-and-validation.md).  
  
- Pokud je dotyčná vlastnost závislosti považována za vlastnost na úrovni architektury WPF, metadata mohou obsahovat vlastnosti vlastností závislostí na úrovni architektury WPF, které vykazují informace a stav pro služby, jako je například úroveň architektury WPF logika dědičnosti modulu rozložení a dědičnosti vlastností. Další informace o tomto aspektu metadat vlastností závislostí naleznete v [tématu Metadata vlastností rozhraní Framework](framework-property-metadata.md).  
  
<a name="APIs"></a>
## <a name="metadata-apis"></a>Metadata API  
 Typ, který hlásí většinu informací metadat používaných systémem <xref:System.Windows.PropertyMetadata> vlastností je třída. Instance metadat jsou volitelně určeny při registraci vlastností závislostí v systému vlastností a mohou být znovu zadány pro další typy, které se buď přidají jako vlastníci, nebo přepíší metadata, která dědí ze závislosti základní třídy. definice vlastnosti. (V případech, kdy registrace vlastnosti neurčuje <xref:System.Windows.PropertyMetadata> metadata, je vytvořen výchozí s výchozími hodnotami pro danou třídu.) Registrovaná metadata je <xref:System.Windows.PropertyMetadata> vrácena jako <xref:System.Windows.DependencyProperty.GetMetadata%2A> při volání různých přetížení, které získat <xref:System.Windows.DependencyObject> metadata z vlastnosti závislosti na instanci.  
  
 Třída <xref:System.Windows.PropertyMetadata> je pak odvozen z poskytnout konkrétnější metadata pro architektonické divize, jako jsou třídy wpf na úrovni architektury. <xref:System.Windows.UIPropertyMetadata>přidá vytváření sestav animace a <xref:System.Windows.FrameworkPropertyMetadata> poskytuje vlastnosti na úrovni architektury WPF uvedené v předchozí části. Při registraci vlastností závislostí mohou <xref:System.Windows.PropertyMetadata> být registrovány s těmito odvozenými třídami. Při zkoumání metadat, základní <xref:System.Windows.PropertyMetadata> typ může být potenciálně přetypována na odvozené třídy, takže můžete prozkoumat konkrétnější vlastnosti.  
  
> [!NOTE]
> Vlastnosti, které mohou <xref:System.Windows.FrameworkPropertyMetadata> být zadány v jsou někdy označovány v této dokumentaci jako "příznaky". Při vytváření nových instancí metadat pro použití v registraci vlastností závislostí nebo přepsání <xref:System.Windows.FrameworkPropertyMetadataOptions> metadat, zadáte tyto hodnoty pomocí výčtu ve <xref:System.Windows.FrameworkPropertyMetadata> výšce ve vlajkovém směru a pak zadáte případně zřetězené hodnoty výčtu konstruktoru. Jakmile jsou však tyto vlastnosti možnosti vytvořeny v rámci <xref:System.Windows.FrameworkPropertyMetadata> řady logických vlastností, nikoli hodnoty výpočtu. Logické vlastnosti umožňují zkontrolovat každou podmínku, nikoli vyžadovat použití masky na hodnotu výčtu ve výšce ve vlajkové masce, abyste získali informace, které vás zajímají. Konstruktor používá zřetězené, <xref:System.Windows.FrameworkPropertyMetadataOptions> aby byla délka podpisu konstruktoru přiměřená, zatímco skutečná vytvořená metadata zpřístupňují diskrétní vlastnosti, aby bylo dotazování metadat intuitivnější.  
  
<a name="override_or_subclass"></a>
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Kdy přepsat metadata, kdy odvodit třídu  
 Systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností vytvořil možnosti pro změnu některých charakteristik vlastností závislostí, aniž by bylo nutné je zcela znovu implementovat. Toho lze dosáhnout vytvořením jiné instance metadat vlastnosti pro vlastnost závislosti, protože existuje u určitého typu. Všimněte si, že většina existujících vlastností závislostí nejsou virtuální vlastnosti, takže přísně vzato "re-implementing" je na zděděné třídy lze provést pouze stínování existující člen.  
  
 Pokud scénář, který se pokoušíte povolit pro vlastnost závislosti na typu nelze provést změnou charakteristik existujících vlastností závislostí, může být nutné vytvořit odvozenou třídu a potom deklarovat vlastní vlastnost závislosti na odvozené třídě. Vlastnost vlastní závislost se chová stejně jako vlastnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] závislostí definované rozhraními API. Další podrobnosti o vlastních vlastnostech závislostí naleznete [v tématu Vlastní vlastnosti závislostí](custom-dependency-properties.md).  
  
 Jedna pozoruhodná charakteristika vlastnosti závislosti, kterou nelze přepsat, je její typ hodnoty. Pokud dědíte vlastnost závislosti, která má přibližné chování, které požadujete, ale pro něj vyžadujete jiný typ, budete muset implementovat vlastní vlastnost závislosti a možná propojit vlastnosti prostřednictvím převodu typu nebo jiné implementaci na vaší vlastní třídě. Také nelze nahradit existující <xref:System.Windows.ValidateValueCallback>, protože toto zpětné volání existuje v samotném registračním poli a nikoli v jeho metadatech.  
  
<a name="scenarios"></a>
## <a name="scenarios-for-changing-existing-metadata"></a>Scénáře pro změnu existujících metadat  
 Pokud pracujete s metadaty existující vlastnosti závislosti, jeden běžný scénář pro změnu metadat vlastnosti závislostí je změnit výchozí hodnotu. Změna nebo přidání zpětná volání systému vlastností je pokročilejší scénář. Můžete to provést, pokud vaše implementace odvozené třídy má různé vzájemné vztahy mezi vlastnostmi závislostí. Jednou z podmínek, které mají programovací model, který podporuje kód a deklarativní použití je, že vlastnosti musí povolit nastavení v libovolném pořadí. Proto všechny závislé vlastnosti musí být nastaveny just-in-time bez kontextu a nelze spoléhat na znalost pořadí nastavení, jako je možné nalézt v konstruktoru. Další informace o tomto aspektu systému vlastností naleznete v [tématu Zpětná volání vlastností závislostí a ověření](dependency-property-callbacks-and-validation.md). Všimněte si, že zpětná volání ověření nejsou součástí metadat; jsou součástí identifikátoru vlastnosti závislosti. Proto ověření zpětná volání nelze změnit přepsáním metadata.  
  
 V některých případech můžete také chtít změnit možnosti metadat vlastnosti na úrovni architektury WPF na existující vlastnosti závislostí. Tyto možnosti komunikují určité známé podmínky o vlastnostech na úrovni architektury WPF jiným procesům na úrovni architektury WPF, jako je například systém rozložení.  Nastavení možností se obvykle provádí pouze při registraci nové vlastnosti závislosti, ale je také možné změnit metadata vlastnosti wpf na úrovni rozhraní jako součást <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> nebo <xref:System.Windows.DependencyProperty.AddOwner%2A> volání. Konkrétní hodnoty, které mají být používány, a další informace naleznete v [tématu Metadata vlastností rozhraní Framework](framework-property-metadata.md). Další informace, které se relevantní k jak by měly být tyto možnosti nastaveny pro nově registrovanou vlastnost závislosti, naleznete [v tématu Vlastní vlastnosti závislostí](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>
### <a name="overriding-metadata"></a>Přepsání metadat  
 Účelem přepsání metadat je především tak, že máte možnost změnit různé chování odvozené metadata, které jsou použity na vlastnost závislosti, jak existuje na váš typ. Důvody jsou podrobněji vysvětleny v části [Metadata.](#dp_metadata_contents) Další informace, včetně některých příkladů kódu, naleznete [v tématu Přepsat metadata pro vlastnost závislosti](how-to-override-metadata-for-a-dependency-property.md).  
  
 Metadata vlastnosti mohou být poskytnuta pro vlastnost<xref:System.Windows.DependencyProperty.Register%2A>závislosti během volání registrace ( ). V mnoha případech však můžete chtít poskytnout metadata specifická pro typ pro vaši třídu, když zdědí tuto vlastnost závislosti. Můžete to provést voláním <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody.  Příklad z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] api <xref:System.Windows.FrameworkElement> je třída typ, který nejprve <xref:System.Windows.UIElement.Focusable%2A> registruje vlastnost závislosti. Ale <xref:System.Windows.Controls.Control> třída přepíše metadata pro vlastnost závislosti poskytnout vlastní počáteční výchozí `false` `true`hodnotu, změna z <xref:System.Windows.UIElement.Focusable%2A> na , a jinak znovu použije původní implementaci.  
  
 Když přepíšete metadata, různé charakteristiky metadat jsou sloučeny nebo nahrazeny.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>je sloučena. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je povýšen jako odkaz z nejbližšípředchůdce, který ji zadal v metadatech.  
  
- Skutečné chování systému <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> vlastností pro je, že implementace pro všechny vlastníky metadat v hierarchii jsou zachovány a přidány do tabulky, s pořadím provádění systémem vlastností je, že nejvíce odvozené třídy zpětná volání jsou vyvolány jako první.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>je nahrazen. Pokud nezadáte <xref:System.Windows.PropertyMetadata.DefaultValue%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližšípředchůdce, který ji zadal v metadatech.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementace jsou nahrazeny. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> je povýšen jako odkaz z nejbližšípředchůdce, který ji zadal v metadatech.  
  
- Chování systému vlastností <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> je, že je vyvolána pouze v bezprostřední metadata. Nejsou zachovány <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> žádné odkazy na jiné implementace v hierarchii.  
  
 Toto chování <xref:System.Windows.PropertyMetadata.Merge%2A>je implementováno společností , a může být přepsáno na odvozených třídách metadat.  
  
#### <a name="overriding-attached-property-metadata"></a>Přepsání metadat připojené vlastnosti  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oblasti jsou připojené vlastnosti implementovány jako vlastnosti závislostí. To znamená, že mají také metadata vlastností, které mohou přepsat jednotlivé třídy. Obory aspekty pro připojené vlastnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jsou <xref:System.Windows.DependencyObject> obecně, že každý může mít připojené vlastnosti nastavit na nich. Proto všechny <xref:System.Windows.DependencyObject> odvozené třídy můžete přepsat metadata pro všechny připojené vlastnosti, jako může být nastavena na instanci třídy. Můžete přepsat výchozí hodnoty, zpětná volání nebo WPF vlastnosti vykazování na úrovni architektury. Pokud je připojená vlastnost nastavena na instanci vaší třídy, platí tyto charakteristiky metadat přepsání vlastností. Například můžete přepsat výchozí hodnotu, tak, aby vaše hodnota přepsání je vykázána jako hodnota připojené vlastnosti na instance vaší třídy, kdykoli není jinak nastavena vlastnost.  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> není relevantní pro připojené vlastnosti.  
  
<a name="dp_add_owner"></a>
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Přidání třídy jako vlastníka existující vlastnosti závislosti  
 Třída můžete přidat sám jako vlastník vlastnosti závislosti, která již <xref:System.Windows.DependencyProperty.AddOwner%2A> byla zaregistrována pomocí metody. To umožňuje třídě použít vlastnost závislosti, která byla původně registrována pro jiný typ. Přidání třídy obvykle není odvozené třídy typu, který nejprve zaregistroval, že závislost vlastnost jako vlastník. Efektivně to umožňuje vaší třídě a její odvozené třídy "dědit" implementace vlastnosti závislostí bez původní vlastník třídy a přidání třídy je ve stejné hierarchii true třídy. Kromě toho přidání třídy (a všechny odvozené třídy také) pak můžete poskytnout metadata specifické pro typ pro původní vlastnost závislosti.  
  
 Stejně jako přidání sebe jako vlastníka prostřednictvím metody property system utility, přidání třídy by měl deklarovat další veřejné členy na sebe, aby se závislost vlastnost] úplný účastník v systému vlastností s expozicí kódu a značky . Třída, která přidá existující vlastnost závislosti, má stejné odpovědnosti, pokud jde o vystavení objektového modelu pro tuto vlastnost závislosti, stejně jako třída, která definuje novou vlastní vlastnost závislosti. První takový člen vystavit je pole identifikátor u vlastnosti závislostí. Toto pole `public static readonly` by mělo <xref:System.Windows.DependencyProperty>být poletypu , které <xref:System.Windows.DependencyProperty.AddOwner%2A> je přiřazeno k návratové hodnotě volání. Druhý člen definovat je common language runtime (CLR) "obálka" vlastnost. Obálka umožňuje mnohem pohodlnější manipulovat s vlastností závislostí v kódu <xref:System.Windows.DependencyObject.SetValue%2A> (vyhnete volání pokaždé a můžete provést toto volání pouze jednou v samotném obalu). Obálka je implementována identicky, jak by byla implementována, pokud jste registrovali vlastní závislost vlastnost. Další informace o implementaci vlastnosti závislosti naleznete v [tématu Vlastní vlastnosti závislostí](custom-dependency-properties.md) a [Přidání typu vlastníka pro vlastnost závislosti](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>Přidat vlastníka a připojené vlastnosti  
 Můžete volat <xref:System.Windows.DependencyProperty.AddOwner%2A> vlastnost závislosti, která je definována jako připojená vlastnost třídou vlastníka. Obecně důvodem pro to je vystavit dříve připojené vlastnosti jako vlastnost nepřipojené závislosti. Potom zpřístupníte <xref:System.Windows.DependencyProperty.AddOwner%2A> vrácenou `public static readonly` hodnotu jako pole pro použití jako identifikátor vlastnosti závislosti a definujete vhodné vlastnosti "obálky", takže vlastnost se zobrazí v tabulce členů a podporuje nepřipojené využití vlastnosti ve vaší třídě.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastnosti architektury](framework-property-metadata.md)
