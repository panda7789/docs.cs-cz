---
title: Definování vlastních typů pro práci s technologií .NET Framework XAML Services
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 9edc7baa1a540a71997cf5b1ed010ad5c7960d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definování vlastních typů pro práci s technologií .NET Framework XAML Services
Při definování vlastních typů, které jsou objekty firmy nebo jsou typy, které nemají závislost na konkrétní architektury, existují některé osvědčené postupy pro jazyk XAML můžete provést. Pokud budete postupovat podle těchto postupech, můžete zjistit charakteristiky XAML vašeho typu a dejte mu odpovídající reprezentace v datový proud uzlu XAML pomocí systému XAML typ rozhraní .NET Framework XAML Services a jeho XAML čtení a zápis XAML. Toto téma popisuje osvědčené postupy pro definice typů, člen definice a CLR zapisujících typů nebo členy.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Konstruktor vzory a definic typů pro jazyk XAML  
 Chcete-li být vytvořena instance jako element objektu v jazyce XAML, vlastní třídu musí splňovat následující požadavky:  
  
-   Vlastní třída musí být veřejná a musí vystavit výchozí veřejný konstruktor (bez parametrů). (Viz následující části poznámky týkající se struktury).  
  
-   Vlastní třída nesmí být vnořená třída. Navíc "bod" v cestě název úplné vytvoří obor názvů třídy dělení nejednoznačný a naruší to jinými XAML funkcemi, jako je přidružené vlastnosti.  
  
 Pokud objekt se dá vytvořit instance jako element objektu, vytvořený objekt vyplnit formu všechny vlastnosti, které trvat objekt jako svoje základní typ pro element vlastnosti.  
  
 Pokud povolíte převaděč hodnoty, můžete zadejte stále objekt hodnoty pro typy, které tato kritéria nesplňují. Další informace najdete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Struktury  
 Struktury dokážou vždy v jazyce XAML, zkonstruovat podle definice CLR. To je proto CLR kompilátoru implicitně vytvoří výchozí konstruktor pro strukturu. Tento konstruktor inicializuje všechny hodnoty vlastností pro jejich výchozí hodnoty.  
  
 V některých případech není výchozí chování konstrukce pro strukturu žádoucí. Může to být proto strukturu slouží k vyplnění hodnoty a funkce koncepčně jako spojení. Jako union obsahují hodnoty může mít vzájemně se vylučuje interpretace, a proto nejsou žádná z jeho vlastnosti nastavit. Příklad struktury ve slovníku WPF je <xref:System.Windows.GridLength>. Tyto struktury by měla implementovat převaděče typů tak, aby hodnoty mohou být vyjádřeny v atributu formuláře pomocí názvů řetězec vytvořit různé interpretace nebo režimy hodnoty strukturu. Struktura by měl vystavit také podobné chování pro vytváření kódu prostřednictvím jiné než výchozí konstruktor.  
  
### <a name="interfaces"></a>Rozhraní  
 Rozhraní slouží jako základní typy členů. Systém typů XAML zkontroluje seznamu přiřadit a očekává, že objekt, který je zadaný jako hodnota může být přiřazen rozhraní. Neexistuje žádná koncepce jak musí být rozhraní zobrazovat jako typ jazyka XAML typu relevantní Přiřaditelné podporuje požadavky na vytváření XAML.  
  
