---
title: Atributy CLR související s jazykem XAML pro vlastní typy a knihovny
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a264ec3fa1232a058a3bfbabbe8b84712cf87322
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956414"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributy CLR související s jazykem XAML pro vlastní typy a knihovny
Toto téma popisuje atributy modulu CLR (Common Language Runtime), které jsou definovány pomocí .NET Framework služby XAML. Popisuje také jiné atributy CLR, které jsou definovány v .NET Framework, které mají scénář související s XAML pro aplikaci do sestavení nebo typů. Přizpůsobování sestavení, typů nebo členů pomocí těchto atributů CLR poskytuje typy informací o systému typu XAML, které souvisejí s vašimi typy. Informace jsou k dispozici libovolnému spotřebiteli XAML, který používá .NET Framework služby XAML pro zpracování datového proudu uzlu XAML přímo nebo prostřednictvím vyhrazeného čtecího modulu XAML a zapisovače XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributy CLR související s jazykem XAML pro vlastní typy a vlastní členy  
 Použití atributů CLR znamená, že k definování typů používáte celkový CLR, jinak takové atributy nejsou k dispozici. Použijete-li modul CLR k definování typu back-Type, pak výchozí kontext schématu XAML používaný .NET Framework moduly XAML pro kódování XAML může číst prohlášení CLR prostřednictvím reflexe proti záložním sestavením.  
  
 Následující části popisují atributy související s jazykem XAML, které lze použít na vlastní typy nebo vlastní členy. Každý atribut CLR komunikuje s informacemi, které jsou relevantní pro systém typů XAML. V cestě načtení se s atributy postaví informace buď pomocí čtečky XAML, na platný datový proud uzlu XAML, nebo pomáhá zapisovači XAML vytvořit platný graf objektů. V cestě pro uložení se atributy pomůžou považovat za čtecí modul XAML a vytvoří platný datový proud uzlu XAML, který rekládá systémové informace typu XAML. nebo deklaruje pomocné parametry nebo požadavky na serializaci pro zapisovač XAML nebo jiné příjemce XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Platí pro:** Třída, vlastnost nebo `get` členové přistupujícího objektu, kteří podporují připojitelné vlastnosti.  
  
 **Náhodné** Žádné  
  
 <xref:System.Windows.Markup.AmbientAttribute>označuje, že vlastnost nebo všechny vlastnosti, které přijímají typ s atributy, by měly být interpretovány v konceptu ambientních vlastností v jazyce XAML. Ambientní pojem se vztahuje na to, jak procesory XAML určují typ vlastníci členů. Ambientní vlastnost je vlastnost, kde je očekávána hodnota v kontextu analyzátoru při vytváření grafu objektů, ale v případě, že typický typ – vyhledávání členů je pozastaveno pro vytvoření okamžité sady uzlů jazyka XAML.  
  
 Ambientní koncept lze použít na připojitelné členy, které nejsou reprezentovány jako vlastnosti z hlediska způsobu, jakým definuje <xref:System.AttributeTargets>autor CLR. Použití metody, která se má použít, by mělo být použito pouze v `get` případě přístupového objektu, který podporuje připojitelné použití pro XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Řetězec, který určuje název vlastnosti, která odpovídá jednomu argumentu konstruktoru.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Určuje, že objekt lze inicializovat pomocí syntaxe konstruktoru bez parametrů a zda vlastnost zadaného názvu dodává informace o konstrukci. Tyto informace jsou primárně určeny pro serializaci XAML. Další informace naleznete v tématu <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>Třída ContentPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Řetězec, který určuje název členu typu s atributy.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>označuje, že vlastnost pojmenovaná argumentem by měla sloužit jako vlastnost obsahu XAML pro daný typ. Definice vlastnosti obsahu XAML dědí na všechny odvozené typy, které lze přiřadit k definičnímu typu. Můžete přepsat definici konkrétního odvozeného typu <xref:System.Windows.Markup.ContentPropertyAttribute> použitím pro konkrétní odvozený typ.  
  
 Pro vlastnost, která slouží jako vlastnost obsahu XAML, lze tagování elementu vlastnosti pro vlastnost vynechat v použití XAML. Obvykle určíte vlastnosti obsahu XAML, které podporují zjednodušený kód XAML pro váš obsah a modely zahrnutí. Vzhledem k tomu, že pouze jeden člen může být určen jako vlastnost obsahu XAML, někdy máte možnost navrhovat volby, které mají být určeny pro to, které z několika vlastností kontejneru typu by měly být označeny jako vlastnost obsahu XAML. Ostatní vlastnosti kontejneru musí být použity s explicitními prvky vlastností.  
  
 V datovém proudu uzlu XAML stále `StartMember` vytváření a `EndMember` uzly vlastností obsahu XAML používá název vlastnosti pro <xref:System.Xaml.XamlMember>. Chcete-li zjistit, zda je členem vlastnost obsahu XAML, zkontrolujte <xref:System.Xaml.XamlType> hodnotu `StartObject` z pozice <xref:System.Xaml.XamlType.ContentProperty%2A>a získejte hodnotu.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Platí pro:** Třída, konkrétně typy kolekcí.  
  
 **Náhodné** A <xref:System.Type> určuje typ, který má být použit jako typ obálky obsahu pro cizí obsah.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Určuje jeden nebo více typů pro přidružený typ kolekce, který bude použit k zabalení cizího obsahu. Cizí obsah odkazuje na případy, kdy omezení typu systému na typ vlastnosti Content nezachycují všechny možné případy obsahu, které by použití XAML pro vlastnící typ podporovalo. Například podpora jazyka XAML pro obsah konkrétního typu může podporovat řetězce ve silně typované obecné <xref:System.Collections.ObjectModel.Collection%601>. Obálky obsahu jsou užitečné pro migraci stávajících konvencí pro psaní kódu do nejvyšší hodnoty přiřazení pro kolekce v jazyce XAML, jako je například migrace modelů obsahu souvisejících s textem.  
  
 Chcete-li zadat více než jeden typ obálky obsahu, použijte atribut několikrát.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Platí pro:** Vlastnost  
  
 **Náhodné** Řetězec, který určuje název jiného člena typu s atributy.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>označuje, že vlastnost s atributy závisí na hodnotě jiné vlastnosti. Použití tohoto atributu na definici vlastnosti zajišťuje, aby závislé vlastnosti byly zpracovány jako první v zápisu objektu XAML. Použití lze určit výjimečné případy vlastností u typů, kde konkrétní pořadí analýzy musí následovat za účelem platného vytvoření objektu. <xref:System.Windows.Markup.DependsOnAttribute>  
  
 Můžete použít více <xref:System.Windows.Markup.DependsOnAttribute> případů na definici vlastnosti.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Platí pro:** Třída, která by měla být <xref:System.Windows.Markup.MarkupExtension> odvozeným typem.  
  
 **Náhodné** Který určuje nejpřesnější typ, který má `ProvideValue` <xref:System.Windows.Markup.MarkupExtension>být očekáván jako výsledek atributu. <xref:System.Type>  
  
 Další informace naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Podporuje dva formy přidělení:  
  
