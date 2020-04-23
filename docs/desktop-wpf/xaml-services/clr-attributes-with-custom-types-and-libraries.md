---
title: Atributy CLR související s jazykem XAML pro vlastní typy a knihovny
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071764"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributy CLR související s XAML pro vlastní typy a knihovny

Toto téma popisuje atributy CLR (COMMON Language runtime), které jsou definovány službou .NET XAML Services. Popisuje také další atributy CLR, které jsou definovány v rozhraní .NET, které mají scénář související s XAML pro aplikaci na sestavení nebo typy. Přiřazení sestavení, typů nebo členů s těmito atributy CLR poskytuje informace o systému typu XAML související s vašimi typy. Informace jsou poskytovány každému spotřebiteli XAML, který používá služby .NET XAML pro přímé zpracování datového proudu uzlu XAML nebo prostřednictvím vyhrazených čteček XAML a zapisovačů XAML.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributy CLR související s XAML pro vlastní typy a vlastní členy

Použití clr atributy znamená, že používáte celkový CLR definovat typy, jinak tyto atributy nejsou k dispozici. Pokud použijete CLR k definování zálohování typu, pak výchozí kontext schématu XAML používaný zapisovateli XAML services .NET může číst přiřazení CLR prostřednictvím reflexe proti záložním sestavením.

Následující části popisují atributy související s XAML, které můžete použít pro vlastní typy nebo vlastní členy. Každý atribut CLR sděluje informace, které jsou relevantní pro systém typu XAML. V cestě zatížení přiřazené informace buď pomáhá čtečce XAML vytvořit platný datový proud uzlu XAML, nebo pomáhá zapisovateli XAML vytvořit platný objektový graf. V cestě pro uložení přiřazené informace buď pomáhá čtečce XAML vytvořit platný datový proud uzlu XAML, který rekonstituuuje systémové informace typu XAML; nebo deklaruje rady pro serializaci nebo požadavky pro zapisovače XAML nebo jiné spotřebitele XAML.

### <a name="ambientattribute"></a>Atribut AmbientAttribute

**Referenční dokumentace:**<xref:System.Windows.Markup.AmbientAttribute>

**Platí pro:** Členy třídy, `get` vlastnosti nebo přistupujícího objektu, které podporují připojitelné vlastnosti.

**Argumenty:** Žádný

<xref:System.Windows.Markup.AmbientAttribute>označuje, že vlastnost nebo všechny vlastnosti, které berou přiřazený typ, by měly být interpretovány pod konceptem vlastnosti ambient v XAML. Koncept okolí se vztahuje k tomu, jak procesory XAML určují vlastníky typů členů. Ambient vlastnost je vlastnost, kde se očekává, že hodnota bude k dispozici v kontextu analyzátoru při vytváření grafu objektu, ale kde je pro vytvoření okamžité sady uzlů XAML pozastaveno typické vyhledávání členů typu.

Koncept okolí lze použít na připojitelné členy, které nejsou reprezentovány jako vlastnosti <xref:System.AttributeTargets>z hlediska definice přiřazení CLR . Použití atribuce metody by mělo `get` být použito pouze pro přistupujícího ortu, který podporuje připojitelné použití pro XAML.

### <a name="constructorargumentattribute"></a>Atribut konstruktoruArgument

**Referenční dokumentace:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**Platí pro:** Třída

**Argumenty:** Řetězec, který určuje název vlastnosti, která odpovídá jeden argument konstruktoru.

<xref:System.Windows.Markup.ConstructorArgumentAttribute>určuje, že objekt lze inicializovat pomocí syntaxe konstruktoru bez parametrů a že vlastnost zadaného názvu poskytuje informace o konstrukci. Tyto informace jsou určeny především pro serializaci XAML. Další informace naleznete v tématu <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>Atribut ContentPropertyAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**Platí pro:** Třída

**Argumenty:** Řetězec, který určuje název člena přiřazeného typu.

<xref:System.Windows.Markup.ContentPropertyAttribute>označuje, že vlastnost pojmenovaná argumentem by měla sloužit jako vlastnost obsahu XAML pro daný typ. Definice vlastnosti obsahu XAML dědí na všechny odvozené typy, které jsou přiřaditelné k definujícímu typu. Definici na konkrétním odvozeném typu můžete <xref:System.Windows.Markup.ContentPropertyAttribute> přepsat použitím na konkrétní odvozený typ.