### <a name="factory-methods"></a>Metody vytváření  
 Metody vytváření jsou funkce jazyka XAML 2009. Jejich upravit Princip XAML, objekty musí mít výchozí konstruktory. Metody vytváření nejsou popsané v tomto tématu. V tématu [x: factorymethod – direktiva](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Výčty  
 Výčty chovají XAML nativní typ převodu. Výčet konstantní názvy zadané v jazyce XAML se přeloží proti základní typ výčtu a obnoví hodnota výčtu zapisovač objekt XAML.  
  
 XAML podporuje použití příznaky stylu pro výčty s <xref:System.FlagsAttribute> použít. Další informace najdete v tématu [XAML syntaxe v podrobností](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md). ([XAML syntaxe v podrobností](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) je napsán pro cílovou skupinu WPF, ale většina informací v tomto tématu je relevantní pro jazyk XAML, které nejsou specifické pro konkrétní rozhraní implementuje.)  
  
## <a name="member-definitions"></a>Definice člena  
 Typy můžete definovat členy pro použití XAML. Je možné pro typy, které definují členů, které jsou použitelné XAML, i když tento konkrétní typ není použitelné XAML. To je možné z důvodu dědičnosti CLR. Tak dlouho, dokud nějaký typ, který dědí člen podporuje použití XAML jako typ a člen podporuje použití XAML pro jeho zdrojovým typem nebo má k dispozici nativní XAML syntaxi, je daný člen XAML použitelné.  
  
### <a name="properties"></a>Vlastnosti  
 Pokud definujete vlastnosti jako veřejné vlastnosti CLR pomocí typické CLR `get` a `set` přistupujícího objektu vzory a používání jazyka vhodné, můžete sestavu systém typů XAML vlastnost jako člena s příslušné informace k dispozici pro <xref:System.Xaml.XamlMember> vlastnosti, jako například <xref:System.Xaml.XamlMember.IsReadPublic%2A> a <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Specifické vlastnosti můžete povolit syntaxe textu s použitím <xref:System.ComponentModel.TypeConverterAttribute>. Další informace najdete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Chybí textových syntaxi nebo nativní převod XAML a bez další dereference, jako je například rozšíření použití značek, typ vlastnosti (<xref:System.Xaml.XamlMember.TargetType%2A> v XAML systém typů) musí být schopen vrátit instanci objektu zapisovač XAML podle práce t Typ arget jako typ CLR.  
  
 Pokud používáte XAML 2009 [x: Reference – rozšíření značek](../../../docs/framework/xaml-services/x-reference-markup-extension.md) slouží k zadání hodnot, pokud nejsou splněné předchozí aspekty; je však informace o využití problém než problémem definice typu.  
  
### <a name="events"></a>Události  
 Pokud definujete události jako veřejná událost CLR, systém typů XAML ohlásit událost jako člena s <xref:System.Xaml.XamlMember.IsEvent%2A> jako `true`. Vzájemné propojení obslužné rutiny událostí není v rámci oboru funkce rozhraní .NET Framework XAML Services; je to zleva implementace a konkrétní rozhraní.  
  
### <a name="methods"></a>Metody  
 Vložený kód pro metody není výchozí XAML možnost. Ve většině případů je přímo neodkazujte metoda členy z XAML a roli metody v jazyce XAML je pouze k zajištění podpory pro určité vzory XAML. [x: factorymethod – direktiva](../../../docs/framework/xaml-services/x-factorymethod-directive.md) je výjimku.  
  
### <a name="fields"></a>Pole  
 Pokyny pro návrh CLR bránit nestatické pole. Statická pole, dostanete statické pole hodnot pouze prostřednictvím [x: Static – rozšíření značek](../../../docs/framework/xaml-services/x-static-markup-extension.md); v takovém případě nejsou žádné zvláštní v definici CLR vystavit pole pro provádění [x: Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) použití.  
  
## <a name="attachable-members"></a>Připojitelné členy  
 Připojitelné členové jsou vystaveny XAML prostřednictvím vzor metoda přistupující objekt definující typu. Definující vlastní typ nemusí být XAML použitelné jako objekt. Ve skutečnosti je běžný vzor deklarovat třídu služby, který má roli vlastní připojitelné člen a implementovat související chování, ale poskytovat další funkce, jako je například znázornění uživatelského rozhraní. Na následující oddíly zástupného textu *PropertyName* představuje název vaší připojitelné člena. Tento název musí být platný v [XamlName – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 Věnujte pozornost kolize názvů mezi tyto vzory a jiné metody typu. Pokud člena existuje odpovídající jednomu z vzory, ho můžete interpretovat jako cestu připojitelné člen využití procesoru XAML i v případě, která nebyla svůj záměr.  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName přístupového objektu  
 Podpis pro `Get` *PropertyName* přistupujícího objektu musí být:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` Objekt lze zadat jako typu konkrétnější v implementaci. Můžete použít k určení rozsahu využití vaší připojitelné člena; použití mimo zamýšlený rozsah vyvolá výjimku neplatné obsazení výjimky, které jsou pak prezentované podle chybu analýzy XAML. Název parametru `target` není povinné, ale je s názvem `target` podle konvence většina implementací.  
  
-   Návratovou hodnotu lze zadat jako typu konkrétnější v implementaci.  
  
 Pro podporu <xref:System.ComponentModel.TypeConverter> povoleno text syntaxe pro použití atributu připojitelné člena použít <xref:System.ComponentModel.TypeConverterAttribute> k `Get` *PropertyName* přistupujícího objektu. Použití `get` místo `set` se může zdát nonintuitive; touto konvencí však může podporovat koncept jen pro čtení připojitelné členy, kteří jsou serializable, který je užitečný ve scénářích, návrháře.  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName přístupového objektu  
 Podpis pro sadu*PropertyName* přistupujícího objektu musí být:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` Objekt lze zadat jako typu konkrétnější v implementaci pomocí stejné logiky a důsledky, jak je popsáno v předchozí části.  
  
-   `value` Objekt lze zadat jako typu konkrétnější v implementaci.  
  
 Mějte na paměti, že hodnota pro tuto metodu je vstupní pocházejících z použití XAML, obvykle v podobě atributu. Z formuláře atributu musí být hodnota převaděč podpora textových syntaxi a atributu u `Get` *PropertyName* přistupujícího objektu.  
  
### <a name="attachable-member-stores"></a>Připojitelné člen úložiště  
 Metody přístupových objektů nejsou obvykle dostatek prostředků k umístěte hodnoty připojitelné členů do grafu objektu, nebo k načtení hodnoty z grafu objektů a je správně serializovat. Tato funkce `target` objekty v předchozí signatury přistupujícího objektu musí být schopný ukládání hodnot. Mechanismus úložiště musí být v souladu se zásadou připojitelné člen, který je člen připojitelné k cílům, kde připojitelné člen není v seznamu členů. Rozhraní .NET framework XAML Services poskytuje implementaci technika pro připojitelné člen ukládá prostřednictvím rozhraní API <xref:System.Xaml.IAttachedPropertyStore> a <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> XAML zapisovače používané ke zjišťování implementace úložiště a by měla být implementována na typ, který je `target` přistupujících objektů. Statické <xref:System.Xaml.AttachablePropertyServices> rozhraní API se používají v textu přístupové objekty a připojitelné odkazujte podle jeho <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atributy CLR související s XAML  
 Správně zapisujících vaší typy, členů a sestavení je důležité, aby sestavy informace systému typ jazyka XAML pro rozhraní .NET Framework XAML Services. To je důležité, pokud máte v úmyslu vaší typy pro použití s XAML systémy, které jsou přímo založené na rozhraní .NET Framework XAML Services XAML čtení a zápis XAML, nebo pokud můžete definovat, nebo pomocí rozhraní využívá XAML, které je založena na těchto XAML čtení a zápis XAML.  
  
 Seznam každý atribut související s jazykem XAML, které jsou důležité pro XAML podporuje vlastní typy najdete v tématu [XAML-Related CLR atributy pro vlastní typy a knihovny](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Použití  
 Použití vlastní typy vyžaduje, aby autor značek musí být mapována předponu pro sestavení a obor názvů CLR, které obsahují vlastní typ. Tento postup není dokumentováno v tomto tématu.  
  
## <a name="access-level"></a>Úroveň přístupu  
 XAML poskytuje prostředky ke spouštění a vytvoření instancí typy, které mají `internal` úroveň přístupu. Tato funkce je k dispozici, aby uživatelský kód můžete definovat vlastní typy a potom vytvořte instanci tyto třídy z kód, který je také součástí oboru stejný kód uživatele.  
  
 Příklad z grafického subsystému WPF je vždy, když uživatel kód definuje <xref:System.Windows.Controls.UserControl> určený jako způsob, jak Refaktorovat chování uživatelského rozhraní, ale nikoli jako součást všechny možné rozšíření mechanismus, který může být implicitní deklarováním třídy podpůrné s `public` úroveň přístupu. Takové <xref:System.Windows.Controls.UserControl> lze deklarovat s `internal` přístup, pokud je kód základní zkompilovat do stejného sestavení, ze které se odkazuje jako typ jazyka XAML.  
  
 Pro aplikaci, která načte XAML pod úplným vztahem důvěryhodnosti a používá <xref:System.Xaml.XamlObjectWriter>, načítání tříd pomocí `internal` úroveň přístupu je vždy povolena.  
  
 Pro aplikaci, která načte XAML v částečné důvěryhodnosti, můžete řídit charakteristiky úrovně přístupu pomocí <xref:System.Xaml.Permissions.XamlAccessLevel> rozhraní API. Navíc musí být schopen rozšířit žádné úrovně oprávnění k přístupu a zachování jejich pro hodnocení případné běhu; mechanismy odložení (například systém šablony WPF) To se interně zpracovává předáním <xref:System.Xaml.Permissions.XamlAccessLevel> informace.  
  
### <a name="wpf-implementation"></a>Implementace WPF  
 WPF XAML používá model částečným vztahem důvěryhodnosti přístupu, kde Pokud BAML je zavedený v částečné důvěryhodnosti, přístup je omezen na <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> pro sestavení, který je zdrojem BAML. Pro odložení, používá WPF <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> jako mechanismus pro předávání informací úrovně přístupu.  
  
 V terminologii WPF XAML *interní typ* je typ, který je definován pomocí stejného sestavení, která zahrnuje i odkazující XAML. Takové typ se dá namapovat prostřednictvím oboru názvů jazyka XAML, který úmyslně vynechá sestavení = část mapování, například `xmlns:local="clr-namespace:WPFApplication1"`.  Pokud BAML odkazuje na interní typ a že má typ `internal` přístup úrovni, tím se vygeneruje `GeneratedInternalTypeHelper` třídu pro sestavení. Pokud chcete, aby se zabránilo `GeneratedInternalTypeHelper`, buď musíte použít `public` přístup úroveň, nebo musí zohlednit příslušné třídě do samostatné sestavení a ujistěte se, že sestavení závislé.  
  
## <a name="see-also"></a>Viz také  
 [Atributy CLR související s jazykem XAML pro vlastní typy a knihovny](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [XAML Services](../../../docs/framework/xaml-services/index.md)
