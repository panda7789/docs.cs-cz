---
title: Definování vlastních typů pro použití s .NET XAML Services
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: ff7e4229450e801a6d618c5141efde8cdcbef03d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071855"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>Definování vlastních typů pro použití se službami .NET XAML Services

Při definování vlastní typy, které jsou obchodní objekty nebo typy, které nemají závislost na konkrétní rozhraní, existují určité osvědčené postupy pro XAML můžete sledovat. Pokud budete postupovat podle těchto postupů, .NET XAML Services a jeho XAML čtečky a Zapisovače XAML můžete zjistit xaml charakteristiky vašeho typu a poskytnout mu odpovídající reprezentaci v datovém proudu uzlu XAML pomocí systému typu XAML. Toto téma popisuje osvědčené postupy pro definice typů, definice členů a clr přiřazení typů nebo členů.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Vzory konstruktoru a definice typů pro XAML

Chcete-li vytvořit instanci jako prvek objektu v XAML, vlastní třída musí splňovat následující požadavky:

- Vlastní třída musí být veřejné a musí vystavit public konstruktor bez parametrů. (Poznámky týkající se struktur naleznete v následující části.)

- Vlastní třída nesmí být vnořenou třídou. Extra "tečka" v cestě celého názvu způsobí, že dělení oboru názvů třídy je nejednoznačné a narušuje jiné funkce XAML, jako jsou připojené vlastnosti.
Pokud objekt může být vytvořena jako prvek objektu, vytvořený objekt může vyplnit formulář prvku vlastnosti všech vlastností, které berou objekt jako jejich základní typ.

Stále můžete zadat hodnoty objektů pro typy, které nesplňují tato kritéria, pokud povolíte převaděč hodnot. Další informace naleznete v [tématu Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).

### <a name="structures"></a>Struktury

Struktury lze vždy sestavit v XAML podle definice CLR. Důvodem je, že kompilátor CLR implicitně vytvoří konstruktor bez parametrů pro strukturu. Tento konstruktor inicializuje všechny hodnoty vlastností na jejich výchozí hodnoty.

V některých případech není žádoucí výchozí konstrukční chování pro strukturu. To může být způsobeno tím, že struktura je určena k vyplnění hodnot a funkce koncepčně jako unie. Jako unie obsažené hodnoty může mít vzájemně se vylučující interpretace, a proto žádné z jeho vlastností jsou taelné. Příkladem takové struktury ve slovníku WPF <xref:System.Windows.GridLength>je . Tyto struktury by měly implementovat převaděč typu tak, aby hodnoty mohou být vyjádřeny ve formě atributu pomocí konvence řetězce, které vytvářejí různé interpretace nebo režimy hodnoty struktury. Struktura by měla také vystavit podobné chování pro konstrukci kódu prostřednictvím konstruktoru bez parametrů.

### <a name="interfaces"></a>Rozhraní

Rozhraní lze použít jako základní typy členů. Systém typu XAML zkontroluje přiřaditelný seznam a očekává, že objekt, který je k dispozici jako hodnota může být přiřazen a rozhraní. Neexistuje žádný koncept, jak rozhraní musí být prezentovány jako typ XAML tak dlouho, dokud příslušný přiřaditelný typ podporuje požadavky na konstrukci XAML.

### <a name="factory-methods"></a>Výrobní metody

Metody výroby jsou funkcí XAML 2009. Upravují princip XAML, že objekty musí mít konstruktory bez parametrů. Metody výroby nejsou v tomto článku popsány. Viz [x:Směrnice metod výroby](xfactorymethod-directive.md).

## <a name="enumerations"></a>Výčty

Výčty mají chování převodu nativního typu XAML. Názvy konstant výčtu zadané v xaml jsou vyřešeny proti základní typ výčtu a vrátit hodnotu výčtu zapisovačobjektu XAML.

XAML podporuje použití ve stylu příznaků pro <xref:System.FlagsAttribute> výčty s aplikovaným. Další informace naleznete [v tématu Syntaxe XAML v detailu](../../framework/wpf/advanced/xaml-syntax-in-detail.md). ([Syntaxe XAML V detailu](../../framework/wpf/advanced/xaml-syntax-in-detail.md) je napsána pro cílovou skupinu WPF, ale většina informací v tomto tématu je relevantní pro XAML, který není specifický pro konkrétní prováděcí rámec.)

## <a name="member-definitions"></a>Definice členů

Typy můžete definovat členy pro použití XAML. Je možné pro typy definovat členy, které jsou xaml použitelné i v případě, že tento konkrétní typ není xaml použitelné. To je možné z důvodu dědičnosti CLR. Tak dlouho, dokud některé typy, které dědí člen podporuje xaml použití jako typ a člen podporuje xaml použití pro jeho základní typ nebo má nativní syntaxi XAML k dispozici, tento člen je XAML použitelné.

### <a name="properties"></a>Vlastnosti

