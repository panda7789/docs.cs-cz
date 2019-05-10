---
title: Definování vlastních typů pro práci s technologií .NET Framework XAML Services
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: fea5c656cf5e793ca0717cf3ef60016128a942be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617295"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definování vlastních typů pro práci s technologií .NET Framework XAML Services
Při definování vlastních typů, které jsou pro obchodní objekty nebo jsou typy, které nemají závislost na určité rozhraní, jsou některé osvědčené postupy pro XAML, můžete postupovat podle. Pokud budete postupovat podle těchto postupů, můžete zjistit vlastnosti XAML stejného typu a přiřaďte jí vhodné vyjádření v datovém proudu uzlu XAML pomocí typu systému XAML rozhraní .NET Framework XAML Services a jeho XAML čtečky a zapisovače XAML. Toto téma popisuje osvědčené postupy pro definice typu, definice členů a zapisujících CLR typy nebo členy.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Zabezpečené vzory konstruktoru a definic typů pro XAML  
 Má být vytvořena jako element objektu v XAML, vlastní třídy musí splňovat následující požadavky:  
  
- Vlastní třída musí být veřejné a musí zveřejnit výchozí veřejný konstruktor (bez parametrů). (Viz následující části pro poznámky týkající se struktury).  
  
- Vlastní třída nesmí být vnořená třída. Nadbytečné "tečka" v cestě celé jméno díky dělení obor názvů třídy nejednoznačný a naruší to ostatní funkce XAML jako připojené vlastnosti.  
  
 Pokud objekt může být vytvořen jako element objektu, vytvořený objekt vyplnit formu všechny vlastnosti, které získat objekt jako jeho základní typ vlastnosti elementu.  
  
 Stále můžete zadat objekt hodnoty pro typy, které nesplňují tato kritéria, pokud povolíte převaděč hodnoty. Další informace najdete v tématu [převaděče typů a rozšíření značek pro XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Struktury  
 Struktury jsou vždycky možné zkonstruovat v XAML, podle definice CLR. Je to proto, že kompilátor CLR implicitně vytvoří výchozí konstruktor pro struktury. Tento konstruktor inicializuje všechny hodnoty vlastností, které jejich výchozích hodnotách.  
  
 V některých případech není chování výchozí konstrukci pro strukturu žádoucí. Příčinou může být struktura je určený k vyplnění hodnot a funkce koncepčně jako sjednocení. Jako sjednocení omezením hodnot může mít vzájemně se vylučující interpretace a proto nejsou žádná z její vlastnosti nastavitelná při čekání. Je například struktura, ve slovníku WPF <xref:System.Windows.GridLength>. Tyto struktury by měly implementovat konvertor typu tak, aby hodnot lze vyjádřit do formuláře atributů, pomocí řetězce vytváření názvů, které vytvářejí různé interpretace nebo režimy struktura hodnoty. Struktury by měly vystavit také podobné chování pro tvorbu kódu prostřednictvím jiného než výchozího konstruktoru.  
  
### <a name="interfaces"></a>Rozhraní  
 Rozhraní může sloužit jako základní typy členů. Systém typů XAML kontroluje seznamu přiřadit a očekává, že objekt, který je uvedený jako hodnota může být přiřazen k rozhraní. Neexistuje žádný koncept jak musí být rozhraní zobrazí jako typ XAML tak dlouho, dokud odpovídající typ přiřaditelný podporuje požadavky dané XAML konstrukce.  
  
### <a name="factory-methods"></a>Metody pro vytváření objektů  
 Metody pro vytváření objektů jsou funkce XAML 2009. Mění se zásadou XAML, že objekty musí mít výchozí konstruktory. Metody pro vytváření objektů nejsou uvedené v tomto tématu. Zobrazit [x: FactoryMethod – direktiva](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Výčty  
 Výčty mají XAML nativní typ převodu chování. Výčet konstantní názvy zadané v XAML jsou vyřešeny před nadřízený typ výčtu a vrátí hodnotu výčtu pro zápis objektu XAML.  
  
 XAML podporuje použití stylu příznaky pro výčty s <xref:System.FlagsAttribute> použít. Další informace najdete v tématu [syntaxe XAML v podrobnosti o](../wpf/advanced/xaml-syntax-in-detail.md). ([Syntaxe XAML v podrobnosti o](../wpf/advanced/xaml-syntax-in-detail.md) je určené pro cílovou skupinu WPF, ale většina informace v tomto tématu je relevantní pro XAML, která není specifická pro konkrétní implementaci rozhraní.)  
  
## <a name="member-definitions"></a>Definice členů  
 Typy lze definovat členy pro využití XAML. Je možné pro typy, které definují členy, které jsou použitelné XAML i v případě konkrétního typu se nedá použít pro XAML. To je možné z důvodu CLR dědičnosti. Tak dlouho, dokud nějaký typ, který dědí člen podporuje použití XAML jako typ a člen podporuje použití XAML pro jeho základní typ nebo má nativní syntaxe XAML k dispozici, je daný člen XAML počítačově využitelný.  
  
### <a name="properties"></a>Vlastnosti  
 Pokud definujete vlastnosti jako veřejná vlastnost CLR pomocí typické CLR `get` a `set` přístupové vzory a používání jazyka odpovídající typu systému XAML můžete nahlásit zadaná pro vlastnost jako člena s příslušnými informacemi <xref:System.Xaml.XamlMember> vlastnosti, jako například <xref:System.Xaml.XamlMember.IsReadPublic%2A> a <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Specifické vlastnosti můžete povolit syntaxe textu s použitím <xref:System.ComponentModel.TypeConverterAttribute>. Další informace najdete v tématu [převaděče typů a rozšíření značek pro XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Chybí text syntaxe nebo nativní převod XAML a neexistují další dereference, jako je například použití rozšíření značky, typ vlastnosti (<xref:System.Xaml.XamlMember.TargetType%2A> XAML zadejte system) musí být schopni vracet instanci pro zápis objektu XAML díky tomu t, že Typ cíle jako typ CLR.  
  
 Pokud používáte XAML 2009 [x: Reference – rozšíření značek](x-reference-markup-extension.md) je možné zadat hodnoty, pokud předchozí požadavky nejsou splněny; který je ale více problém použití než v případě problému definice typu.  
  
### <a name="events"></a>Události  
 Pokud definujete události jako veřejná událost CLR, typu systému XAML můžete nahlásit události jako člena s <xref:System.Xaml.XamlMember.IsEvent%2A> jako `true`. Vzájemné propojení obslužné rutiny událostí není v rámci oboru funkce rozhraní .NET Framework XAML Services; To je ponecháno na konkrétní rozhraní a implementaci.  
  
### <a name="methods"></a>Metody  
 Vložený kód pro metody není výchozí možnost XAML. Ve většině případů můžete přímo neodkazujte metoda členy z XAML a roli metod v XAML je jenom k poskytování podpory pro určité vzory XAML. [x: FactoryMethod – direktiva](x-factorymethod-directive.md) výjimka.  
  
### <a name="fields"></a>Pole  
 Pokyny k návrhu CLR Zabraňte nestatické pole. Pro statické pole se zobrazí hodnoty statických polí jen prostřednictvím [x: Static – rozšíření značek](x-static-markup-extension.md); v takovém případě nejsou dělat nic zvláštního v definici CLR vystavit pole pro [x: Static](x-static-markup-extension.md) použití.  
  
## <a name="attachable-members"></a>Připojitelná členy  
 Připojitelná členy jsou přístupné na XAML prostřednictvím na definující typ přístupového objektu metoda vzorek. Definující typ, samotný nemusí být XAML použitelné jako objekt. Ve skutečnosti se běžně používá k deklaraci třídy služby, jejichž role je vlastní připojitelný člen a implementovat související chování, ale sloužit jiné funkce, jako je například znázornění uživatelského rozhraní. Na následující oddíly, zástupný symbol *PropertyName* představuje název připojitelný člen. Tento název musí být platné v [xamlname – gramatika](xamlname-grammar.md).  
  
 Buďte opatrní kolizí název mezi tyto vzory a jiné metody typu. Pokud existuje člen, který odpovídá jednomu ze vzorů, ji lze interpretovat jako cestu připojitelný člen využití procesoru XAML i v případě, který nebyl váš záměr.  
  
#### <a name="the-getpropertyname-accessor"></a>Přístupový objekt GetPropertyName  
 Podpis pro `Get` *PropertyName* přístupový objekt musí být:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
- `target` Objektu lze zadat jako konkrétnější typ ve vaší implementaci. Může být využit k určení oboru využití připojitelný člen; použití mimo určený rozsah vyvolají výjimky neplatné přetypování, které jsou pak prezentované podle Chyba analýzy XAML. Název parametru `target` není povinné, ale má název `target` konvencí ve většině implementací.  
  
- Návratová hodnota se dá nastavit jako konkrétnější typ ve vaší implementaci.  
  
 Pro podporu <xref:System.ComponentModel.TypeConverter> povoleno textová syntaxe pro použití atributu připojitelný člen použít <xref:System.ComponentModel.TypeConverterAttribute> k `Get` *PropertyName* přistupujícího objektu. Použití `get` místo `set` se může zdát nonintuitive; tato úmluva však může podporovat koncept jen pro čtení připojitelná členů, které jsou serializovatelné, což je užitečné v situacích, návrháře.  
  
#### <a name="the-setpropertyname-accessor"></a>Přístupový objekt SetPropertyName  
 Podpis pro sadu*PropertyName* přístupový objekt musí být:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
- `target` Objektu lze zadat jako konkrétnější typ v implementaci, se stejnými logiky a důsledky, jak je popsáno v předchozí části.  
  
- `value` Objektu lze zadat jako konkrétnější typ ve vaší implementaci.  
  
 Mějte na paměti, že hodnota pro tuto metodu je vstup z využití XAML, obvykle do formuláře atributů. Z formuláře atributů musí být hodnota převaděč podporu syntaxe textu, a atribut na `Get` *PropertyName* přistupujícího objektu.  
  
### <a name="attachable-member-stores"></a>Připojitelný člen úložišť  
 Přístupové metody obvykle nejsou dost prostředků připojitelný člen hodnoty umístí do grafu objektu, nebo k načtení hodnoty z objektu grafu a je správně serializovat. Tuto funkčnost `target` objekty v předchozích podpisech přístupový objekt musí být schopné ukládání hodnot. Mechanismus úložiště by měl být konzistentní s připojitelný člen zásadě, že člen je připojitelná k cíli, kde připojitelný člen není v seznamu členů. Rozhraní .NET framework XAML Services poskytuje techniku implementaci pro prostřednictvím rozhraní API jsou uloženy připojitelný člen <xref:System.Xaml.IAttachedPropertyStore> a <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> uživatelé vytvářející obsah XAML používá ke zjišťování implementace úložiště a by měla být implementována na typ, který je `target` přistupujících objektů. Statické <xref:System.Xaml.AttachablePropertyServices> rozhraní API se používají v těle přístupové objekty a odkazovat na připojitelný člen podle jeho <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atributy CLR související s jazykem XAML  
 Správně zapisujících typy, členy a sestavení je důležité, aby sestavy informací o typu systému XAML pro rozhraní .NET Framework XAML Services. Toto je relevantní, pokud máte v úmyslu vaše typy pro použití s XAML systémy, které jsou přímo založena na rozhraní .NET Framework XAML Services XAML čtečky a zapisovače XAML, nebo pokud definujete nebo pomocí rozhraní využívá XAML, která je založena na těchto XAML čtečky a zapisovače XAML.  
  
 Výpis každého atributu souvisejícím s XAML, který je relevantní informace o podpoře XAML vlastní typy, najdete v části [XAML-Related CLR atributy pro vlastní typy a knihovny](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Použití  
 Použití vlastních typů vyžaduje, že autor značky musí být namapovaný předponu pro sestavení a názvový prostor CLR, které obsahují vlastního typu. Tento postup není uvedeno v tomto tématu.  
  
## <a name="access-level"></a>Úroveň přístupu  
 XAML poskytuje prostředky pro načtení a vytvoření instancí typů, které mají `internal` úroveň přístupu. Tato možnost je poskytována tak, aby uživatelský kód můžete definovat vlastní typy a pak vytvoření instance těchto tříd z kódu, který je také součástí stejného kódu oboru uživatele.  
  
 Příkladem pro WPF je vždy, když uživatelský kód definuje <xref:System.Windows.Controls.UserControl> , který je určený jako způsob, jak Refaktorovat chování uživatelského rozhraní, ale ne jako součást každý použitý mechanizmus možné rozšíření, která může být implicitní podpůrnou třídu s deklarací `public` úroveň přístupu. Tyto <xref:System.Windows.Controls.UserControl> mohou být deklarovány s `internal` přistupovat v případě, že záložní kód je zkompilován do stejného sestavení, ze kterého se na ni odkazuje jako typ XAML.  
  
 Pro aplikace, která načte XAML v úplném vztahu důvěryhodnosti a použije <xref:System.Xaml.XamlObjectWriter>, načítání tříd pomocí `internal` úroveň přístupu je vždy povolena.  
  
 Pro aplikace, která načte XAML v částečném vztahu důvěryhodnosti, můžete nastavit vlastnosti úrovně přístupu pomocí <xref:System.Xaml.Permissions.XamlAccessLevel> rozhraní API. Navíc musí být schopen rozšířily úrovně oprávnění a zachovat pro zkušební případnou běhu; mechanismy odložení (jako je například systém šablony WPF) To je interně zpracována třídou předání <xref:System.Xaml.Permissions.XamlAccessLevel> informace.  
  
### <a name="wpf-implementation"></a>Implementaci WPF  
 WPF XAML používá model přístupu částečným vztahem důvěryhodnosti, kam Pokud BAML je načten v částečném vztahu důvěryhodnosti, je přístup omezen na <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> pro sestavení, který je zdrojem BAML. Používá pro odložení, WPF <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> jako mechanismus pro předávání informací úrovně přístupu.  
  
 V terminologii WPF XAML *vnitřní typ* je typ, který je definován ve stejném sestavení, která zahrnuje i odkazující XAML. Takový typ lze mapovat pomocí oboru názvů XAML, která záměrně vynechá sestavení = část mapování, například `xmlns:local="clr-namespace:WPFApplication1"`.  Pokud BAML odkazuje na vnitřní typ a zda má typ `internal` přístup k úrovni, tím se vygeneruje `GeneratedInternalTypeHelper` třídy pro sestavení. Pokud chcete, aby se zabránilo `GeneratedInternalTypeHelper`, buď musíte použít `public` přístup k úrovni, nebo musí zohlednit příslušné třídě do samostatných sestavení a ujistěte se, že sestavení závislé.  
  
## <a name="see-also"></a>Viz také:

- [Atributy CLR související s jazykem XAML pro vlastní typy a knihovny](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML Services](index.md)
