---
title: Atributy CLR související s jazykem XAML pro vlastní typy a knihovny
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 13cc4d85a1a4b5c9b1ff61afbf7980a54e3d22d0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563641"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributy CLR související s jazykem XAML pro vlastní typy a knihovny
Toto téma popisuje běžné atributy modulu runtime (CLR) jazyka, které jsou definovány pomocí rozhraní .NET Framework XAML Services. Popisuje také další atributy CLR, které jsou definovány v rozhraní .NET Framework, které mají související s XAML scénář pro aplikaci na sestavení nebo typy. Přidělování sestavení, typy nebo členy s těmito atributy CLR poskytuje typ informace o systému XAML souvisejících typů. Informace jsou poskytovány k příjemci XAML, který používá rozhraní .NET Framework XAML Services pro zpracování datový proud uzlu XAML přímo nebo prostřednictvím vyhrazené XAML čtečky a zapisovače XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributy CLR související s jazykem XAML pro vlastní typy a členy, vlastní  
 Pomocí atributů CLR má za následek, že používáte celkové CLR k definování typů, jinak tyto atributy nejsou k dispozici. Pokud používáte modul CLR k definování typu zálohování, může číst výchozí kontext schématu XAML používá rozhraní .NET Framework XAML Services XAML zapisovače attribution CLR prostřednictvím reflexe proti zálohování sestavení.  
  
 Následující části popisují atributy související s XAML, které můžete použít pro vlastní typy nebo členy vlastní. Jednotlivé atributy CLR komunikuje informace, které jsou relevantní pro systém typů XAML. V cestě zatížení s atributy informace buď pomáhá čtečky XAML tvoří platný datový proud uzlu XAML nebo pomáhá zapisovač XAML vytvořit platný objekt grafu. V poli Uložit cestu, s atributy informace buď pomáhá čtečky XAML tvoří platný datový proud uzlu XAML, který reconstitutes informace o typu systému XAML; nebo deklaruje pomocné parametry serializace nebo požadavky na zápis XAML nebo ostatní uživatelé XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Platí pro:** třídy, vlastnosti, nebo `get` přistupující členy, které podporují připojitelná vlastnosti.  
  
 **Argumenty:** None  
  
 <xref:System.Windows.Markup.AmbientAttribute> Označuje, že vlastnost nebo všechny vlastnosti, které provést s atributy typu by měl být interpretován pod vedlejší vlastnost koncept v XAML. Okolí koncept se vztahuje jak XAML procesory určit vlastníky typ členů. Změní vlastnost ambient je vlastnost, kde se očekává, že hodnota bude k dispozici v rámci analyzátor při vytváření grafu objektů, ale v případě vyhledávání typický typ člena je pozastaven okamžité uzlu XAML nastavit vytváří.  
  
 Ambientní koncept lze použít u připojitelná členy, které nejsou reprezentovány jako vlastnosti z hlediska jak definuje CLR attribution <xref:System.AttributeTargets>. Použití metody přidělení bude použito pouze v případě třídy `get` přístupový objekt, který podporuje připojitelná využití pro XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** řetězec, který určuje název vlastnosti, která odpovídá v něm argument jediný konstruktor.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> Určuje, že lze objekt inicializovat pomocí syntaxe jiného než výchozího konstruktoru. proto, že vlastnost se zadaným názvem poskytuje informace o vytváření. Tyto informace jsou primárně pro serializaci XAML. Další informace naleznete v tématu <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>Třída ContentPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** řetězec, který určuje název člena s atributy typu.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> znamená, že vlastnost pojmenovaného argumentu by měla sloužit jako vlastnost XAML pro daný typ obsahu. Vlastnost obsahu definice XAML zdědí všechny odvozené typy, které jsou přiřadit k definování typu. Definice na konkrétní odvozený typ může přepsat s použitím <xref:System.Windows.Markup.ContentPropertyAttribute> na konkrétní odvozeného typu.  
  
 Pro vlastnost, která slouží jako vlastnost obsahu XAML můžete vynechat property – element pro vlastnost označování využití XAML. Obvykle stanovíte vlastnosti obsahu XAML, které podporují zjednodušené značky XAML pro modely obsahu a členství ve skupině. Protože pouze jednoho člena lze označit jako vlastnost obsahu XAML, máte někdy možnosti návrhu pro Ujistěte se, díky kterým několik kontejner vlastnosti typu by měla být určena jako vlastnost obsahu XAML. Vlastnosti kontejneru musí použít s prvky explicitní vlastnost.  
  
 V datovém proudu uzlu XAML vlastnosti obsahu XAML stále vytvářejí `StartMember` a `EndMember` uzly, název vlastnosti pro použití <xref:System.Xaml.XamlMember>. Pokud chcete zjistit, zda je člen vlastnost obsahu XAML, zkontrolujte <xref:System.Xaml.XamlType> hodnotu z `StartObject` umístěte a získat výhody <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Platí pro:** třídy, konkrétně typů kolekce.  
  
 **Argumenty:** A <xref:System.Type> , který určuje typ, který má používat jako typ obsahu obálky cizí obsahu.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> Určuje jeden nebo více typů na přiřazené kolekce typu, který se použije při zabalení cizí obsah. Cizí obsah odkazuje na případy, kde systém omezeními typu na typ obsahu vlastnosti nezachytí všechny možné obsahu případy, které by podporují použití XAML pro vlastnícího typu. Například podporovat XAML pro obsah určitého typu může podporovat řetězce v silného typu obecného <xref:System.Collections.ObjectModel.Collection%601>. Obálky obsahu jsou užitečné při migraci stávající konvence kódu do vaší XAML koncepci Přiřaditelné hodnoty pro kolekce, jako je migrace, související s textem modely obsahu.  
  
 Chcete-li zadat více než jeden typ obsahu obálky, použijte atribut více než jednou.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Platí pro:** vlastnost  
  
 **Argumenty:** řetězec určující název jiného člena s atributy typu.  
  
 <xref:System.Windows.Markup.DependsOnAttribute> Označuje, že vlastnost s atributy závisí na hodnotě jiné vlastnosti. Použití tohoto atributu na definici vlastnosti zajistí, že závislé vlastnosti jsou zpracovány nejprve v zápisu objektu XAML. Použití <xref:System.Windows.Markup.DependsOnAttribute> zadejte výjimečných případech vlastnosti na typy, kde musí být následován konkrétní pořadí analýzy pro vytvoření objektu platný.  
  
 Můžete použít více <xref:System.Windows.Markup.DependsOnAttribute> případy definici vlastnosti.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Platí pro:** třídu, která má být <xref:System.Windows.Markup.MarkupExtension> odvozeného typu.  
  
 **Argumenty:** A <xref:System.Type> , který určuje typ nejpřesnější očekávat jako `ProvideValue` výsledek s atributy <xref:System.Windows.Markup.MarkupExtension>.  
  
 Další informace najdete v tématu [– rozšíření značek XAML přehled](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** podporuje dvě formy autorství:  
  
-   Řetězec, který určuje název vlastnosti v typu s atributy.  
  
-   Řetězec, který určuje název vlastnosti a s <xref:System.Type> pro typ, který definuje vlastnost s názvem. Tento formulář slouží k určení připojitelný člen jako vlastnost namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> Určuje vlastnost, která obsahuje hodnotu namescope XAML pro třídu s atributy. Vlastnost obor namescope XAML má odkazovat na objekt, který implementuje <xref:System.Windows.Markup.INameScope> a obsahuje skutečný obor namescope XAML, ukládání a její chování.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** řetězec, který určuje název vlastnosti názvu za běhu s atributy typu.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> sestavy vlastnost s atributy typu, který se mapuje XAML [x: Name – direktiva](../../../docs/framework/xaml-services/x-name-directive.md). Vlastnost musí být typu <xref:System.String> a musí být pro čtení a zápisu.  
  
 Definice zdědí všechny odvozené typy, které jsou přiřadit k definování typu. Definice na konkrétní odvozený typ může přepsat s použitím <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> na konkrétní odvozeného typu.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Platí pro:** typy  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> platí pro konkrétní typy, které se zobrazují jako podřízené prvky v rámci prázdné místo důležité obsahu (obsah drží kolekce, která má <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> především vztahující se k uložení cesty, ale je k dispozici v systému typů XAML v cestě zatížení prozkoumáním <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Další informace najdete v tématu [– zpracování mezerových znaků v XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Referenční dokumentace:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Platí pro:** třídy, vlastnosti, metody (pouze XAML platná metoda případem je `get` přístupový objekt, který podporuje připojitelný člen).  
  
 **Argumenty:** <xref:System.Type> z <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute> v XAML kontext odkazuje na vlastní <xref:System.ComponentModel.TypeConverter>. To <xref:System.ComponentModel.TypeConverter> poskytuje chování převodu typu pro vlastní typy nebo členy tohoto typu.  
  
 Můžete použít <xref:System.ComponentModel.TypeConverterAttribute> atribut pro váš typ odkazování na vaší implementace převodníku typů. Převaděče typů pro XAML můžete definovat na třídy, struktury nebo rozhraní. Není potřeba poskytovat převod typů výčtů, nativně povolen převod.  
  
 Váš typ převaděče měli být schopni převést z řetězce, který se používá pro atributy nebo inicializace text v kódu, do vašeho typu požadovaného cíle. Další informace najdete v tématu [TypeConverters a XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Nejsou implementovány všechny hodnoty typu, ale typ převaděče chování pro XAML můžete také navázat na specifickou vlastnost. V tomto případě použijete <xref:System.ComponentModel.TypeConverterAttribute> v definici vlastnosti (vnějšího definice, nikoli konkrétní `get` a `set` definic).  
  
 Je možné přiřadit typ převaděč chování pro XAML využití vlastních připojitelný člen použitím <xref:System.ComponentModel.TypeConverterAttribute> k `get` metoda přístupový objekt, který podporuje použití XAML.  
  
 Podobně jako <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existoval v rozhraní .NET Framework před existenci XAML a model konvertor typu obsluhovat jiným účelům. Aby bylo možné odkazovat a využívat <xref:System.ComponentModel.TypeConverterAttribute>, musí plně kvalifikujte jej nebo poskytovat `using` příkaz pro <xref:System.ComponentModel>. Systémové sestavení je také nutné uvést ve vašem projektu.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** řetězec, který odkazuje na odpovídající vlastnosti podle názvu.  
  
 Označuje vlastnost CLR třídy, že aliasy [x: Uid – direktiva](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** logickou hodnotu. Pokud používá pro zamýšlený účel atributu, to by měl vždy být zadána jako `true`.  
  
 Určuje, zda tento typ je sestavena shora dolů při vytváření grafu objektu XAML. Toto je pokročilé koncept, což je pravděpodobně úzce souvisí s definice programovací model. Další informace naleznete v tématu <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Platí pro:** třídy, vlastnosti, metody (pouze XAML platná metoda případem je `get` přístupový objekt, který podporuje připojitelný člen).  
  
 **Argumenty:** A <xref:System.Type> , který určuje hodnotu serializátoru pomocná třída pro použití při serializaci všechny vlastnosti typu s atributy, nebo s konkrétní atributy vlastnosti.  
  
 <xref:System.Windows.Markup.ValueSerializer> Určuje, který vyžaduje další stav a kontext než třída serializace hodnotu <xref:System.ComponentModel.TypeConverter> nepodporuje. <xref:System.Windows.Markup.ValueSerializer> můžou být spojené s připojitelný člen použitím <xref:System.Windows.Markup.ValueSerializerAttribute> atribut na statické `get` přístupové metody pro připojitelný člen. Hodnota serializace platí i pro výčty a struktury a rozhraní, ale ne pro delegáty.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Platí pro:** třídy, specificky typy kolekce, kteří budou hostovat smíšený obsah, kde mezery okolo objektu prvků může být důležité pro reprezentaci uživatelského rozhraní.  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> Označuje, že typ kolekce má být zpracován jako prázdné místo důležité procesorem XAML, který ovlivňuje konstrukce uzly hodnot datový proud uzlu XAML v rámci kolekce. Další informace najdete v tématu [– zpracování mezerových znaků v XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Platí pro:** třídy, vlastnosti.  
  
 **Argumenty:** attribution podporuje dva typy jako řetězce forms nebo typy jako <xref:System.Type>. Zobrazit <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Označuje, že je třída nebo vlastnost má odloženého načtení využití pro XAML (například šablony chování) a sestavy umožňující odložení chování a jeho cílové nebo obsah typu třídy.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** názvy zpětného volání.  
  
 Označuje, že rozšíření značek můžete zadat hodnotu pro jeden nebo více vlastností třídy a odkazuje na obslužnou rutinu, která zapisovač XAML by měly volat před provedením operace set rozšíření značek jakékoli vlastnosti třídy.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** názvy zpětného volání.  
  
 Označuje, že třída slouží k zadání hodnoty pro jeden nebo více vlastností konvertor typu a odkazuje na obslužnou rutinu, která zapisovač XAML by měly volat před provedením operace set konvertor typu jakékoli vlastnosti třídy.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Platí pro:** třídy  
  
 **Argumenty:** řetězec, který určuje název vlastnosti, která má alias `xml:lang` s atributy typu.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> sestavy vlastnost s atributy typu, který se mapuje XML `lang` směrnice. Vlastnost není typu nutně <xref:System.String>, ale musí být přiřaditelný z řetězce (toho je možné dosáhnout přidružením konvertoru typu s typem vlastnosti nebo s konkrétní vlastnost). Vlastnost musí být pro čtení a zápisu.  
  
 Scénáře pro mapování `xml:lang` je tak, aby objektového modelu runtime měl přístup k informacím o jazyk XML určuje jazyk bez konkrétně zpracování ve službě XMLDOM.  
  
 Definice zdědí všechny odvozené typy, které jsou přiřadit k definování typu. Definice na konkrétní odvozený typ může přepsat s použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> na konkrétní odvozený typ, i když se běžné scénáře.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributy CLR související s jazykem XAML na úrovni sestavení  
 Následující části popisují atributy související s XAML, které nejsou u typů nebo definice členů, ale místo toho se použijí pro sestavení. Tyto atributy se vztahují k celkovému cíli definování knihovnu, která obsahuje vlastní typy, které se použijí v XAML. Některé atributy nejsou nutně vliv datový proud uzlu XAML přímo, ale jsou předány v datovém proudu uzlu pro ostatní uživatelé používat. Příjemci informace zahrnují vybavená vývojová prostředí nebo serializace procesy, které potřebují informace oboru názvů XAML a přidružené informace předponu. XAML schématu kontextu (včetně výchozí rozhraní .NET Framework XAML Services) také použije tyto informace.  
  
### <a name="xmlnscompatiblewithattribute"></a>Atribut XmlnsCompatibleWithAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumenty:**  
  
-   Řetězec určující identifikátor oboru názvů XAML k začlenění.  
  
-   Řetězec určující identifikátor oboru názvů XAML, který může začlenění obor názvů XAML z předchozí argument.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> Určuje, že obor názvů XAML může subsumed pomocí jiného oboru názvů XAML. Obvykle je označeno subsuming oboru názvů XAML v dříve definované <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Tento postup lze použít pro správu verzí slovník jazyka XAML v knihovně a aby byl kompatibilní s dříve definované značky proti dříve označené verzí slovníku.  
  
### <a name="xmlnsdefinitionattribute"></a>Atributu XmlnsDefinitionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumenty:**  
  
-   Řetězec určující identifikátor oboru názvů XAML k definování.  
  
-   Řetězec, který označuje obor názvů CLR. Obor názvů CLR by měl definovat veřejné typy v sestavení a alespoň jeden obor názvů typů CLR by měla být určený pro použití XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Určuje mapování na základě za sestavení mezi obor názvů XAML a obor názvů CLR, který se pak použije pro rozlišení typ v kontext schématu XAML a XAML objektu zapisovače.  
  
 Více než jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> lze použít k sestavení. To může být provedeno pro jakoukoli kombinaci následujících důvodů:  
  
-   Návrh knihovna obsahuje více oborů názvů CLR pro logické uspořádání přístup přes rozhraní API za běhu; však chcete, aby všechny typy v těchto oborů názvů má být použitelná pro XAML pomocí odkazu na stejný obor názvů XAML. V takovém případě můžete použít několik <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributy, pomocí stejných <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnota ale jiným <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> hodnoty. To je obzvláště užitečné, pokud definujete mapování pro obor názvů XAML, který rozhraní framework vaší aplikace si klade za cíl jako výchozí obor názvů XAML v běžné použití.  
  
-   Návrh knihovna obsahuje více oborů názvů CLR a chcete rozhodnout vědomě a záměrně rozdělení oboru názvů XAML mezi použití typů v těchto oborů názvů CLR.  
  
-   Můžete definovat obor názvů CLR v sestavení a chcete, aby byl přístupný prostřednictvím více než jeden obor názvů XAML. Tento scénář nastane, pokud podporujete více vocabularies pomocí stejného základu kódu.  
  
-   Podpora jazyka XAML definujete v jedné nebo více oborů názvů CLR. Pro ty <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnota by měla být `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>Atributu XmlnsPrefixAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumenty:**  
  
-   Řetězec určující identifikátor oboru názvů XAML.  
  
-   Řetězec, který specifikuje doporučenou předponu.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Určuje doporučené předponu pro obor názvů XAML. Předpona, která je užitečná při vytváření elementů a atributů v souboru XAML, který je serializováno modulem rozhraní .NET Framework XAML Services <xref:System.Xaml.XamlXmlWriter>, nebo když knihovnu implementace XAML komunikuje s prostředím návrhu, který má XAML funkce úprav.  
  
 Více než jeden <xref:System.Windows.Markup.XmlnsPrefixAttribute> lze použít k sestavení. To může být provedeno pro jakoukoli kombinaci následujících důvodů:  
  
-   Vaše sestavení definuje typy pro více než jeden obor názvů XAML. V tomto případě byste měli definovat hodnoty jinou předponu pro každý obor názvů XAML.  
  
-   Podporujete více vocabularies a použít odlišné předpony pro každý slovník a obor názvů XAML.  
  
-   Definujte podpora jazyka XAML v sestavení a nechte <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pro `http://schemas.microsoft.com/winfx/2006/xaml`. V takovém případě je obvykle by měly podporovat předponu `x`.  
  
> [!NOTE]
>  Rozhraní .NET framework XAML Services také definuje atributu souvisejícím s XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Tento atribut je atribut úrovně sestavení pro podpora projektových systémů a není relevantní pro vlastní typy XAML.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Attribute>  
 [Definování vlastních typů pro práci s technologií .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
