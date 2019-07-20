---
title: Definování vlastních typů pro práci s technologií .NET Framework XAML Services
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: e563c0d7e5113d55d4b942fb1d175a64f5b71abc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364291"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definování vlastních typů pro práci s technologií .NET Framework XAML Services
Při definování vlastních typů, které jsou obchodní objekty, nebo typy, které nemají závislost na konkrétních architekturách, je možné sledovat určité osvědčené postupy pro XAML. Pokud budete postupovat podle těchto postupů, .NET Framework služby XAML a jeho čtenáři XAML a moduly pro zápis XAML mohou zjistit charakteristiky XAML vašeho typu a poskytnout mu odpovídající reprezentace v datovém proudu uzlu XAML pomocí systému typů XAML. V tomto tématu jsou popsány osvědčené postupy pro definice typu, definice členů a CLR, které připisují typy nebo členy.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Vzory konstruktoru a definice typů pro XAML  
 Aby mohla vlastní třída vytvořit instanci jako prvek objektu v jazyce XAML, musí splňovat následující požadavky:  
  
- Vlastní třída musí být veřejná a musí vystavovat výchozí veřejný konstruktor (bez parametrů). (Poznámky týkající se struktur najdete v následující části.)  
  
- Vlastní třída nesmí být vnořená třída. Znak "tečka" v cestě s úplným názvem způsobuje nejednoznačnou divizi oboru názvů třídy a je v konfliktu s jinými funkcemi XAML, jako jsou například připojené vlastnosti.  
  
 Pokud objekt může být vytvořen jako prvek objektu, může vytvořený objekt vyplnit formulář elementu vlastnosti všech vlastností, které přebírají objekt jako svůj podkladový typ.  
  
 Pokud povolíte převaděč hodnot, můžete přesto zadat hodnoty objektů pro typy, které nesplňují tato kritéria. Další informace naleznete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Struktury  
 Struktury jsou vždy možné sestavit v jazyce XAML podle definice CLR. Je to proto, že kompilátor CLR implicitně vytvoří konstruktor bez parametrů pro strukturu. Tento konstruktor inicializuje všechny hodnoty vlastností na jejich výchozí hodnoty.  
  
 V některých případech není výchozí chování konstrukce pro strukturu žádoucí. Důvodem může být to, že struktura je určena k vyplnění hodnot a funkce koncepčně jako sjednocení. V rámci sjednocení mohou obsažené hodnoty mít vzájemně exkluzivní výklad, a proto nelze nastavit žádnou z jejích vlastností. Příkladem takové struktury ve slovníku WPF je <xref:System.Windows.GridLength>. Tyto struktury by měly implementovat konvertor typu tak, aby hodnoty mohly být vyjádřeny ve formě atributu pomocí konvencí řetězců, které vytvářejí různé interpretace nebo režimy hodnot struktury. Struktura by měla také vystavovat podobné chování pro vytváření kódu prostřednictvím konstruktoru bez parametrů.  
  
### <a name="interfaces"></a>Rozhraní  
 Rozhraní lze použít jako základní typy členů. Systém typů XAML kontroluje seznam přiřazení a očekává, že objekt, který je k dispozici jako hodnota, lze přiřadit k rozhraní. Neexistuje žádný koncept, jak musí být rozhraní prezentována jako typ XAML, pokud příslušný typ přiřazení podporuje požadavky na konstrukci XAML.  
  
