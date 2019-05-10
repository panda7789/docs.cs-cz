---
title: Metadata vlastností závislosti
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: a4b2edce76bc5ab97e644ec8dbdf045931e87786
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663435"
---
# <a name="dependency-property-metadata"></a>Metadata vlastností závislosti
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Vlastnost systém zahrnuje metadata vytváření sestav systém, který jde nad rámec co může být nahlášené o vlastnosti prostřednictvím reflexe a Obecné [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] charakteristiky. Metadata pro vlastnost závislosti lze také přiřadit jednoznačně podle třídy, která definuje vlastnost závislosti, můžete změnit, pokud vlastnost závislosti je přidána do jiné třídy a může být explicitně přepsáno všechny odvozené třídy, které dědí Vlastnost závislosti z definující základní třídy.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnosti závislosti z pohledu příjemce vlastnosti existujícího závislosti na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a čtení [přehled vlastností závislosti](dependency-properties-overview.md). Pokud chcete postupovat podle příkladů v tomto tématu, měli byste také znát [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Jak se používá Metadata vlastností závislosti  
 Metadata vlastností závislosti existuje jako objekt, který může být dotazována k prozkoumání vlastností vlastnost závislosti. Tato metadata je také často přístupné vlastnosti systému jako zpracovává všechny danou vlastnost závislosti. Objekt metadat pro vlastnost závislosti může obsahovat následující typy informací:  
  
- Výchozí hodnota pro vlastnost závislosti, pokud žádná hodnota se dají určit pro vlastnost závislosti pomocí místní hodnoty, styl, dědičnost, atd. Důkladný rozbor jak výchozí hodnoty účastnit priority používá systémem vlastnost při přiřazování hodnot pro vlastnosti závislosti, v tématu [Priorita hodnot závislých vlastností](dependency-property-value-precedence.md).  
  
- Odkazy na implementace zpětného volání, které ovlivňují oznamování změn nebo konverze za chování na základě typu za vlastníka. Všimněte si, že tato zpětná volání jsou často definovány s úrovní přístupu neveřejné tak získání skutečné odkazů z metadat obecně není možné pokud odkazy nejsou v rámci vašeho oboru povolený přístup. Další informace o zpětných volání závislostí vlastnost, naleznete v tématu [vlastnost závislosti zpětné volání a ověření](dependency-property-callbacks-and-validation.md).  
  
- Pokud vlastnost závislosti dotyčný se považuje za vlastnost úrovni rozhraní WPF, metadata mohou obsahovat WPF závislostí na úrovni architektury vlastnost vlastnostmi, které zaznamenávají informace a stav služeb, jako je WPF úrovni framework modul a vlastnost dědičnosti logiku rozložení. Další informace o tento aspekt metadata vlastností závislosti, naleznete v tématu [Metadata vlastnosti architektury](framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Metadata API  
 Typ, který bude hlásit většinu informací metadat používané v systému vlastností je <xref:System.Windows.PropertyMetadata> třídy. Instance metadata jsou zadat při vlastnosti závislosti jsou registrovány v systému vlastností a je možné zadat znovu pro další typy, které se přidávají jako vlastníky nebo přetížení metadat, který dědí ze základní třídy závislosti definice vlastnosti. (Pro případy, kde registraci vlastnost neurčuje metadat, výchozí <xref:System.Windows.PropertyMetadata> se vytvoří s použitím výchozích hodnot pro danou třídu.) Registrované metadat se vrátí jako <xref:System.Windows.PropertyMetadata> při volání různých <xref:System.Windows.DependencyProperty.GetMetadata%2A> přetížení, která získat metadata z vlastnosti závislosti na <xref:System.Windows.DependencyObject> instance.  
  
 <xref:System.Windows.PropertyMetadata> Je pak třída odvozena z zajištění konkrétnější metadat pro architektury oddělení například třídy úrovni rozhraní WPF. <xref:System.Windows.UIPropertyMetadata> Přidá reporting animace a <xref:System.Windows.FrameworkPropertyMetadata> poskytuje vlastnosti úrovni rozhraní WPF uvedených v předchozí části. Když jsou registrované vlastnosti závislosti, lze registrovat pomocí těchto <xref:System.Windows.PropertyMetadata> odvozené třídy. Když je zkontrolován metadata, základní <xref:System.Windows.PropertyMetadata> typ může být převeden na odvozené třídy potenciálně, tak, aby můžete prozkoumat další specifické vlastnosti.  
  
> [!NOTE]
>  Vlastnost charakteristiky, které lze zadat v <xref:System.Windows.FrameworkPropertyMetadata> jsou někdy označovány jako "flags" této dokumentace. Při vytváření nové instance metadata pro použití v závislosti registrace vlastností nebo metadat přepsání, zadejte tyto hodnoty pomocí flagwise výčtu <xref:System.Windows.FrameworkPropertyMetadataOptions> a pak poskytnete pravděpodobně zřetězených hodnot výčtu <xref:System.Windows.FrameworkPropertyMetadata> konstruktoru. Však po vytvořen, tyto možnosti vlastnosti jsou vystaveny v rámci <xref:System.Windows.FrameworkPropertyMetadata> jako pro řadu logické vlastnosti, namísto vytváření hodnota výčtu. Logické vlastnosti umožňují kontrolovat každý podmíněné, spíše než by bylo potřeba použít masky pro hodnotu výčtu flagwise získat informace o vás zajímají. Konstruktor používá zřetězených <xref:System.Windows.FrameworkPropertyMetadataOptions> abychom zachovali délka signatury konstruktoru přiměřenou, zatímco skutečná konstruovaný metadat zpřístupní diskrétní vlastnosti provést dotaz na metadata intuitivnější.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Když pro přepis metadat, kdy se má odvodit třídu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vlastnost systém stal možnosti pro změnu některé vlastnosti Vlastnosti závislostí bez nutnosti jejich být zcela znovu implementovaná. Toho dosahuje tak, že vytváří jinou instanci metadat vlastností pro vlastnost závislosti, protože existuje u určitého typu. Mějte na paměti, že nejvíce existující vlastnosti závislosti nejsou virtuální vlastnosti, takže přesněji řečeno "pokaždé znova implementovány" je na zděděné třídy může provést pouze stínováním existujícího člena.  
  
 Pokud tento scénář se pokoušíte povolit pro vlastnost závislosti na typu nelze provést úpravou vlastností vlastností existujícího závislosti, může pak být potřebné k vytvoření odvozené třídy a potom deklarovat vlastnost vlastní závislost v odvozené třídě. Vlastnost vlastní závislosti chová stejně jako vlastnosti závislosti definované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. Další podrobnosti o vlastní vlastnosti závislosti najdete v tématu [vlastní vlastnosti závislosti](custom-dependency-properties.md).  
  
 Jeden významné charakteristiky, které nelze přepsat vlastnost závislosti je její typ hodnoty. Pokud se dědí vlastnost závislosti, approximate chování budete potřebovat, ale vyžadují jiný typ, budete muset implementovat vlastní závislost vlastnost a možná vlastnosti prostřednictvím převodu typu nebo jiné propojení implementace na vaše vlastní třídy. Kromě toho nelze nahradit stávající <xref:System.Windows.ValidateValueCallback>, protože tato zpětné volání existuje v samotné pole registrace a není v rozsahu jeho metadata.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Scénáře pro změnu stávajících metadat  
 Při práci s metadaty existující vlastnost závislosti, chcete-li změnit výchozí hodnota je jeden běžný scénář pro změnu metadata vlastností závislosti. Změna nebo přidání zpětná volání vlastností systému je pokročilejších scénářích. Můžete to provést, pokud vaše implementace odvozená třída má různé vztahy mezi vlastnosti závislosti. Jednou z podmíněné výrazy nutnosti programovací model, který podporuje kód a deklarativní využití je, že vlastnosti musíte povolit, která je nastavena v libovolném pořadí. Proto všechny závislé vlastnosti potřeba nastavit just-in-time bez kontextu a nelze spoléhat na vědomím, že nastavení pořadí může být nalezen, jako v konstruktoru. Další informace o tento aspekt systému vlastností najdete v tématu [vlastnost závislosti zpětné volání a ověření](dependency-property-callbacks-and-validation.md). Všimněte si, že ověření zpětná volání nejsou součástí metadat; jsou součástí identifikátoru vlastnosti závislosti. Zpětná volání ověření proto nelze změnit tak, že přepíšete metadata.  
  
 V některých případech může být také vhodné změnit možnosti metadat vlastnosti na úrovni rozhraní WPF na vlastnosti existujícího závislosti. Tyto možnosti komunikovat o vlastnostech úrovni rozhraní WPF jiným procesům úrovni rozhraní WPF jako je například systém rozložení určité známé podmíněné výrazy.  Nastavení možnosti se obvykle provádí pouze při registraci nové vlastnosti závislosti, ale je také možné změnit metadata vlastnosti na úrovni rozhraní WPF jako součást <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> nebo <xref:System.Windows.DependencyProperty.AddOwner%2A> volání. Konkrétní hodnoty mají použít a další informace najdete v části [Metadata vlastnosti architektury](framework-property-metadata.md). Další informace, které jsou relevantní tyto možnosti by měl být nastavení pro vlastnost závislosti nově zaregistrovaný, naleznete v tématu [vlastní vlastnosti závislosti](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Přepsání metadat  
 Účelem přepsání metadat je primárně, takže budete mít příležitost změnit různé chování odvozených metadat, které jsou použity pro vlastnost závislosti na typu existuje. Důvody jsou vysvětlené podrobněji [metadat](#dp_metadata_contents) oddílu. Další informace včetně některé příklady kódu naleznete v tématu [přepsání metadat pro vlastnost závislosti](how-to-override-metadata-for-a-dependency-property.md).  
  
 Metadata vlastnosti může být zadán pro vlastnost závislosti během volání registrace (<xref:System.Windows.DependencyProperty.Register%2A>). Ale v mnoha případech můžete chtít poskytnout metadata specifická pro typ pro třídu, když dědí vlastnosti závislosti. Toto lze provést zavoláním <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody.  Příklad z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], <xref:System.Windows.FrameworkElement> třída je typ, který se poprvé registruje <xref:System.Windows.UIElement.Focusable%2A> vlastnost závislosti. Ale <xref:System.Windows.Controls.Control> třída přepíše metadata pro vlastnost závislosti definovat vlastní počáteční výchozí hodnotu, změna z `false` k `true`a jinak znovu použije původní <xref:System.Windows.UIElement.Focusable%2A> implementace.  
  
 Při přepsání metadat vlastnosti rozdílná metadata jsou sloučené nebo nahradit.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> se sloučí. Pokud chcete přidat nový <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> povýšen jako odkaz v nejbližším podřízeném objektu, který je zadán v metadatech.  
  
- Skutečné vlastnost chování systému pro <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je, že se zachovají a přidá do tabulky, pomocí pořadí provádění vlastnosti systému, že se zpětná volání nejvíce odvozené třídy jsou vyvolány nejprve implementace pro všechny vlastníky metadat v hierarchii.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> nahrazuje. Pokud nezadáte <xref:System.Windows.PropertyMetadata.DefaultValue%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližším podřízeném objektu, který je zadán v metadatech.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementace se nahradí. Pokud chcete přidat nový <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> povýšen jako odkaz v nejbližším podřízeném objektu, který je zadán v metadatech.  
  
- Chování vlastnosti systému je to jenom <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v metadatech okamžité je vyvolána. Žádné odkazy na další <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementace v hierarchii se zachovají.  
  
 Toto chování je implementováno <xref:System.Windows.PropertyMetadata.Merge%2A>a u tříd odvozených metadat je možné přepsat.  
  
#### <a name="overriding-attached-property-metadata"></a>Přepsání metadat připojené vlastnosti  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojené vlastnosti jsou implementovány jako vlastnosti závislosti. To znamená, že mají také metadata vlastnosti, které jednotlivé třídy můžete přepsat. Aspekty oborů pro připojené vlastnosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou obecně, který všechny <xref:System.Windows.DependencyObject> může mít připojené vlastnosti nastavit na ně. Proto všechny <xref:System.Windows.DependencyObject> může přepsat metadata pro připojené vlastnosti, protože může být nastaveno na instanci třídy. Můžete přepsat výchozí hodnoty, zpětná volání nebo vlastnosti zpráv charakteristiku úrovni rozhraní WPF. Pokud připojená vlastnost nastavená na instanci třídy, ty přepsat vlastnost metadat, platí charakteristiky. Například můžete přepsat výchozí hodnotu tak, aby hodnotu pro přepisování je ohlášeny jako hodnotu přidruženou vlastnost instance třídy, vždy, když vlastnost jinak nenastaví.  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Vlastnost není relevantní pro připojené vlastnosti.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Přidání třídy jako vlastníka skupiny existující vlastnost závislosti  
 Třída sám můžete přidat jako vlastníka skupiny, který již byl registrován, pomocí vlastnosti závislosti <xref:System.Windows.DependencyProperty.AddOwner%2A> metody. To umožňuje používat vlastnost závislosti, která byla původně zaregistrována pro jiný typ třídy. Přidání třídy není obvykle odvozené třídy typu, který nejprve zaregistrovat tuto vlastnost závislosti jako vlastník. To efektivně, umožňuje vaší třídy a její odvozené třídy "dědí" na závislost vlastnost implementace bez původního vlastníka třídy a přidávání se ve stejné hierarchii true třídy. Také přidává třídu (a také všechny odvozené třídy) jim pak můžou metadata specifická pro typ pro původní vlastnost závislosti.  
  
 Stejně jako přidávání sama jako vlastník prostřednictvím metody vlastností systému nástroj přidání třída by měla deklarovat další veřejné členy sám na sobě aby byla vlastnost závislosti] Úplný účastník v systému vlastností se kódu a kódu s . Třída, která přidá existující vlastnost závislosti má stejné odpovědnosti až na hodnotu vystavení objektový model pro danou vlastnost závislosti, stejně jako třídy, která definuje novou vlastnost vlastní závislost. První je tento člen vystavit pole identifikátoru vlastnosti závislosti. Toto pole musí mít `public static readonly` pole typu <xref:System.Windows.DependencyProperty>, která je přiřazená vrácenou hodnotu <xref:System.Windows.DependencyProperty.AddOwner%2A> volání. Je druhý člen definovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost "zabezpečenou obálku". Obálka je to mnohem více vhodné k manipulaci s vaší vlastnost závislosti v kódu (byste se vyhnout volání <xref:System.Windows.DependencyObject.SetValue%2A> každý čas a můžete provést toto volání pouze jednou v samotné obálky). Obálka identicky implementované tak, aby jak ho by implementovat Pokud se registrace vlastnost vlastní závislosti. Další informace o implementaci vlastnost závislosti, naleznete v tématu [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [přidání typu vlastníka pro vlastnost závislosti](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner a připojené vlastnosti  
 Můžete volat <xref:System.Windows.DependencyProperty.AddOwner%2A> pro vlastnost závislosti, který je definován jako připojené vlastnosti třídy vlastníka. Důvod pro to je obvykle zveřejnit předtím připojená vlastnost jako vlastnost závislosti nepřipojené. Pak bude vystavovat <xref:System.Windows.DependencyProperty.AddOwner%2A> vrátí hodnotu jako `public static readonly` pole pro použití jako identifikátor vlastnosti závislostí a definovat vlastnosti příslušné "obálky" tak, aby vlastnost se zobrazí v tabulce členů a podporuje nepřipojené vlastnosti využití ve své třídě.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastnosti architektury](framework-property-metadata.md)