Pro vlastnost, která slouží jako vlastnost obsahu XAML, může být označení prvku vlastnosti vynecháno v použití XAML. Obvykle určíte vlastnosti obsahu XAML, které propagují zjednodušené značky XAML pro vaše modely obsahu a uzavření. Vzhledem k tomu, že pouze jeden člen může být označen jako vlastnost obsahu XAML, někdy máte možnost návrhu, které z několika vlastností kontejneru typu by měly být označeny jako vlastnost obsahu XAML. Ostatní vlastnosti kontejneru musí být použity s explicitní vlastnosti prvky.

V datovém proudu uzlu XAML vlastnosti `StartMember` obsahu `EndMember` XAML stále vytvářejí a <xref:System.Xaml.XamlMember>uzly, pomocí názvu vlastnosti pro . Chcete-li zjistit, zda je člen vlastností <xref:System.Xaml.XamlType> obsahu `StartObject` XAML, zkontrolujte hodnotu z pozice a získejte <xref:System.Xaml.XamlType.ContentProperty%2A>hodnotu .

### <a name="contentwrapperattribute"></a>Atribut ContentWrapperAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**Platí pro:** Třída, konkrétně typy kolekcí.

**Argumenty:** A, <xref:System.Type> který určuje typ, který má být používán jako typ obálky obsahu pro cizí obsah.

<xref:System.Windows.Markup.ContentWrapperAttribute>určuje jeden nebo více typů na přidruženém typu kolekce, který bude použit k zalomení cizího obsahu. Cizí obsah odkazuje na případy, kdy omezení systému typů na typ vlastnosti obsahu nezachycují všechny možné případy obsahu, které by podporovalo použití XAML pro vlastnící typ. Například podpora XAML pro obsah určitého typu může podporovat řetězce <xref:System.Collections.ObjectModel.Collection%601>v obecném typu silného typu . Obálky obsahu jsou užitečné pro migraci již existujících konvencí značek do koncepce přiřaditelných hodnot XAML pro kolekce, jako je migrace modelů obsahu souvisejících s textem.

Chcete-li určit více než jeden typ obálky obsahu, aplikujte atribut vícekrát.

### <a name="dependsonattribute"></a>Atribut DependsOn

**Referenční dokumentace:**  <xref:System.Windows.Markup.DependsOnAttribute>

**Platí pro:** Vlastnost

**Argumenty:** Řetězec, který určuje název jiného člena přiřazeného typu.

<xref:System.Windows.Markup.DependsOnAttribute>označuje, že přiřazená vlastnost závisí na hodnotě jiné vlastnosti. Použití tohoto atributu na definici vlastností zajišťuje, že závislé vlastnosti jsou zpracovány nejprve v zápisu objektu XAML. Použití <xref:System.Windows.Markup.DependsOnAttribute> určit výjimečné případy vlastností na typy, kde musí být dodržena konkrétní pořadí analýzy pro vytvoření platného objektu.

Na definici <xref:System.Windows.Markup.DependsOnAttribute> vlastnosti můžete použít více případů.

### <a name="markupextensionreturntypeattribute"></a>Atribut Atribut Návratový typ markupExtension

**Referenční dokumentace:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**Platí pro:** Třída, která se očekává, <xref:System.Windows.Markup.MarkupExtension> že odvozený typ.

**Argumenty:** A, <xref:System.Type> který určuje nejpřesnější typ `ProvideValue` očekávat jako výsledek <xref:System.Windows.Markup.MarkupExtension>atributu .

Další informace naleznete [v tématu Markup Extensions for XAML Overview](markup-extensions-overview.md).

### <a name="namescopepropertyattribute"></a>Atribut NameScopePropertyAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**Platí pro:** Třída

**Argumenty:** Podporuje dvě formy atribuce:

- Řetězec, který určuje název vlastnosti na přiřazený typ.

- Řetězec, který určuje název vlastnosti a <xref:System.Type> pro typ, který definuje pojmenovanou vlastnost. Tento formulář je určen pro určení připojitelného člena jako vlastnost iscope názvů XAML.

<xref:System.Windows.Markup.NameScopePropertyAttribute>určuje vlastnost, která poskytuje hodnotu název_oboru XAML pro přiřazenou třídu. Očekává se, že vlastnost namescope XAML <xref:System.Windows.Markup.INameScope> bude odkazovat na objekt, který implementuje a obsahuje skutečný název xaml, jeho úložiště a jeho chování.