Pokud definujete vlastnosti jako veřejnou vlastnost `get` CLR pomocí typických vzorů CLR a `set` přistupujícího objektu a klíčových slov <xref:System.Xaml.XamlMember> odpovídajících jazyku, systém typu XAML může tuto vlastnost hlásit jako člena s příslušnými informacemi pro vlastnosti, například <xref:System.Xaml.XamlMember.IsReadPublic%2A> a <xref:System.Xaml.XamlMember.IsWritePublic%2A>.

Specifické vlastnosti mohou povolit <xref:System.ComponentModel.TypeConverterAttribute>syntaxi textu použitím aplikace . Další informace naleznete v [tématu Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).

Při absenci syntaxe textu nebo nativního převodu XAML a při absenci dalšího dereference, jako<xref:System.Xaml.XamlMember.TargetType%2A> je například použití rozšíření značek, musí být typ vlastnosti ( v systému typu XAML) schopen vrátit instanci zapisovateli objektu XAML tím, že bude cílový typ považován za typ CLR.

Pokud používáte XAML 2009, [x:Reference Markup Extension](xreference-markup-extension.md) lze použít k zadání hodnot, pokud nejsou splněny předchozí aspekty; to je však spíše problém s použitím než problém definice typu.

### <a name="events"></a>Události

Pokud definujete události jako veřejnou událost CLR, systém typu XAML <xref:System.Xaml.XamlMember.IsEvent%2A> `true`může hlásit událost jako člen s jako . Zapojení obslužných rutin událostí není v rámci možností služby .NET XAML Services. zapojení je ponecháno na konkrétních rámcích a implementacích.

### <a name="methods"></a>Metody

Vsazený kód pro metody není výchozí funkcí XAML. Ve většině případů není přímo odkazovat na členy metody z XAML a role metod v XAML je pouze poskytovat podporu pro konkrétní vzory XAML. [x:FactoryMethod směrnice](xfactorymethod-directive.md) je výjimkou.

### <a name="fields"></a>Pole

Pokyny pro návrh CLR odrazují od nestatických polí. U statických polí můžete přistupovat ke statickým hodnotám polí pouze prostřednictvím [x:Static Markup Extension](xstatic-markup-extension.md); v tomto případě neděláte nic zvláštního v definici CLR vystavit pole pro [x:Statické](xstatic-markup-extension.md) použití.

## <a name="attachable-members"></a>Připojitelné členy

Připojitelné členy jsou vystaveny XAML prostřednictvím vzoru přistupující metody na definující typ. Samotný definující typ nemusí být xaml použitelný jako objekt. Ve skutečnosti společný vzor je deklarovat třídu služby, jejíž úlohou je vlastnit připojitelný člen a implementovat související chování, ale slouží žádné jiné funkce, jako je například reprezentace rozhraní. Pro následující části zástupný *název PropertyName* představuje název připojitelného člena. Tento název musí být platný v [xamlname gramatiky](xamlname-grammar.md).

Buďte opatrní při kolizi názvů mezi těmito vzory a jinými metodami typu. Pokud člen existuje, který odpovídá jeden ze vzorů, může být interpretován jako připojitelné členské cesty využití procesorem XAML i v případě, že to nebyl váš záměr.

#### <a name="the-getpropertyname-accessor"></a>Přistupující objekt GetPropertyName

Podpis pro `GetPropertyName` přistupujícího ortu musí být:

`public static object GetPropertyName(object target)`

- Objekt `target` lze zadat jako konkrétnější typ v implementaci. Můžete použít k vymezení použití připojitelný člen; použití mimo zamýšlený obor vyvolá neplatné výjimky přetypovacího vysílání, které jsou pak objeveny chybou analýzy XAML. Název `target` parametru není požadavek, `target` ale je pojmenován podle konvence ve většině implementací.

- Vrácená hodnota může být zadána jako konkrétnější typ v implementaci.

Chcete-li <xref:System.ComponentModel.TypeConverter> podporovat povolenou textovou syntaxi pro <xref:System.ComponentModel.TypeConverterAttribute> použití `GetPropertyName` atributu připojitelného člena, použijte přistupujícího pole. Použití `get` na místo `set` se může zdát neintuitivní; Tato konvence však může podporovat koncept připojitelných členů jen pro čtení, které lze serializovat, což je užitečné v návrhářských scénářích.

#### <a name="the-setpropertyname-accessor"></a>Přistupující objekt SetPropertyName

Podpis pro `SetPropertyName` přistupujícího ortu musí být:

`public static void SetPropertyName(object target, object value)`

- Objekt `target` lze zadat jako konkrétnější typ v implementaci, se stejnou logikou a důsledky, jak je popsáno v předchozí části.

- Objekt `value` lze zadat jako konkrétnější typ v implementaci.

Nezapomeňte, že hodnota pro tuto metodu je vstup pocházející z využití XAML, obvykle ve formě atributu. Z formuláře atributu musí být podpora převaděče hodnot `GetPropertyName`pro syntaxi textu a atribut v přistupujícím s.

### <a name="attachable-member-stores"></a>Připojitelné členské obchody