### <a name="factory-methods"></a>Metody pro vytváření objektů  
 Metody pro vytváření objektů jsou funkcí XAML 2009. Upravují princip jazyka XAML, že objekty musí mít konstruktory bez parametrů. Metody pro vytváření objektů nejsou popsány v tomto tématu. Viz [direktiva x:FactoryMethod –](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Výčty  
 Výčty mají chování konverze nativního typu XAML. Výčty názvů výčtu zadané v jazyce XAML jsou vyřešeny proti základnímu typu výčtu a vracejí hodnotu výčtu do zapisovače objektu XAML.  
  
 Jazyk XAML podporuje použití stylu příznaků pro výčty s <xref:System.FlagsAttribute> použitím. Další informace naleznete v tématu [syntaxe jazyka XAML podrobněji](../wpf/advanced/xaml-syntax-in-detail.md). ([Syntaxe jazyka XAML je podrobně](../wpf/advanced/xaml-syntax-in-detail.md) určena pro cílovou skupinu WPF, ale většina informací v tomto tématu je relevantní pro jazyk XAML, který není specifický pro konkrétní implementaci rozhraní.)  
  
## <a name="member-definitions"></a>Definice členů  
 Typy mohou definovat členy pro použití v jazyce XAML. Je možné použít typy, které definují členy, které jsou použitelné v jazyce XAML, i v případě, že tento konkrétní typ není použit jako XAML. To je možné z důvodu dědičnosti CLR. Pokud nějaký typ, který dědí člen, podporuje použití XAML jako typ a člen podporuje použití XAML pro svůj základní typ nebo má k dispozici nativní syntaxi jazyka XAML, je tento člen použitelný jako XAML.  
  
### <a name="properties"></a>Vlastnosti  
 Definujete-li vlastnosti jako veřejnou vlastnost CLR pomocí typických vzorů `set` CLR `get` a přístupových objektů a odpovídajících jazyků, může systém typů XAML hlásit vlastnost jako člen s příslušnými informacemi poskytnutými pro <xref:System.Xaml.XamlMember> vlastnosti ,<xref:System.Xaml.XamlMember.IsReadPublic%2A> například a <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Konkrétní vlastnosti umožňují použít syntaxi <xref:System.ComponentModel.TypeConverterAttribute>textu. Další informace naleznete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 V případě, že se nejedná o syntaxi textu nebo nativní konverzi XAML a v případě neexistence dalšího indirekce, jako je například použití rozšíření značek, musí být typ vlastnosti<xref:System.Xaml.XamlMember.TargetType%2A> (v systému typů XAML) schopný vrátit instanci do zapisovače objektů XAML tím, že zpracuje t typ arget jako typ CLR.  
  
 Pokud používáte XAML 2009, lze použít [rozšíření značek x:Reference](x-reference-markup-extension.md) k poskytnutí hodnot, pokud předchozí okolnosti nejsou splněny. ale to je více než problém s definicí typu.  
  
### <a name="events"></a>Události  
 Definujete-li události jako veřejnou událost CLR, může systém typů XAML hlásit událost jako člen s <xref:System.Xaml.XamlMember.IsEvent%2A> jako. `true` Kabely obslužných rutin událostí nejsou v rozsahu možností .NET Framework služby XAML. Toto je ponecháno na konkrétní architektury a implementace.  
  
### <a name="methods"></a>Metody  
 Vložený kód pro metody není výchozí funkcí jazyka XAML. Ve většině případů neodkazujte přímo na členy metody z XAML a role metod v jazyce XAML je určena pouze k poskytnutí podpory pro konkrétní vzory XAML. [direktiva x:FactoryMethod –](x-factorymethod-directive.md) je výjimka.  
  
### <a name="fields"></a>Pole  
 Pokyny pro návrh CLR odradit nestatickým polím. Pro statická pole můžete přistupovat k hodnotám statického pole pouze prostřednictvím [rozšíření značek x:static](x-static-markup-extension.md); v takovém případě neprovádíte žádné speciální údaje v definici CLR k vystavení pole pro použití [x:static](x-static-markup-extension.md) .  
  
## <a name="attachable-members"></a>Připojení členové  
 Připojitelné členy jsou zpřístupněny XAML prostřednictvím vzoru metody přístupového objektu na definujícím typu. Definiční typ samotný není nutné použít jako objekt XAML. Společný vzor ve skutečnosti je deklarovat třídu služby, jejíž role je vlastníkem přihlášeného člena a implementovat související chování, ale neposkytuje žádnou jinou funkci, jako je například reprezentace uživatelského rozhraní. V následujících částech zástupný symbol *PropertyName* nepředstavuje název připojeného člena. Tento název musí být platný v gramatice v kódu [XAML](xamlname-grammar.md).  
  
 Buďte opatrní proti kolizím názvů mezi těmito vzory a jinými metodami typu. Pokud existuje člen, který odpovídá jednomu ze vzorů, lze jej interpretovat jako připojovatelné členy pomocí procesoru XAML, a to i v případě, že to nebylo vaším záměrem.  
  
#### <a name="the-getpropertyname-accessor"></a>Přístupový objekt GetProperty  
 Signatura `Get`přístupového objektu *PropertyName* musí být:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
- `target` Objekt může být zadán jako konkrétnější typ v implementaci. Tuto možnost můžete použít k určení rozsahu využití přidaného člena; použití mimo zamýšlený rozsah vyvolá neplatné výjimky přetypování, které jsou následně vykryty chybou analýzy XAML. Název `target` parametru není požadavek, ale je pojmenován `target` podle konvence ve většině implementací.  
  
- Návratová hodnota může být v implementaci zadána jako konkrétnější typ.  
  
 Pro podporu <xref:System.ComponentModel.TypeConverter> povolených syntaxí textu pro použití atributu přistupujícího člena použijte <xref:System.ComponentModel.TypeConverterAttribute> pro přístup k `Get` *PropertyName* . Použití na `get` místo `set` se může zdát neintuitivní; Nicméně tato konvence může podporovat koncept přidaných členů, kteří jsou serializovatelný, což je užitečné v rámci scénářů pro návrháře.  
  
#### <a name="the-setpropertyname-accessor"></a>Přístup ke SetProperty  
 Podpis pro přístup Set*PropertyName* musí být:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
- `target` Objekt může být zadán jako konkrétnější typ v implementaci, se stejnou logikou a následky, jak je popsáno v předchozí části.  
  
- `value` Objekt může být zadán jako konkrétnější typ v implementaci.  
  
 Pamatujte, že hodnota pro tuto metodu je vstup z použití XAML, obvykle ve formě atributu. Z formuláře atributu musí být podpora převaděče hodnot pro textovou syntaxi a atributem `Get`přístupového objektu *PropertyName* .  
  
### <a name="attachable-member-stores"></a>Připojitelná úložiště členů  
 Přístupové metody nejsou obvykle dostačující k tomu, aby poskytovaly prostředky, které umožňují umístit přizpůsobitelné členské hodnoty do grafu objektů, nebo načíst hodnoty z grafu objektů a serializovat je správně. Aby bylo možné tuto funkci poskytnout `target` , objekty v předchozích podpisech přístupového objektu musí být schopny ukládat hodnoty. Mechanismus úložiště by měl být v souladu s principem připojitelné člena, že člen je možné připojit k cílům, kde je připojitelný člen v seznamu členů. .NET Framework služby XAML poskytují techniku implementace pro připojovatelné členské obchody prostřednictvím rozhraní API <xref:System.Xaml.IAttachedPropertyStore> a <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore>je používána zapisovači jazyka XAML ke zjištění implementace úložiště a měla by být implementována na typ, který je `target` přístupovými objekty. Statická <xref:System.Xaml.AttachablePropertyServices> rozhraní API se používají v těle přístupových objektů a odkazují na připojitelné členy podle jeho <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atributy CLR související s jazykem XAML  
 Správné označení vašich typů, členů a sestavení je důležité, aby bylo možné nahlásit systémové informace typu XAML do .NET Framework služby XAML. To je důležité, pokud máte v úmyslu používat systémy XAML přímo na základě .NET Framework čtenáři XAML a zapisovače XAML, nebo pokud definujete nebo používáte rozhraní XAML, které je založené na těchto čtenářích XAML a zapisovači XAML.  
  
 Seznam každého atributu souvisejícího s XAML, který je relevantní pro podporu jazyka XAML vašich vlastních typů, naleznete v tématu [atributy CLR související s jazykem XAML pro vlastní typy a knihovny](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Použití  
 Použití vlastních typů vyžaduje, aby autor značek musel mapovat předponu pro sestavení a obor názvů CLR, který obsahuje vlastní typ. Tato procedura není popsána v tomto tématu.  
  
## <a name="access-level"></a>Úroveň přístupu  
 XAML poskytuje způsob načítání a vytváření instancí typů, které mají `internal` úroveň přístupu. Tato funkce je k dispozici, aby kód uživatele mohl definovat vlastní typy, a poté vytvořit instance těchto tříd ze značek, který je také součástí stejného oboru kódu uživatele.  
  
 Příklad z WPF je vždy <xref:System.Windows.Controls.UserControl> , když uživatel definuje kód, který je určen jako způsob refaktorující chování uživatelského rozhraní, ale ne jako součást jakéhokoli mechanizmu rozšiřujícího mechanismu, který může být odvozen deklarováním podpůrné třídy s `public` úrovní přístupu. Takový objekt <xref:System.Windows.Controls.UserControl> lze deklarovat s `internal` přístupem, pokud je zálohovaný kód zkompilován do stejného sestavení, ze kterého je odkazováno jako typ XAML.  
  
 Pro aplikaci, která načte XAML pod úplným vztahem <xref:System.Xaml.XamlObjectWriter>důvěryhodnosti a pomocí, `internal` je načítání tříd s úrovní přístupu vždy povoleno.  
  
 Pro aplikaci, která načte XAML v rámci částečné důvěryhodnosti, můžete řídit charakteristiky úrovně přístupu pomocí <xref:System.Xaml.Permissions.XamlAccessLevel> rozhraní API. Mechanismy odložení (například systém šablony WPF) musí být schopné rozšířit všechna oprávnění na úrovni přístupu a zachovat je pro případná vyhodnocení doby běhu; Tato <xref:System.Xaml.Permissions.XamlAccessLevel> informace je interně zpracována předáním informací.  
  
### <a name="wpf-implementation"></a>Implementace WPF  
 WPF XAML používá model přístupu s částečnou důvěryhodností, kde Pokud je BAML načten v rámci částečné důvěryhodnosti, přístup <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> je omezen na pro sestavení, které je zdrojem BAML. Pro odložení používá <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> WPF jako mechanismus pro předávání informací o úrovni přístupu.  
  
 V terminologii WPF XAML je *interní typ* typu, který je definován stejným sestavením, které také obsahuje odkaz na XAML. Takový typ lze namapovat pomocí oboru názvů XAML, který záměrně vynechává sestavení = část mapování, `xmlns:local="clr-namespace:WPFApplication1"`například.  Pokud BAML odkazuje na interní typ a tento typ má `internal` úroveň přístupu, `GeneratedInternalTypeHelper` vygeneruje třídu pro sestavení. Pokud se chcete vyhnout `GeneratedInternalTypeHelper`, je nutné buď použít `public` úroveň přístupu, nebo musí zvážit relevantní třídu do samostatného sestavení a zajistit, aby bylo sestavení závislé.  
  
## <a name="see-also"></a>Viz také:

- [Atributy CLR související s jazykem XAML pro vlastní typy a knihovny](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Services](index.md)