### <a name="runtimenamepropertyattribute"></a>Atribut RuntimeNamePropertyAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**Platí pro:** Třída

**Argumenty:** Řetězec, který určuje název vlastnosti název za běhu na přiřazeném typu.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>hlásí vlastnost přiřazeného typu, která se mapuje na XAML [x:Name Directive](xname-directive.md). Vlastnost musí být <xref:System.String> typu a musí být čtení a zápis.

Definice dědí na všechny odvozené typy, které jsou přiřaditelné k definujícímu typu. Definici na konkrétním odvozeném typu můžete <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> přepsat použitím na konkrétní odvozený typ.

### <a name="trimsurroundingwhitespaceattribute"></a>Atribut TrimSurroundingWhitespaceAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**Platí pro:** Typy

**Argumenty:** Žádný.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>se použije na určité typy, které se mohou zobrazit jako podřízené prvky v rámci významného obsahu prázdného místa (obsah v držení kolekce, která má <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>je relevantní především pro cestu uložení, ale je k dispozici v systému <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>typu XAML v cestě zatížení kontrolou . Další informace naleznete [v tématu White-space processing in XAML](white-space-processing.md).

### <a name="typeconverterattribute"></a>Typeconverterattribute

**Referenční dokumentace:**  <xref:System.ComponentModel.TypeConverterAttribute>

**Platí pro:** Třída, vlastnost, metoda (pouze XAML platné `get` metody případ je přistupující objekt, který podporuje připojitelný člen).

**Argumenty:** <xref:System.ComponentModel.TypeConverter>. <xref:System.Type>

<xref:System.ComponentModel.TypeConverterAttribute>v kontextu XAML odkazuje <xref:System.ComponentModel.TypeConverter>na vlastní . To <xref:System.ComponentModel.TypeConverter> poskytuje chování převodu typu pro vlastní typy nebo členy tohoto typu.

Použijte <xref:System.ComponentModel.TypeConverterAttribute> atribut pro váš typ, odkazující na implementaci převaděče typu. Převaděče typů pro XAML můžete definovat na třídách, strukturách nebo rozhraních. Není nutné zadat převod typu pro výčty, tento převod je povolen nativně.

Převaděč typu by měl být schopen převést z řetězce, který se používá pro atributy nebo inicializační text ve značkách, do zamýšleného cílového typu. Další informace naleznete v [tématech TypeConverters a XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

Spíše než použití na všechny hodnoty typu, převaděč chování typu pro XAML lze také vytvořit na konkrétní vlastnost. V tomto případě <xref:System.ComponentModel.TypeConverterAttribute> platí pro definici vlastnosti (vnější `get` `set` definice, nikoli specifické a definice).

Chování převaděče typů pro použití XAML vlastního připojitelného člena lze přiřadit použitím na přistupující <xref:System.ComponentModel.TypeConverterAttribute> `get` ho metodu, který podporuje použití XAML.

Podobně <xref:System.ComponentModel.TypeConverter>jako <xref:System.ComponentModel.TypeConverterAttribute> , existoval v rozhraní .NET před existencí XAML a model převaděče typů sloužil jiným účelům. Chcete-li odkazovat <xref:System.ComponentModel.TypeConverterAttribute>a používat , musíte `using` jej <xref:System.ComponentModel>plně kvalifikovat nebo poskytnout prohlášení pro . Do projektu také zahrňte sestavení systému.

### <a name="uidpropertyattribute"></a>Atribut UidProperty

**Referenční dokumentace:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**Platí pro:** Třída

**Argumenty:** Řetězec, který odkazuje na příslušnou vlastnost podle názvu.

Označuje vlastnost CLR třídy, která aliasuje [x:Uid Směrnice](xuid-directive.md).

### <a name="usableduringinitializationattribute"></a>UčitelnýBěhem inicializaceAtribut

**Referenční dokumentace:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**Platí pro:** Třída

**Argumenty:** Logická hodnota. Pokud se používá pro zamýšlený účel atributu, `true`hodnota by měla být nastavena na .

Označuje, zda je typ sestaven shora dolů během vytváření grafu objektů XAML. Jedná se o pokročilý koncept, který pravděpodobně úzce souvisí s definicí programovacího modelu. Další informace naleznete v tématu <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>Atribut ValueSerializerAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**Platí pro:** Třída, vlastnost, metoda (pouze XAML platné `get` metody případ je přistupující objekt, který podporuje připojitelný člen).

**Argumenty:** A, <xref:System.Type> který určuje třídu podpory serializátoru hodnoty, která se má použít při serializaci všech vlastností přiřazeného typu nebo konkrétní přiřazené vlastnosti.

<xref:System.Windows.Markup.ValueSerializer>určuje třídu serializace hodnoty, která vyžaduje <xref:System.ComponentModel.TypeConverter> více stavu a kontextu než a dělá. <xref:System.Windows.Markup.ValueSerializer>může být přidružena k připojitelný <xref:System.Windows.Markup.ValueSerializerAttribute> člen použitím `get` atributu na statickou přistupující metodu pro připojitelný člen. Serializace hodnot je také použitelná pro výčty, rozhraní a struktury, ale ne pro delegáty.

### <a name="whitespacesignificantcollectionattribute"></a>Atribut WhitespaceSignificantCollectionAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**Platí pro:** Třída, konkrétně typy kolekce, které se očekává, že hostitele smíšeného obsahu, kde prázdné místo kolem objektu prvky může být významné pro reprezentaci uživatelského rozhraní.

**Argumenty:** Žádný.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>označuje, že typ kolekce by měly být zpracovány jako prázdné místo významné procesorem XAML, což ovlivňuje konstrukci uzlů hodnotového proudu uzlu XAML v rámci kolekce. Další informace naleznete [v tématu White-space processing in XAML](white-space-processing.md).

### <a name="xamldeferloadattribute"></a>Atribut XamlDeferLoad

**Referenční dokumentace:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**Platí pro:** Třída, majetek.

**Argumenty:** Podporuje dva typy atribučních formulářů <xref:System.Type>jako řetězce nebo typy jako . Viz třída <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Označuje, že třída nebo vlastnost má odložené zatížení využití pro XAML (například chování šablony) a hlásí třídu, která umožňuje chování odložení a jeho cíl/typ obsahu.

### <a name="xamlsetmarkupextensionattribute"></a>Atribut XamlSetMarkupExtensionAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**Platí pro:** Třída

**Argumenty:** Pojmenuje zpětné volání.

Označuje, že třída může použít rozšíření značky poskytnout hodnotu pro jednu nebo více jeho vlastností a odkazuje na obslužnou rutinu, že zapisovač XAML by měl volat před provedením operace sady rozšíření značky na libovolnou vlastnost třídy.

### <a name="xamlsettypeconverterattribute"></a>Atribut xamlsettypeconverter

**Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**Platí pro:** Třída

**Argumenty:** Pojmenuje zpětné volání.

Označuje, že třída může použít převaděč typu poskytnout hodnotu pro jednu nebo více jeho vlastností a odkazuje na obslužnou rutinu, že zapisovač XAML by měl volat před provedením operace převaděč typu nastavit na libovolnou vlastnost třídy.

### <a name="xmllangpropertyattribute"></a>Atribut _XmlLangPropertyAttribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**Platí pro:** Třída

**Argumenty:** Řetězec, který určuje název vlastnosti alias `xml:lang` na přiřazený typ.

<xref:System.Windows.Markup.XmlLangPropertyAttribute>hlásí vlastnost přiřazeného typu, která se `lang` mapuje na direktivu XML. Vlastnost není nutně typu, <xref:System.String> ale musí být přiřaditelné z řetězce (přiřazení může být provedeno přisučením převaděče typu s typem vlastnosti nebo s konkrétní vlastností). Vlastnost musí být čtení a zápis.

Scénář pro `xml:lang` mapování je tak, aby objektový model runtime má přístup k informacím jazyka zadaný mj.

Definice dědí na všechny odvozené typy, které jsou přiřaditelné k definujícímu typu. Definici na konkrétním odvozeném typu můžete <xref:System.Windows.Markup.XmlLangPropertyAttribute> přepsat použitím na konkrétní odvozený typ, i když se jedná o neobvyklý scénář.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributy CLR související s XAML na úrovni sestavení

Následující části popisují atributy související s XAML, které nejsou použity pro typy nebo definice členů, ale místo toho jsou použity pro sestavení. Tyto atributy se připomíjejí celkovému cíli definování knihovny, která obsahuje vlastní typy, které se mají používat v xaml. Některé atributy nemusí nutně ovlivnit datový proud uzlu XAML přímo, ale jsou předávány v datovém proudu uzlu pro ostatní spotřebitele k použití. Spotřebitelé informací zahrnují návrhová prostředí nebo procesy serializace, které potřebují informace o oboru názvů XAML a přidružené informace o předponě. Kontext schématu XAML (včetně výchozího nastavení služby .NET XAML) také používá tyto informace.

### <a name="xmlnscompatiblewithattribute"></a>Atribut XmlnsCompatibleWith

**Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Argumenty:**

- Řetězec, který určuje identifikátor oboru názvů XAML pro subsume.

- Řetězec, který určuje identifikátor oboru názvů XAML, který může podeřadit obor názvů XAML z předchozího argumentu.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>určuje, že obor názvů XAML může být zahrnut jiným oborem názvů XAML. Obor názvů XAML subsuming je obvykle uveden v <xref:System.Windows.Markup.XmlnsDefinitionAttribute>dříve definovaném oboru . Tuto techniku lze použít pro správu verzí slovníku XAML v knihovně a pro jeho kompatibilitu s dříve definovanými značkami proti staršímu slovníku verze.

### <a name="xmlnsdefinitionattribute"></a>Xmlnsdefinitionattribute

**Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Argumenty:**

- Řetězec, který určuje identifikátor oboru názvů XAML, který má být definován.

- Řetězec, který pojmenuje obor názvů CLR. Obor názvů CLR by měl definovat veřejné typy ve vašem sestavení a alespoň jeden z typů oboru názvů CLR by měl být určen pro použití XAML.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>určuje mapování na základě sestavení mezi oborem názvů XAML a oborem názvů CLR, které se pak používá pro rozlišení typu zapisovačem objektu XAML nebo kontextem schématu XAML.

  Více než <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jeden lze použít na sestavení. To může být provedeno z jakékoli kombinace následujících důvodů:

- Návrh knihovny obsahuje více oborů názvů CLR pro logickou organizaci přístupu rozhraní API za běhu; však chcete, aby všechny typy v těchto oborech názvů byly použitelné xaml odkazem na stejný obor názvů XAML. V takovém případě použijete několik <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributů pomocí stejné <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnoty, ale různé <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> hodnoty. To je užitečné zejména v případě, že definujete mapování pro obor názvů XAML, který vaše architektura nebo aplikace zamýšlí být výchozím oborem názvů XAML v běžném používání.

- Návrh knihovny obsahuje více oborů názvů CLR a chcete záměrné oddělení oboru názvů XAML mezi použitími typů v těchto oborech názvů CLR.

- Definujete obor názvů CLR v sestavení a chcete, aby byl přístupný prostřednictvím více než jednoho oboru názvů XAML. K tomuto scénáři dochází, pokud podporujete více slovníků se stejným základem kódu.

- Podporu jazyka XAML definujete v jednom nebo více oborech názvů CLR. V tomto případě <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> by `http://schemas.microsoft.com/winfx/2006/xaml`měla být hodnota .

### <a name="xmlnsprefixattribute"></a>Atribut XmlnsPrefix

**Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Argumenty:**

- Řetězec, který určuje identifikátor oboru názvů XAML.

- Řetězec, který určuje doporučenou předponu.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>určuje doporučenou předponu, která se má použít pro obor názvů XAML. Předpona je užitečná při psaní prvků a atributů v souboru XAML, který je serializován službou .NET XAML Services <xref:System.Xaml.XamlXmlWriter>, nebo při interakci knihovny implementující XAML s návrhovým prostředím, které má funkce úprav XAML.

  Více než <xref:System.Windows.Markup.XmlnsPrefixAttribute> jeden lze použít na sestavení. To může být provedeno z jakékoli kombinace následujících důvodů:

- Sestavení definuje typy pro více než jeden obor názvů XAML. V takovém případě definujte různé hodnoty předpony pro každý obor názvů XAML.

- Podporujete více slovníků a používáte různé předpony pro každou slovní zásobu a obor názvů XAML.

- Definujete podporu jazyka XAML v <xref:System.Windows.Markup.XmlnsDefinitionAttribute> sestavení `http://schemas.microsoft.com/winfx/2006/xaml`a mají pro . V takovém případě byste obvykle měli `x`povýšit předponu .

> [!NOTE]
> Služba .NET XAML Services také definuje atribut <xref:System.Windows.Markup.RootNamespaceAttribute>související s XAML . Tento atribut je atribut na úrovni sestavení pro podporu systému projektu a není relevantní pro vlastní typy XAML.

## <a name="see-also"></a>Viz také

- <xref:System.Attribute>
- [Definování vlastních typů pro použití s .NET XAML Services](define-custom-types.md)