Přistupující metody obvykle nestačí k poskytnutí prostředků k umístění připojitelných hodnot členů do grafu objektu nebo k načtení hodnot z grafu objektu a jejich serializaci správně. Chcete-li poskytnout tuto `target` funkci, musí být objekty v předchozích přistupujících podpisech schopny ukládat hodnoty. Mechanismus úložiště by měl být v souladu s principem připojitelný člen, že člen je připojitelný k cílům, kde připojitelný člen není v seznamu členů. Služba .NET XAML Services poskytuje techniku implementace pro <xref:System.Xaml.IAttachedPropertyStore> <xref:System.Xaml.AttachablePropertyServices>připojitelná úložiště členů prostřednictvím rozhraní API a . <xref:System.Xaml.IAttachedPropertyStore>používá autoři XAML ke zjištění implementace úložiště a by měla být `target` implementována na typu, který je přístupových částí. Statická <xref:System.Xaml.AttachablePropertyServices> připojení k dispozici jsou používány v těle přístupových částí a <xref:System.Xaml.AttachableMemberIdentifier>odkazují na připojitelný člen jeho .

## <a name="xaml-related-clr-attributes"></a>Atributy CLR související s XAML

Správné přiřazení typů, členů a sestavení je důležité pro vykazování informací o systému typu XAML do služby .NET XAML Services. Hlášení informací o typu systému XAML je relevantní, pokud platí některá z následujících situací:

- Máte v úmyslu typy pro použití se systémy XAML, které jsou přímo založeny na .NET XAML služby XAML čtečky a Zapisovače XAML.
- Definujete nebo používáte rozhraní S Využití XAML, které je založeno na těchto čtecích čtecích a zapisovačích XAML.

Seznam jednotlivých atributů souvisejících s XAML, který je relevantní pro podporu XAML vašich vlastních typů, naleznete v [tématu Atributy CLR související s XAML pro vlastní typy a knihovny](clr-attributes-with-custom-types-and-libraries.md).

## <a name="usage"></a>Využití

Použití vlastních typů vyžaduje, aby autor značek musel mapovat předponu pro soubor sestavení a obor názvů CLR, které obsahují vlastní typ. Tento postup není v tomto tématu popsán.

## <a name="access-level"></a>Úroveň přístupu

XAML poskytuje prostředky k načtení a vytvoření `internal` instance typů, které mají úroveň přístupu. Tato funkce je k dispozici tak, aby uživatelský kód můžete definovat své vlastní typy a potom vytvořit instanci těchto tříd ze značek, která je také součástí stejného oboru kódu uživatele.

Příkladem z WPF je vždy, <xref:System.Windows.Controls.UserControl> když uživatelský kód definuje, který je určen jako způsob refaktorování chování uživatelského rozhraní, ale ne `public` jako součást jakéhokoli možného mechanismu rozšíření, který může být implikován deklarováním podpůrné třídy s úrovní přístupu. Takový <xref:System.Windows.Controls.UserControl> může být `internal` deklarován s přístupem, pokud je záložní kód zkompilován do stejného sestavení, ze kterého je odkazován jako typ XAML.

Pro aplikaci, která načte XAML pod plnou důvěryhodnost a používá <xref:System.Xaml.XamlObjectWriter>, načítání tříd s `internal` úrovní přístupu je vždy povolena.

Pro aplikaci, která načte XAML pod částečný medaiontistikou důvěryhodnosti, můžete řídit charakteristiky úrovně přístupu <xref:System.Xaml.Permissions.XamlAccessLevel> pomocí rozhraní API. Mechanismy časování (například systém šablony WPF) musí být také schopny šířit všechna oprávnění na úrovni přístupu a zachovat je pro případné vyhodnocení doby běhu; to je zpracována interně předáním <xref:System.Xaml.Permissions.XamlAccessLevel> informací.

### <a name="wpf-implementation"></a>Implementace WPF

WPF XAML používá model přístupu částečné důvěryhodnosti, kde pokud BAML <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> je načten pod částečný vztah důvěryhodnosti, přístup je omezen na sestavení, které je zdrojem BAML. Pro časově rozlišené WPF používá <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> jako mechanismus pro předávání informací o úrovni přístupu.

V terminologii WPF XAML je *interní typ* typ, který je definován stejným sestavením, které také zahrnuje odkazující XAML. Takový typ lze mapovat prostřednictvím oboru názvů XAML, který záměrně vynese sestavení `xmlns:local="clr-namespace:WPFApplication1"`= část mapování, například . Pokud BAML odkazuje na interní typ `internal` a tento typ `GeneratedInternalTypeHelper` má úroveň přístupu, vygeneruje se třída pro sestavení. Pokud se chcete `GeneratedInternalTypeHelper`vyhnout , `public` musíte buď použít úroveň přístupu, nebo musíte faktor příslušné třídy do samostatného sestavení a učinit toto sestavení závislé.

## <a name="see-also"></a>Viz také

- [Atributy CLR související s jazykem XAML pro vlastní typy a knihovny](clr-attributes-with-custom-types-and-libraries.md)
- [XAML Services](../../../api/index.md)