- Řetězec, který určuje název vlastnosti u typu s atributy.  
  
- Řetězec, který určuje název vlastnosti, a <xref:System.Type> pro typ, který definuje pojmenovanou vlastnost. Tento formulář slouží k zadání připojeného člena jako vlastnosti namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Určuje vlastnost, která poskytuje hodnotu namescope XAML pro třídu s atributy. Očekává se, že vlastnost namescope XAML odkazuje na objekt, který <xref:System.Windows.Markup.INameScope> implementuje a obsahuje skutečný namescope XAML, jeho úložiště a chování.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Řetězec určující název vlastnosti název běhu u typu s atributy.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>oznamuje vlastnost typu s atributem, který se mapuje na direktivu [x:Name](x-name-directive.md)jazyka XAML. Vlastnost musí být typu <xref:System.String> a musí být určena pro čtení i zápis.  
  
 Definice dědí na všechny odvozené typy, které lze přiřadit k definičnímu typu. Můžete přepsat definici konkrétního odvozeného typu <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> použitím pro konkrétní odvozený typ.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Platí pro:** Typy  
  
 **Náhodné** Žádné  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>je použita na konkrétní typy, které se mohou zobrazit jako podřízené prvky v rámci významného obsahu (obsah uložený v kolekci, <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>která má). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>je hlavně relevantní pro cestu pro uložení, ale je k dispozici v systému typů XAML v cestě zatížení prozkoumáním <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Další informace naleznete v tématu [prázdné místo zpracování v jazyce XAML](whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Referenční dokumentace:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Platí pro:** Třída, vlastnost, metoda (jediný parametr, který je platný pouze v jazyce `get` XAML, je přístupový objekt, který podporuje člena, který lze připojit).  
  
 **Náhodné** <xref:System.Type> z <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>v kontextu XAML odkazuje na vlastní <xref:System.ComponentModel.TypeConverter>. To <xref:System.ComponentModel.TypeConverter> poskytuje chování převodu typů pro vlastní typy nebo členy tohoto typu.  
  
 Aplikujete <xref:System.ComponentModel.TypeConverterAttribute> atribut na typ a odkazuje na implementaci konvertoru typu. Můžete definovat konvertory typů pro jazyk XAML pro třídy, struktury nebo rozhraní. Pro výčty není nutné zadávat převod typu, tento převod je povolen nativně.  
  
 Konvertor typu by měl být schopný převést z řetězce, který se používá pro atributy nebo inicializační text v kódu, do zamýšleného cílového typu. Další informace naleznete v tématu [TypeConverters a XAML](../wpf/advanced/typeconverters-and-xaml.md).  
  
 Namísto použití na všechny hodnoty typu může být pro konkrétní vlastnost také vytvořeno chování konvertoru typu pro XAML. V takovém případě se použije <xref:System.ComponentModel.TypeConverterAttribute> na definici vlastnosti (vnější definice, nikoli na konkrétní `get` definice a `set` definice).  
  
 Chování konvertoru typu pro použití jazyka XAML vlastního přistupujícího člena lze přiřadit pomocí <xref:System.ComponentModel.TypeConverterAttribute> `get` přístupového objektu metody, který podporuje použití XAML.  
  
 Podobně jako v .NET Framework existovaly před existencí kódu XAML a model konvertoru typu obsluhuje jiné účely. <xref:System.ComponentModel.TypeConverterAttribute> <xref:System.ComponentModel.TypeConverter> Aby bylo možné odkazovat a používat <xref:System.ComponentModel.TypeConverterAttribute>, musíte je plně kvalifikovat nebo `using` poskytnout příkaz pro <xref:System.ComponentModel>. Do projektu musíte také zahrnout systémové sestavení.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Řetězec, který odkazuje na příslušnou vlastnost podle názvu.  
  
 Určuje vlastnost CLR třídy, která je aliasem [direktivy x:UID –](x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Logická hodnota. Pokud se používá pro zamýšlený účel atributu, mělo by být vždy zadáno jako `true`.  
  
 Určuje, zda je tento typ během vytváření grafu objektů XAML sestaven nahoru. Toto je pokročilý koncept, který je pravděpodobně úzce spojen s definicí programovacího modelu. Další informace naleznete v tématu <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Platí pro:** Třída, vlastnost, metoda (jediný parametr, který je platný pouze v jazyce `get` XAML, je přístupový objekt, který podporuje člena, který lze připojit).  
  
 **Náhodné** <xref:System.Type> Který určuje, že serializátor hodnoty podporuje třídu, která se má použít při serializaci všech vlastností typu s atributy nebo konkrétní vlastnost s atributy.  
  
 <xref:System.Windows.Markup.ValueSerializer>Určuje třídu serializace hodnoty, která vyžaduje více stavů a kontextu <xref:System.ComponentModel.TypeConverter> , než má. <xref:System.Windows.Markup.ValueSerializer>lze přidružit k připojenému členu <xref:System.Windows.Markup.ValueSerializerAttribute> použitím atributu u metody statického `get` přístupového objektu pro připojeného člena. Serializace hodnot je také platná pro výčty, rozhraní a struktury, ale ne pro delegáty.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Platí pro:** Třída, konkrétně typy kolekcí, které jsou očekávány pro hostování smíšeného obsahu, kde prázdné znaky kolem prvků objektu mohou být významné pro reprezentaci uživatelského rozhraní.  
  
 **Náhodné** Žádné  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>označuje, že typ kolekce by měl být zpracován jako prázdné místo, které je významné pro procesor XAML, což ovlivňuje konstrukci uzlů hodnot datového proudu uzlu XAML v rámci kolekce. Další informace naleznete v tématu [prázdné místo zpracování v jazyce XAML](whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Platí pro:** Třída, vlastnost.  
  
 **Náhodné** Podporuje dva typy forem přiřazení jako řetězce nebo typy jako <xref:System.Type>. Viz <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Označuje, že třída nebo vlastnost má odložené použití načtení pro XAML (například chování šablony), a hlásí třídu, která umožňuje odložení chování a jeho cíl nebo typ obsahu.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Pojmenuje zpětné volání.  
  
 Označuje, že třída může použít rozšíření značek k poskytnutí hodnoty pro jednu nebo více jeho vlastností a odkazuje na obslužnou rutinu, kterou by měl před provedením operace set rozšíření značek volat modul pro zápis kódu na jakoukoliv vlastnost třídy.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Pojmenuje zpětné volání.  
  
 Označuje, že třída může použít konvertor typu k poskytnutí hodnoty pro jednu nebo více jejích vlastností a odkazuje na obslužnou rutinu, kterou by měl zapisovač XAML volat před provedením operace sady konvertoru typu u libovolné vlastnosti třídy.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Platí pro:** Třída  
  
 **Náhodné** Řetězec, který určuje název vlastnosti, na kterou má alias `xml:lang` přihlášený typ s atributem.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>oznamuje vlastnost typu s atributem, který se mapuje na direktivu `lang` XML. Vlastnost není nutně typu <xref:System.String>, ale musí být přizpůsobena z řetězce (to lze provést přidružením konvertoru typu s typem vlastnosti nebo s konkrétní vlastností). Vlastnost musí být pro čtení i zápis.  
  
 Scénář pro mapování `xml:lang` je tak, aby běhový objektový model měl přístup k informacím jazyka XML, a to bez konkrétního zpracování pomocí XMLDOM.  
  
 Definice dědí na všechny odvozené typy, které lze přiřadit k definičnímu typu. Definici pro konkrétní odvozený typ můžete přepsat použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> konkrétního odvozeného typu, přestože to je neobvyklý scénář.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributy CLR související s jazykem XAML na úrovni sestavení  
 Následující části popisují atributy související s jazykem XAML, které nejsou aplikovány na typy nebo definice členů, ale jsou místo toho aplikovány na sestavení. Tyto atributy jsou relevantní pro celkový cíl definování knihovny, která obsahuje vlastní typy pro použití v jazyce XAML. Některé atributy nemusí nutně ovlivnit datový proud uzlu XAML přímo, ale jsou předány v datovém proudu uzlu, aby je mohli používat jiní uživatelé. Mezi příjemce pro tyto informace patří návrhová prostředí nebo procesy serializace, které potřebují informace o oboru názvů XAML a související informace o předponě. Tyto informace používá kontext schématu XAML (včetně výchozích .NET Framework služby XAML).  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Náhodné**  
  
- Řetězec, který určuje identifikátor oboru názvů XAML pro začlenění.  
  
- Řetězec, který určuje identifikátor oboru názvů XAML, který může začlenění obor názvů XAML z předchozího argumentu.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Určuje, že obor názvů XAML může být subsumed jiným oborem názvů XAML. Obor názvů XAML subsuming je obvykle uveden v dříve definovaném <xref:System.Windows.Markup.XmlnsDefinitionAttribute>typu. Tento postup lze použít pro správu verzí slovníku XAML v knihovně a pro zajištění jeho kompatibility s dříve definovaným označením ve slovníku starší verze.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Náhodné**  
  
- Řetězec, který určuje identifikátor oboru názvů jazyka XAML, který má být definován.  
  
- Řetězec, který má název oboru názvů CLR. Obor názvů CLR by měl definovat veřejné typy v sestavení a nejméně jeden z typů oborů názvů CLR by měl být určen pro použití v jazyce XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Určuje mapování na základě sestavení mezi oborem názvů XAML a oborem názvů CLR, který je pak použit pro rozlišení typu pomocí kontextu zapisovače objektu XAML nebo kontextu schématu XAML.  
  
 Pro sestavení lze <xref:System.Windows.Markup.XmlnsDefinitionAttribute> použít více než jeden. To může být provedeno v jakékoli kombinaci následujících důvodů:  
  
- Návrh knihovny obsahuje několik oborů názvů CLR pro logickou organizaci přístupu běhového rozhraní API. Nicméně chcete, aby všechny typy v těchto oborech názvů byly použitelné pro XAML odkazem na stejný obor názvů XAML. V takovém případě použijete několik <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributů se stejnou <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnotou, ale s <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> různými hodnotami. To je užitečné hlavně v případě, že definujete mapování pro obor názvů jazyka XAML, který vaše architektura nebo aplikace považují za výchozí obor názvů XAML při běžném použití.  
  
- Návrh knihovny obsahuje několik oborů názvů CLR a v těchto oborech názvů CLR chcete mít záměrné obory názvů XAML mezi využitím typů.  
  
- Definujete obor názvů CLR v sestavení a chcete, aby byl přístupný prostřednictvím více než jednoho oboru názvů XAML. K tomuto scénáři dochází, Pokud podporujete více slovníků se stejným základem kódu.  
  
- Můžete definovat podporu jazyka XAML v jednom nebo více oborech názvů CLR. Pro tyto <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnoty by měla být `http://schemas.microsoft.com/winfx/2006/xaml`hodnota.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Náhodné**  
  
- Řetězec, který určuje identifikátor oboru názvů XAML.  
  
- Řetězec, který určuje doporučenou předponu.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Určuje doporučenou předponu, která se má použít pro obor názvů XAML. Tato předpona je užitečná při psaní prvků a atributů v souboru XAML, který je serializován pomocí služby <xref:System.Xaml.XamlXmlWriter>.NET Framework XAML, nebo když knihovna implementující XAML spolupracuje s návrhovým prostředím, které obsahuje funkce pro úpravu XAML.  
  
 Pro sestavení lze <xref:System.Windows.Markup.XmlnsPrefixAttribute> použít více než jeden. To může být provedeno v jakékoli kombinaci následujících důvodů:  
  
- Sestavení definuje typy pro více než jeden obor názvů XAML. V takovém případě byste měli definovat jiné hodnoty předpony pro každý obor názvů XAML.  
  
- Podporujete více slovníků a používáte různé předpony pro každý slovník a obor názvů XAML.  
  
- Definujete podporu jazyka XAML v sestavení a máte <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pro. `http://schemas.microsoft.com/winfx/2006/xaml` V takovém případě byste obvykle měli propagovat předponu `x`.  
  
> [!NOTE]
> .NET Framework služby XAML také definují atribut <xref:System.Windows.Markup.RootNamespaceAttribute>související s jazykem XAML. Tento atribut je atribut na úrovni sestavení pro podporu systému projektu a není relevantní pro vlastní typy XAML.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Attribute>
- [Definování vlastních typů pro práci s technologií .NET Framework XAML Services](defining-custom-types-for-use-with-net-framework-xaml-services.md)
