---
title: Migrace Newtonsoft.Json z System.Text.Json do - .NET
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0828a5654171df39230055215903d3a49690155d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739237"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Jak migrovat z Newtonsoft.Json na System.Text.Json

Tento článek ukazuje, jak migrovat z <xref:System.Text.Json> [Newtonsoft.Json](https://www.newtonsoft.com/json) do .

Obor `System.Text.Json` názvů poskytuje funkce pro serializaci a rekonstrukci z JavaScript unotace objektu (JSON). Knihovna `System.Text.Json` je součástí sdíleného rozhraní [.NET Core 3.0.](https://aka.ms/netcore3download) Pro ostatní cílové architektury nainstalujte balíček [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet. Balíček podporuje:

* .NET Standard 2.0 a novější verze
* Rozhraní .NET Framework 4.7.2 a novější verze
* .NET Jádro 2.0, 2.1 a 2.2

`System.Text.Json`zaměřuje především na dodržování výkonu, zabezpečení a standardů. Má některé klíčové rozdíly ve výchozím chování a nemá za cíl `Newtonsoft.Json`mít paritu funkcí s . Pro některé `System.Text.Json` scénáře nemá žádné předdefinované funkce, ale existují doporučená řešení. Pro jiné scénáře jsou zástupná řešení nepraktická. Pokud vaše žádost závisí na chybějící funkci, [zvažte podání problému,](https://github.com/dotnet/runtime/issues/new) abyste zjistili, zda lze přidat podporu pro váš scénář.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Většina tohoto článku je o <xref:System.Text.Json.JsonSerializer> použití rozhraní API, ale obsahuje <xref:System.Text.Json.JsonDocument> také pokyny, jak používat (který <xref:System.Text.Json.Utf8JsonReader>představuje <xref:System.Text.Json.Utf8JsonWriter> model objektu dokumentu nebo DOM), a typy.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Tabulka rozdílů mezi Newtonsoft.Json a System.Text.Json

V následující `Newtonsoft.Json` tabulce `System.Text.Json` jsou uvedeny funkce a ekvivalenty. Ekvivalenty spadají do těchto kategorií:

* Podporováno vestavěnou funkcí. Získání podobné `System.Text.Json` chování z může vyžadovat použití atributu nebo globální možnost.
* Není podporováno, je možné řešení. Zástupná řešení jsou [vlastní převaděče](system-text-json-converters-how-to.md), které `Newtonsoft.Json` nemusí poskytovat úplnou paritu s funkcemi. Pro některé z nich ukázkový kód je k dispozici jako příklady. Pokud se spoléháte na tyto `Newtonsoft.Json` funkce, migrace bude vyžadovat změny v modelech objektů .NET nebo jiné změny kódu.
* Není podporováno, řešení není praktické ani možné. Pokud se spoléháte na tyto `Newtonsoft.Json` funkce, migrace nebude možné bez významných změn.

| Newtonsoft.Json funkce                               | System.Text.Json ekvivalent |
|-------------------------------------------------------|-----------------------------|
| Deserializace bez rozlišování velkých a malých písmen ve výchozím nastavení           | ✔️ [PropertyNameCaseInsensitive globální nastavení](#case-insensitive-deserialization) |
| Názvy vlastností camel-case                             | Globální nastavení ✔️ [PropertyNamingPolicy](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Minimální unikání znaků                            | ✔️ [Strict znak unikání, konfigurovatelné](#minimal-character-escaping) |
| `NullValueHandling.Ignore`globální nastavení             | ✔️ [globální možnost Ignorovathodnoty NullValues](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Povolit komentáře                                        | ✔️ [Globální nastavení Zpracování komentáře](#comments) |
| Povolit koncová čárky                                 | ✔️ [Globální nastavení AllowTrailingCommas](#trailing-commas) |
| Registrace vlastního převaděče                         | ✔️ [pořadí priorit se liší](#converter-registration-precedence) |
| Ve výchozím nastavení není žádná maximální hloubka                           | ✔️ [Výchozí maximální hloubka 64, konfigurovatelná](#maximum-depth) |
| Podpora široké škály typů                    | ⚠️[Některé typy vyžadují vlastní převaděče](#types-without-built-in-support) |
| Deserializovat řetězce jako čísla                        | ⚠️[Není podporováno, řešení, ukázka](#quoted-numbers) |
| Rekonstruovat `Dictionary` pomocí klíče bez řetězce          | ⚠️[Není podporováno, řešení, ukázka](#dictionary-with-non-string-key) |
| Polymorfní serializace                             | ⚠️[Není podporováno, řešení, ukázka](#polymorphic-serialization) |
| Polymorfní deserializace                           | ⚠️[Není podporováno, řešení, ukázka](#polymorphic-deserialization) |
| Deserializovat odvozený typ `object` do vlastností      | ⚠️[Není podporováno, řešení, ukázka](#deserialization-of-object-properties) |
| Deserializovat literál `null` JSON na typy hodnot, které nesmožno null | ⚠️[Není podporováno, řešení, ukázka](#deserialize-null-to-non-nullable-type) |
| Deserializovat na neměnné třídy a struktury          | ⚠️[Není podporováno, řešení, ukázka](#deserialize-to-immutable-classes-and-structs) |
| Atribut `[JsonConstructor]`                         | ⚠️[Není podporováno, řešení, ukázka](#specify-constructor-to-use) |
| `Required`nastavení `[JsonProperty]` atributu        | ⚠️[Není podporováno, řešení, ukázka](#required-properties) |
| `NullValueHandling`nastavení `[JsonProperty]` atributu | ⚠️[Není podporováno, řešení, ukázka](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`nastavení `[JsonProperty]` atributu | ⚠️[Není podporováno, řešení, ukázka](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`globální nastavení                 | ⚠️[Není podporováno, řešení, ukázka](#conditionally-ignore-a-property) |
| `DefaultContractResolver`vyloučit vlastnosti       | ⚠️[Není podporováno, řešení, ukázka](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` nastavení   | ⚠️[Není podporováno, řešení, ukázka](#specify-date-format) |
| Zpětná volání                                             | ⚠️[Není podporováno, řešení, ukázka](#callbacks) |
| Podpora veřejných i neveřejných oblastí              | ⚠️[Není podporováno, řešení](#public-and-non-public-fields) |
| Podpora interních a soukromých správců a realitních společností | ⚠️[Není podporováno, řešení](#internal-and-private-property-setters-and-getters) |
| Metoda `JsonConvert.PopulateObject`                   | ⚠️[Není podporováno, řešení](#populate-existing-objects) |
| `ObjectCreationHandling`globální nastavení               | ⚠️[Není podporováno, řešení](#reuse-rather-than-replace-properties) |
| Přidat do kolekcí bez nastavení                    | ⚠️[Není podporováno, řešení](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`globální nastavení           | ❌[Není podporováno](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`globální nastavení                | ❌[Není podporováno](#preserve-object-references-and-handle-loops) |
| Podpora `System.Runtime.Serialization` atributů | ❌[Není podporováno](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`globální nastavení                | ❌[Není podporováno](#missingmemberhandling) |
| Povolit názvy vlastností bez uvozovek                   | ❌[Není podporováno](#json-strings-property-names-and-string-values) |
| Povolit jednoduché uvozovky kolem hodnot řetězce              | ❌[Není podporováno](#json-strings-property-names-and-string-values) |
| Povolit hodnoty JSON bez řetězce pro vlastnosti řetězce    | ❌[Není podporováno](#non-string-values-for-string-properties) |

Toto není vyčerpávající seznam `Newtonsoft.Json` funkcí. Seznam obsahuje mnoho scénářů, které byly požadovány v [githubproblémy](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) nebo [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) příspěvky. Pokud implementujete řešení pro jeden z zde uvedených scénářů, který aktuálně nemá ukázkový kód, a pokud chcete sdílet řešení, vyberte **tuto stránku** v části **Zpětná vazba** v dolní části této stránky. To vytvoří problém v úložišti GitHub této dokumentace a zobrazí jej v části **Zpětná vazba** na této stránce.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Rozdíly ve výchozím chování JsonSerializer ve srovnání s Newtonsoft.Json

<xref:System.Text.Json>je ve výchozím nastavení přísný a vyhýbá se jakémukoli hádání nebo interpretaci jménem volajícího s důrazem na deterministické chování. Knihovna je záměrně navržena tímto způsobem pro výkon a zabezpečení. `Newtonsoft.Json`je ve výchozím nastavení flexibilní. Tento zásadní rozdíl v návrhu je za mnoho z následujících konkrétních rozdílů ve výchozím chování.

### <a name="case-insensitive-deserialization"></a>Deserializace bez rozlišování velkých a malých písmen

Během deserializace `Newtonsoft.Json` se ve výchozím nastavení porovnává název vlastnosti bez rozlišování velkých a malých písmen. Výchozí <xref:System.Text.Json> hodnota rozlišuje malá a velká písmena, což poskytuje lepší výkon, protože provádí přesnou shodu. Informace o tom, jak provést porovnávání bez rozlišování velkých a malých písmen, naleznete [v tématu porovnávání vlastností bez rozlišování velkých a malých písmen](system-text-json-how-to.md#case-insensitive-property-matching).

Pokud používáte `System.Text.Json` nepřímo pomocí ASP.NET Core, nemusíte dělat nic, abyste získali chování jako `Newtonsoft.Json`. ASP.NET Core určuje nastavení [názvů vlastností camel-casing](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) a porovnávání `System.Text.Json`bez rozlišování velkých a malých písmen při použití .

### <a name="minimal-character-escaping"></a>Minimální unikání znaků

Během `Newtonsoft.Json` serializace, je relativně tolerantní o pronájem znaky prostřednictvím bez jejich úniku. To znamená, že je nenahradí místem, `\uxxxx` kde `xxxx` je bod kódu znaku. Pokud jim unikne, činí tak tím, že vyzařuje `\` znak `"` `\"`před znakem (například se stává). <xref:System.Text.Json>ve výchozím nastavení unikne více znaků, aby byla zajištěna ochrana proti skriptování mezi weby (XSS) nebo útokům zpřístupnění informací, a to pomocí šestiznakové sekvence. `System.Text.Json`ve výchozím nastavení unikne všem znakům, které nejsou znaky ASCII, `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json`takže v případě použití v . `System.Text.Json`také ve výchozím nastavení unikne znakům citlivým na HTML. Informace o tom, jak `System.Text.Json` přepsat výchozí chování, naleznete v [tématu Vlastní kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Komentáře

Během deserializace `Newtonsoft.Json` ignoruje komentáře v JSON ve výchozím nastavení. Výchozí <xref:System.Text.Json> je vyvolat výjimky pro komentáře, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) neobsahuje. Informace o povolení komentářů naleznete v tématu [Povolit komentáře a koncová čárky](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Koncová čárka

Během deserializace `Newtonsoft.Json` ignoruje koncové čárky ve výchozím nastavení. Také ignoruje více koncových čárek (například `[{"Color":"Red"},{"Color":"Green"},,]`). Výchozí <xref:System.Text.Json> je vyvolat výjimky pro koncové čárky, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) neumožňuje. Informace o tom, `System.Text.Json` jak je přijmout, naleznete v tématu [Povolit komentáře a koncová čárky](system-text-json-how-to.md#allow-comments-and-trailing-commas). Neexistuje žádný způsob, jak povolit více koncové čárky.

### <a name="converter-registration-precedence"></a>Priorita registrace převaděče

Registrační `Newtonsoft.Json` priorita pro vlastní převaděče je následující:

* Atribut na vlastnosti
* Atribut na typu
* Kolekce [převaděčů](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Toto pořadí znamená, že `Converters` vlastní převaděč v kolekci je přepsán převaděč, který je registrován použitím atributu na úrovni typu. Obě tyto registrace jsou přepsány atributem na úrovni vlastnosti.

Priorita <xref:System.Text.Json> registrace pro vlastní převaděče se liší:

* Atribut na vlastnosti
* <xref:System.Text.Json.JsonSerializerOptions.Converters>Kolekce
* Atribut na typu

Rozdíl je v tom, že `Converters` vlastní převaděč v kolekci přepíše atribut na úrovni typu. Záměrem tohoto pořadí priorit je provést změny za běhu přepsat volby návrhu. Neexistuje žádný způsob, jak změnit prioritu.

Další informace o registraci vlastního převaděče naleznete [v tématu Registrace vlastního převaděče](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>Maximální hloubka

`Newtonsoft.Json`nemá maximální limit hloubky ve výchozím nastavení. Pro <xref:System.Text.Json> tam je výchozí limit 64, a to je <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>konfigurovatelné nastavením .

### <a name="json-strings-property-names-and-string-values"></a>Řetězce JSON (názvy vlastností a hodnoty řetězců)

Během deserializace `Newtonsoft.Json` přijímá názvy vlastností obklopené dvojitými uvozovkami, jednoduchými uvozovkami nebo bez uvozovek. Přijímá řetězcové hodnoty obklopené dvojitými uvozovkami nebo jednoduchými uvozovkami. Například `Newtonsoft.Json` přijímá následující JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`přijímá pouze názvy vlastností a hodnoty řetězců v uvozovkách, protože tento formát je vyžadován specifikací [RFC 8259](https://tools.ietf.org/html/rfc8259) a je jediným formátem považovaným za platný JSON.

Hodnota uzavřená v jednoduchých uvozovkách má za následek [JsonException](xref:System.Text.Json.JsonException) s následující zprávou:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Hodnoty bez řetězce pro vlastnosti řetězce

`Newtonsoft.Json`přijímá hodnoty bez řetězce, například číslo nebo `true` literály a `false`, pro rekonstrukci vlastností řetězce typu. Zde je příklad JSON, `Newtonsoft.Json` který úspěšně reserializuje do následující třídy:

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json`nerekonstruuje hodnoty bez řetězce do vlastností řetězce. Hodnota bez řetězce přijatá pro pole řetězce má za následek [výjimku JsonException](xref:System.Text.Json.JsonException) s následující zprávou:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scénáře používající JsonSerializer, které vyžadují řešení

Následující scénáře nejsou podporovány vestavěné funkce, ale řešení jsou možné. Zástupná řešení jsou [vlastní převaděče](system-text-json-converters-how-to.md), které `Newtonsoft.Json` nemusí poskytovat úplnou paritu s funkcemi. Pro některé z nich ukázkový kód je k dispozici jako příklady. Pokud se spoléháte na tyto `Newtonsoft.Json` funkce, migrace bude vyžadovat změny v modelech objektů .NET nebo jiné změny kódu.

### <a name="types-without-built-in-support"></a>Typy bez vestavěné podpory

<xref:System.Text.Json>neposkytuje integrovanou podporu pro následující typy:

* <xref:System.Data.DataTable>a související typy
* Typy Jazyka F#, například [discriminated unions](../../fsharp/language-reference/discriminated-unions.md), [typy záznamů](../../fsharp/language-reference/records.md)a anonymní [typy záznamů](../../fsharp/language-reference/anonymous-records.md).
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>a související generické typy

Vlastní převaděče lze implementovat pro typy, které nemají integrovanou podporu.

### <a name="quoted-numbers"></a>Citovaná čísla

`Newtonsoft.Json`může serializovat nebo rekonstruovat čísla reprezentovaná řetězci JSON (obklopená uvozovkami). Může například přijmout: `{"DegreesCelsius":"23"}` místo `{"DegreesCelsius":23}`. Chcete-li povolit toto chování v <xref:System.Text.Json>, implementujte vlastní převaděč, jako je následující příklad. Převaděč zpracovává vlastnosti definované jako `long`:

* Serializuje je jako řetězce JSON.
* Přijímá json čísla a čísla v uvozovkách při rekonstrukci.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Zaregistrujte tento vlastní převaděč `long` [pomocí atributu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) na jednotlivé <xref:System.Text.Json.JsonSerializerOptions.Converters> vlastnosti nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce.

### <a name="dictionary-with-non-string-key"></a>Slovník s neřetězcovým klíčem

`Newtonsoft.Json`podporuje kolekce typu `Dictionary<TKey, TValue>`. Integrovaná podpora kolekcí slovníků <xref:System.Text.Json> v aplikacích je omezena na `Dictionary<string, TValue>`. To znamená, že klíč musí být řetězec.

Chcete-li podporovat slovník s celé číslo nebo jiný typ jako klíč, vytvořte převaděč, jako je příklad v [Jak psát vlastní převaděče](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Polymorfní serializace

`Newtonsoft.Json`automaticky provádí polymorfní serializaci. Informace o omezených polymorfních možnostech serializace v tématu <xref:System.Text.Json> [Serializace vlastností odvozených tříd](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Řešení popsané je definovat vlastnosti, které mohou obsahovat `object`odvozené třídy jako typ . Pokud to není možné, další možností je vytvořit `Write` převaděč s metodou pro celou hierarchii typu dědičnosti, jako je příklad v [návodu k zápisu vlastních převaděčů](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Polymorfní deserializace

`Newtonsoft.Json`má `TypeNameHandling` nastavení, které přidává metadata názvu typu do JSON při serializaci. Používá metadata při deserializaci k polymorfní deserializaci. <xref:System.Text.Json>může provést omezený rozsah [polymorfní serializace,](system-text-json-how-to.md#serialize-properties-of-derived-classes) ale ne polymorfní deserializace.

Chcete-li podporovat polymorfní deserializaci, vytvořte převaděč jako v příkladu V [části Jak psát vlastní převaděče](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="deserialization-of-object-properties"></a>Deserializace vlastností objektu

Při `Newtonsoft.Json` deserializaci do <xref:System.Object>, to:

* Odvodí typ primitivních hodnot v datové části `null`JSON (jiné než) a vrátí `string`uložený , `long` `double`, `boolean`, nebo `DateTime` jako zabalený objekt. *Primitivní hodnoty* jsou jednotlivé hodnoty JSON, například `true`číslo `false`JSON, řetězec , nebo `null`.
* Vrátí `JObject` hodnotu a nebo `JArray` pro komplexní hodnotu v datové části JSON. *Komplexní hodnoty* jsou kolekce párů json klíč-hodnota`{}`v rámci závorek`[]`( ) nebo seznamy hodnot v závorkách ( ). Vlastnosti a hodnoty v závorkách nebo závorkách mohou mít další vlastnosti nebo hodnoty.
* Vrátí odkaz null, pokud datová část má literál `null` JSON.

<xref:System.Text.Json>ukládá krabici `JsonElement` pro primitivní i složité hodnoty <xref:System.Object>při každé rekonstrukci na , například:

* Vlastnost. `object`
* Hodnota `object` slovníku.
* Hodnota `object` pole.
* Kořen `object`.

Však `System.Text.Json` zachází `null` stejně `Newtonsoft.Json` jako a vrátí odkaz null, `null` pokud datová část má literál JSON v něm.

Chcete-li implementovat `object` odvození typu pro vlastnosti, vytvořte převaděč jako v příkladu v [části Jak psát vlastní převaděče](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="deserialize-null-to-non-nullable-type"></a>Rekonstruovat hodnotu null na typ, který lze neutužit

`Newtonsoft.Json`nevyvolá výjimku v následujícím scénáři:

* `NullValueHandling`je nastavena na `Ignore`, a
* Během deserializace JSON obsahuje hodnotu null pro typ hodnoty, kterou nelze hodnotu nehodnotitelnou hodnotu.

Ve stejném scénáři <xref:System.Text.Json> vyvolá výjimku. (Odpovídající nastavení null <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>zpracování je .)

Pokud vlastníte cílový typ, nejlepším řešením je, aby se dotyčná vlastnost `int` `int?`mohla změnit (například změnit na).

Dalším zástupem je vytvoření převaděče pro typ, například následující `DateTimeOffset` příklad, který zpracovává hodnoty null pro typy:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu na vlastnost](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

**Poznámka:** Předchozí převaděč zpracovává hodnoty null `Newtonsoft.Json` **jinak** než u pocos, které určují výchozí hodnoty. Předpokládejme například, že následující kód představuje cílový objekt:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

A předpokládejme, že následující JSON je deserializován pomocí předchozího převaděče:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializaci `Date` má vlastnost 1/1/0001 (`default(DateTimeOffset)`), to znamená, že hodnota nastavená v konstruktoru je přepsána. Vzhledem ke stejnému POCO `Newtonsoft.Json` a JSON, by deserializace opustit `Date` 1/1/2001 v majetku.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Deserializovat na neměnné třídy a struktury

`Newtonsoft.Json`můžete rekonstruovat na neměnné třídy a struktury, protože můžete použít konstruktory, které mají parametry. <xref:System.Text.Json>podporuje pouze veřejné konstruktory bez parametrů. Jako řešení můžete volat konstruktor s parametry ve vlastním převaděči.

Zde je neměnná struktura s více parametry konstruktoru:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

A tady je konvertor, který serializuje a reserializuje tuto strukturu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Zaregistrujte tento vlastní převaděč <xref:System.Text.Json.JsonSerializerOptions.Converters> [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce.

Příklad podobného převaděče, který zpracovává otevřené obecné vlastnosti, naleznete [v předdefinovaném převaděči pro dvojice klíč-hodnota](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Určení konstruktoru, který se má použít

Atribut `Newtonsoft.Json` `[JsonConstructor]` umožňuje určit, který konstruktor volat při rekonstrukci na POCO. <xref:System.Text.Json>podporuje pouze konstruktory bez parametrů. Jako řešení můžete volat podle toho, co konstruktor, který potřebujete ve vlastním převaděči. Viz příklad pro [Deserialize neměnné třídy a struktury](#deserialize-to-immutable-classes-and-structs).

### <a name="required-properties"></a>Požadované vlastnosti

V `Newtonsoft.Json`oblasti zadáte, že vlastnost `Required` je `[JsonProperty]` vyžadována nastavením atributu. `Newtonsoft.Json`vyvolá výjimku, pokud není přijata žádná hodnota v JSON pro vlastnost označenou jako požadovaná.

<xref:System.Text.Json>nevyvolá výjimku, pokud není přijata žádná hodnota pro jednu z vlastností cílového typu. Například pokud máte `WeatherForecast` třídu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Následující JSON je deserializován bez chyby:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Chcete-li provést selhání `Date` deserializace, pokud žádná vlastnost je v JSON, implementujte vlastní převaděč. Následující ukázkový kód převaděče `Date` vyvolá výjimku, pokud vlastnost není nastavena po dokončení deserializace:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu na poco třídy](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Pokud budete postupovat podle tohoto vzoru, nepředávají v options <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.JsonSerializer.Deserialize%2A>objektu při rekurzivně volání nebo . Options Objekt obsahuje <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> kolekci. Pokud jej předáte `Serialize` `Deserialize`do nebo , vlastní převaděč volá do sebe, takže nekonečné smyčky, která má za následek výjimku přetečení zásobníku. Pokud výchozí možnosti nejsou proveditelné, vytvořte novou instanci možností s potřebným nastavením. Tento přístup bude pomalý, protože každá nová instance ukládá do mezipaměti nezávisle.

Předchozí kód převaděče je zjednodušený příklad. Další logika by byla vyžadována, pokud potřebujete zpracovat atributy (například [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) nebo různé možnosti (například vlastní kodéry). Ukázkový kód také nezpracovává vlastnosti, pro které je v konstruktoru nastavena výchozí hodnota. A tento přístup nerozlišuje mezi následujícími scénáři:

* V JSON chybí vlastnost.
* Vlastnost pro typ s nulovou hodnotou je k dispozici v JSON, ale hodnota je `int`výchozí pro typ, například nula pro .
* Vlastnost pro typ hodnoty s možnou hodnotou null je k dispozici v JSON, ale hodnota je null.

### <a name="conditionally-ignore-a-property"></a>Podmíněné ignorování vlastnosti

`Newtonsoft.Json`má několik způsobů, jak podmíněně ignorovat vlastnost při serializaci nebo deserializaci:

* `DefaultContractResolver`umožňuje vybrat vlastnosti, které chcete zahrnout nebo vyloučit, na základě libovolných kritérií.
* Nastavení `NullValueHandling` `DefaultValueHandling` a `JsonSerializerSettings` na umožňují určit, že všechny vlastnosti nulové hodnoty nebo výchozí hodnoty by měly být ignorovány.
* Nastavení `NullValueHandling` `DefaultValueHandling` a na `[JsonProperty]` atribut udáváte jednotlivé vlastnosti, které by měly být ignorovány při nastavení na hodnotu null nebo výchozí hodnotu.

<xref:System.Text.Json>Poskytuje následující způsoby, jak vynechat vlastnosti při serializaci:

* Atribut [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) na vlastnost způsobí, že vlastnost vynechat z JSON během serializace.
* Globální možnost [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) umožňuje vyloučit všechny vlastnosti nulové hodnoty.
* Globální volba [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) umožňuje vyloučit všechny vlastnosti jen pro čtení.

Tyto možnosti vám **neumožňují:**

* Ignorujte všechny vlastnosti, které mají výchozí hodnotu pro typ.
* Ignorujte vybrané vlastnosti, které mají výchozí hodnotu pro typ.
* Ignorovat vybrané vlastnosti, pokud je jejich hodnota null.
* Ignorovat vybrané vlastnosti na základě libovolných kritérií vyhodnocováno za běhu.

Pro tuto funkci můžete napsat vlastní převaděč. Zde je ukázka POCO a vlastní převaděč pro něj, který ilustruje tento přístup:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Převaděč `Summary` způsobí, že vlastnost vynechat ze serializace, pokud jeho hodnota je null, prázdný řetězec nebo "Není k dispozici".

Zaregistrujte tento vlastní převaděč [pomocí atributu na třídu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Tento přístup vyžaduje další logiku, pokud:

* POCO obsahuje komplexní vlastnosti.
* Je třeba zpracovat atributy, jako `[JsonIgnore]` jsou nebo možnosti, jako jsou vlastní kodéry.

### <a name="specify-date-format"></a>Zadat formát data

`Newtonsoft.Json`Poskytuje několik způsobů, jak `DateTime` `DateTimeOffset` řídit, jak jsou vlastnosti a typy serializovány a deserializovány:

* Toto `DateTimeZoneHandling` nastavení lze použít k `DateTime` serializaci všech hodnot jako data UTC.
* Nastavení `DateFormatString` a `DateTime` převaděče lze použít k přizpůsobení formátu kalendářních řetězců.

V <xref:System.Text.Json>, jediný formát, který má vestavěnou podporu je ISO 8601-1:2019, protože je široce přijat, jednoznačný a dělá přesně zpáteční lety. Chcete-li použít jiný formát, vytvořte vlastní převaděč. Další informace naleznete [v tématech Podpora DateTime a DateTimeOffset v souborech System.Text.Json](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Zpětná volání

`Newtonsoft.Json`umožňuje spustit vlastní kód na několika místech v procesu serializace nebo deserializace:

* OnDeserializing (při zahájení rekonstruovat objekt)
* OnDeserialized (po dokončení deserializace objektu)
* OnSerializace (při zahájení serializovat objekt)
* OnSerialized (po dokončení serializace objektu)

V <xref:System.Text.Json>, můžete simulovat zpětná volání napsáním vlastního převaděče. Následující příklad ukazuje vlastní převaděč pro POCO. Převaděč obsahuje kód, který zobrazuje zprávu v `Newtonsoft.Json` každém bodě, který odpovídá zpětnému volání.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu na třídu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Pokud používáte vlastní převaděč, který následuje za předchozí ukázkou:

* Kód `OnDeserializing` nemá přístup k nové instanci POCO. Chcete-li manipulovat s novou instancí POCO na začátku rekonstrukce, vložte tento kód do konstruktoru POCO.
* Při rekurzivního volání `Serialize` nebo `Deserialize`. Options Objekt obsahuje `Converters` kolekci. Pokud jej předáte `Serialize` `Deserialize`do nebo , převaděč bude použit, takže nekonečné smyčky, která má za následek výjimku přetečení zásobníku.

### <a name="public-and-non-public-fields"></a>Veřejná a neveřejná pole

`Newtonsoft.Json`můžete serializovat a rekonstruovat pole, jakož i vlastnosti. <xref:System.Text.Json>pracuje pouze s veřejnými nemovitostmi. Vlastní převaděče mohou poskytnout tuto funkci.

### <a name="internal-and-private-property-setters-and-getters"></a>Interní a soukromé nemovitosti seřizovači a getters

`Newtonsoft.Json`můžete použít soukromé a interní vlastnosti setters a getters přes `JsonProperty` atribut. <xref:System.Text.Json>podporuje pouze veřejné settery. Vlastní převaděče mohou poskytnout tuto funkci.

### <a name="populate-existing-objects"></a>Naplnění existujících objektů

Metoda `JsonConvert.PopulateObject` v `Newtonsoft.Json` deserializes dokumentu JSON na existující instanci třídy, namísto vytvoření nové instance. <xref:System.Text.Json>vždy vytvoří novou instanci cílového typu pomocí výchozího veřejného konstruktoru bez parametrů. Vlastní převaděče lze rekonstruovat do existující instance.

### <a name="reuse-rather-than-replace-properties"></a>Opětovné použití místo nahrazení vlastností

Nastavení `Newtonsoft.Json` `ObjectCreationHandling` umožňuje určit, že objekty ve vlastnostech by měly být znovu použity, nikoli nahrazeny během deserializace. <xref:System.Text.Json>vždy nahradí objekty ve vlastnostech.  Vlastní převaděče mohou poskytnout tuto funkci.

### <a name="add-to-collections-without-setters"></a>Přidat do kolekcí bez nastavení

Během deserializace `Newtonsoft.Json` přidá objekty do kolekce i v případě, že vlastnost nemá žádné nastavení. <xref:System.Text.Json>ignoruje vlastnosti, které nemají nastavení. Vlastní převaděče mohou poskytnout tuto funkci.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Scénáře, které JsonSerializer aktuálně nepodporuje

Pro následující scénáře nejsou praktická nebo možná zástupná řešení. Pokud se spoléháte na tyto `Newtonsoft.Json` funkce, migrace nebude možné bez významných změn.

### <a name="preserve-object-references-and-handle-loops"></a>Zachovat odkazy na objekty a smyčky popisovačů

Ve výchozím `Newtonsoft.Json` nastavení serializuje podle hodnoty. Například pokud objekt obsahuje dvě vlastnosti, které `Person` obsahují odkaz na `Person` stejný objekt, hodnoty vlastností tohoto objektu jsou duplikovány v JSON.

`Newtonsoft.Json`má `PreserveReferencesHandling` `JsonSerializerSettings` nastavení, které umožňuje serializovat podle odkazu:

* Metadata identifikátoru jsou přidána do json vytvořeného pro první `Person` objekt.
* JSON, který je vytvořen `Person` pro druhý objekt obsahuje odkaz na tento identifikátor namísto hodnoty vlastností.

`Newtonsoft.Json`má také `ReferenceLoopHandling` nastavení, které umožňuje ignorovat cyklické odkazy spíše než vyvolat výjimku.

<xref:System.Text.Json>podporuje pouze serializace podle hodnoty a vyvolá výjimku pro cyklické odkazy.

### <a name="systemruntimeserialization-attributes"></a>Atributy System.Runtime.Serialization

<xref:System.Text.Json>nepodporuje atributy z `System.Runtime.Serialization` oboru názvů, `DataMemberAttribute` například a `IgnoreDataMemberAttribute`.

### <a name="octal-numbers"></a>Osmičková čísla

`Newtonsoft.Json`považuje čísla s počáteční nulou za osmičková čísla. <xref:System.Text.Json>neumožňuje úvodní nuly, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je neumožňuje.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json`lze nakonfigurovat tak, aby vyvolávat výjimky během deserializace, pokud JSON obsahuje vlastnosti, které chybí v cílovém typu. <xref:System.Text.Json>ignoruje další vlastnosti v JSON, s výjimkou při použití [atributu [JsonExtensionData]](system-text-json-how-to.md#handle-overflow-json). Neexistuje žádné řešení pro chybějící člen funkce.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`umožňuje ladit pomocí `TraceWriter` protokolů, které jsou generovány serializací nebo rekonstrukcí. <xref:System.Text.Json>nedělá protokolování.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument a JsonElement ve srovnání s JToken (jako JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>poskytuje možnost analyzovat a sestavit dokumentový **objektový** model (DOM) z existujícídatové části JSON. DoM poskytuje náhodný přístup k datům v datové části JSON. Prvky JSON, které tvoří datovou část lze <xref:System.Text.Json.JsonElement> přistupovat prostřednictvím typu. Tento `JsonElement` typ poskytuje rozhraní API pro převod textu JSON na běžné typy .NET. `JsonDocument`zpřístupní <xref:System.Text.Json.JsonDocument.RootElement> vlastnost.

### <a name="jsondocument-is-idisposable"></a>JsonDocument je IDisposable

`JsonDocument`vytvoří zobrazení dat v paměti do sdružené vyrovnávací paměti. Proto na `JObject` `JArray` rozdíl `Newtonsoft.Json`od `JsonDocument` nebo `IDisposable` z , typ implementuje a musí být použit uvnitř using bloku.

Vrácení pouze `JsonDocument` z rozhraní API, pokud chcete převést vlastnictví životnosti a nakládat odpovědnost volajícího. Ve většině scénářů to není nutné. Pokud volající potřebuje pracovat s celým dokumentem <xref:System.Text.Json.JsonElement.Clone%2A> JSON, vraťte <xref:System.Text.Json.JsonDocument.RootElement%2A>. <xref:System.Text.Json.JsonElement> Pokud volající potřebuje pracovat s určitým prvkem v dokumentu JSON, vraťte tento <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonElement>prvek . Pokud vrátíte `RootElement` nebo dílčí prvek přímo `Clone`bez provedení , volající nebude moci `JsonElement` získat `JsonDocument` přístup vrácena po, který vlastní je uvolněn.

Zde je příklad, který vyžaduje, `Clone`abyste:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

Předchozí kód očekává, `JsonElement` že obsahuje `fileName` vlastnost. Otevře soubor JSON a `JsonDocument`vytvoří . Metoda předpokládá, že volající chce pracovat s celým `Clone` dokumentem, `RootElement`takže vrátí .

Pokud obdržíte `JsonElement` a vracíte dílčí prvek, není nutné vrátit `Clone` a dílčího prvku. Volající je zodpovědný za `JsonDocument` udržování naživu, `JsonElement` že předaný patří. Příklad:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument je jen pro čtení.

Dom <xref:System.Text.Json> nelze přidat, odebrat nebo upravit Prvky JSON. Je navržen takto pro výkon a snížit přidělení pro analýzu běžných velikostí datové části JSON (to znamená, že < 1 MB). Pokud váš scénář aktuálně používá upravitelné DOM, může být možné jedno z následujících řešení:

* Chcete-li `JsonDocument` vytvořit od nuly (to znamená, bez předání `Parse` existující datové části JSON do `Utf8JsonWriter` metody), napište text JSON pomocí a analyzovat výstup z toho vytvořit nový `JsonDocument`.
* Chcete-li `JsonDocument`upravit existující , použijte jej k zápisu textu JSON, provádění změn při `JsonDocument`psaní a analyzovat výstup z toho vytvořit nový .
* Chcete-li sloučit existující dokumenty `JObject.Merge` `JContainer.Merge` JSON, ekvivalentní nebo rozhraní API z `Newtonsoft.Json`, viz tento problém [GitHub](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement je struktura sjednocení

`JsonDocument`zpřístupňuje `RootElement` jako vlastnost <xref:System.Text.Json.JsonElement>typu , což je unie, struct typ, který zahrnuje všechny JSON element. `Newtonsoft.Json`používá vyhrazené hierarchické `JObject``JArray`typy, jako je , `JToken`, a tak dále. `JsonElement`je to, co můžete prohledávat a výčet přes a můžete použít `JsonElement` k materializaci prvků JSON do typů .NET.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Jak hledat JsonDocument a JsonElement pro dílčí prvky

Vyhledávání tokenů JSON `JObject` pomocí `JArray` `Newtonsoft.Json` nebo z mají tendenci být relativně rychlé, protože jsou vyhledávání v některých slovníku. Pro srovnání, vyhledávání `JsonElement` na vyžadují sekvenční vyhledávání vlastností a `TryGetProperty`proto je relativně pomalý (například při použití). <xref:System.Text.Json>je navržen tak, aby minimalizoval počáteční čas analýzy spíše než čas vyhledávání. Proto použijte následující přístupy k optimalizaci `JsonDocument` výkonu při prohledávání objektu:

* Použijte předdefinované čítače výčtu (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> a <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) spíše než dělat vlastní indexování nebo smyčky.
* Neprovázte sekvenční vyhledávání v celku `JsonDocument` prostřednictvím každé vlastnosti pomocí `RootElement`. Místo toho hledání na vnořené Objekty JSON na základě známé struktury dat JSON. Například `Grade` pokud hledáte vlastnost v `Student` objektech, smyčka `Student` přes objekty `Grade` a získat hodnotu pro `JsonElement` každý, `Grade` spíše než prohledávat všechny objekty hledají vlastnosti. Provedení druhé bude mít za následek zbytečné průchody přes stejná data.

Příklad kódu naleznete v tématu [Použití JsonDocument pro přístup k datům](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader ve srovnání s JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>je vysoce výkonná čtečka json kódovaná pouze s vysokým výkonem, s nízkým přidělením a dopředem pro text JSON kódovaný u UTF-8, který je přečten z [bajtu\<ReadOnlySpan>](xref:System.ReadOnlySpan%601) nebo [bajtu ReadOnlySequence\<>](xref:System.Buffers.ReadOnlySequence%601). Je `Utf8JsonReader` typ nižší úrovně, který lze použít k vytvoření vlastní analyzátory a deserializers.

V následujících částech jsou vysvětleny doporučené programovací vzory pro použití `Utf8JsonReader`.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader je ref struct

Vzhledem `Utf8JsonReader` k tomu, že typ je *ref struct*, má [určitá omezení](../../csharp/language-reference/builtin-types/struct.md#ref-struct). Například nemůže být uložen jako pole na třídu nebo strukturu než ref struct. Chcete-li dosáhnout vysokého výkonu, tento typ musí být `ref struct` protože potřebuje do mezipaměti vstupní [ReadOnlySpan\<bajt>](xref:System.ReadOnlySpan%601), který sám je ref struct. Kromě toho tento typ je proměnlivý, protože obsahuje stav. Proto **předat podle ref** spíše než podle hodnoty. Předání podle hodnoty by mělo za následek kopii struktury a změny stavu by nebyly viditelné pro volajícího. To se `Newtonsoft.Json` liší `Newtonsoft.Json` `JsonTextReader` od protože je třída. Další informace o použití struktury ref naleznete v [tématu Zápis bezpečné a efektivní kód Jazyka C#](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Přečtěte si text UTF-8

Chcete-li dosáhnout nejlepšího `Utf8JsonReader`možného výkonu při použití , přečtěte si datové části JSON, které jsou již kódovány jako text UTF-8, nikoli jako řetězce UTF-16. Příklad kódu naleznete v tématu [Filtrování dat pomocí aplikace Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Čtení pomocí streamu nebo pipereaderu

Podporuje `Utf8JsonReader` čtení z UTF-8 kódované [ReadOnlySpan\<bajt>](xref:System.ReadOnlySpan%601) nebo [ReadOnlySequence\<bajt>](xref:System.Buffers.ReadOnlySequence%601) (což je výsledek čtení z ). <xref:System.IO.Pipelines.PipeReader>

Pro synchronní čtení můžete číst datovou část JSON až do konce datového proudu do bajtového pole a předat ji do čtečky. Pro čtení z řetězce (který je kódován jako <xref:System.Text.Encoding.UTF8>UTF-16), volejte .<xref:System.Text.Encoding.GetBytes%2A> nejprve překódovat řetězec do bajtového pole kódování UTF-8. Pak to předaj. `Utf8JsonReader`

Vzhledem `Utf8JsonReader` k tomu, že vstup považuje za text JSON, značka objednávky Bajt UTF-8 (BOM) je považována za neplatnou JSON. Volající musí filtrovat, že ven před předáním dat do čtečky.

Příklady kódu naleznete [v tématu Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Čtení pomocí vícesegmentové sekvence ReadOnlySequence

Pokud je váš vstup JSON [bajt\<readonlyspan>](xref:System.ReadOnlySpan%601), každý prvek JSON lze přistupovat z `ValueSpan` vlastnosti na čtecí zařízení, jak budete procházet čtení smyčky. Však pokud je váš vstup [ReadOnlySequence\<bajt>](xref:System.Buffers.ReadOnlySequence%601) (což <xref:System.IO.Pipelines.PipeReader>je výsledkem čtení z ), některé prvky JSON může rozkročit více segmentů objektu. `ReadOnlySequence<byte>` Tyto prvky by <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> nebyly přístupné z v bloku souvislé paměti. Místo toho vždy, když `ReadOnlySequence<byte>` máte více segmentů jako vstup, dotazování <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> vlastnost na čtečku zjistit, jak získat přístup k aktuální prvek JSON. Zde je doporučený vzor:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Použití funkce ValueTextEquals pro vyhledávání názvů vlastností

Nepoužívejte <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> k porovnání bajtů po bajtech <xref:System.MemoryExtensions.SequenceEqual%2A> voláním vyhledávání názvů vlastností. Volání <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> místo, protože tato metoda unescapes všechny znaky, které jsou uvozeny v JSON. Zde je příklad, který ukazuje, jak vyhledat vlastnost s názvem "název":

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Čtení hodnot null do typů hodnot s hodnotou, které lze hodnotit

`Newtonsoft.Json`Poskytuje api, <xref:System.Nullable%601>která vrátí `ReadAsBoolean`, například `Null` `TokenType` , který zpracovává `bool?`pro vás vrácením . Předdefinovaná `System.Text.Json` api vrátí pouze typy hodnot s možnou hodnotou, která nelze hodnotu. Například <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> vrátí `bool`. Vyvolá výjimku, pokud `Null` najde v JSON. Následující příklady ukazují dva způsoby zpracování hodnot null, jeden vrácením typu hodnoty s možnou hodnotou s hodnotou s hodnotou null a jeden vrácením výchozí hodnoty:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Vícenásobné cílení

Pokud potřebujete pokračovat v `Newtonsoft.Json` používání pro určité cílové architektury, můžete více cílají a mají dvě implementace. To však není triviální a `#ifdefs` bude vyžadovat některé a zdroj duplikace. Jedním ze způsobů, jak sdílet co `ref struct` nejvíce kódu, `Newtonsoft.Json` `JsonTextReader`je vytvořit obálku kolem `Utf8JsonReader` a . Tento obal by sjednotit veřejné plochy při izolaci behaviorální rozdíly. To umožňuje izolovat změny především na konstrukci typu, spolu s předáním nového typu kolem odkazem. Toto je vzor, který následuje knihovna [Microsoft.Extensions.DependencyModel:](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter ve srovnání s JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>je vysoce výkonný způsob zápisu textu JSON kódovaného UTF-8 `String` `Int32`z `DateTime`běžných typů .NET, jako je , a . Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastní serializers.

V následujících částech jsou vysvětleny doporučené programovací vzory pro použití `Utf8JsonWriter`.

### <a name="write-with-utf-8-text"></a>Psaní s textem UTF-8

Chcete-li dosáhnout nejlepšího `Utf8JsonWriter`možného výkonu při použití , napište datové části JSON již zakódované jako utf-8 text spíše než jako řetězce UTF-16. Slouží <xref:System.Text.Json.JsonEncodedText> k ukládání do mezipaměti a pre-kódovat známé názvy vlastností řetězce a hodnoty jako statika a předat je zapisovateli, spíše než pomocí literály řetězce UTF-16. To je rychlejší než ukládání do mezipaměti a použití utf-8 bajtových polí.

Tento přístup funguje také, pokud potřebujete provést vlastní escaping. `System.Text.Json`neumožňuje zakázat únik při psaní řetězce. Můžete však předat vlastní <xref:System.Text.Encodings.Web.JavaScriptEncoder> vlastní jako možnost pro zapisovače nebo vytvořit vlastní, `JsonEncodedText` který používá vaše `JavascriptEncoder` provést úniku a pak napište `JsonEncodedText` místo řetězce. Další informace naleznete v [tématu Customize character encoding](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Zapsat nezpracované hodnoty

Metoda `Newtonsoft.Json` `WriteRawValue` zapíše nezpracovaná JSON, kde se očekává hodnota. <xref:System.Text.Json>nemá žádný přímý ekvivalent, ale tady je řešení, které zajišťuje pouze platný JSON je zapsán:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Přizpůsobení úniku znaků

[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) nastavení `JsonTextWriter` nabízí možnosti uniknout všechny znaky než ASCII **nebo** HTML znaky. Ve výchozím `Utf8JsonWriter` nastavení unikne všechny znaky mimo ASCII **a** HTML. Toto úniku se provádí z důvodů zabezpečení hloubkové zabezpečení. Chcete-li zadat jinou zásadu úniku, vytvořte <xref:System.Text.Encodings.Web.JavaScriptEncoder> a set <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>. Další informace naleznete v [tématu Customize character encoding](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Přizpůsobení formátu JSON

`JsonTextWriter`obsahuje následující nastavení, `Utf8JsonWriter` pro která nemá ekvivalent:

* [Odsazení](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) - Určuje, kolik znaků se má odsadit. `Utf8JsonWriter`vždy provádí dvoumístné odsazení.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) - Určuje znak, který má být používán pro odsazení.  `Utf8JsonWriter`vždy používá prázdné znaky.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Určuje znak, který má být používán k obsazování hodnot řetězců.  `Utf8JsonWriter`vždy používá dvojité uvozovky.
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Určuje, zda mají být názvy vlastností obklopeny uvozovkami.  `Utf8JsonWriter`vždy je obklopuje uvozovkami.

Neexistují žádná řešení, která by vám umožní přizpůsobit `Utf8JsonWriter` JSON vyrobené těmito způsoby.

### <a name="write-null-values"></a>Zápis nulových hodnot

Chcete-li zapsat `Utf8JsonWriter`hodnoty null pomocí , volejte:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>pro zápis dvojice klíč-hodnota s hodnotou null jako hodnota.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>chcete-li napsat null jako prvek pole JSON.

Pro vlastnost string, pokud je <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> řetězec <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> null `WriteNull` a `WriteNullValue`jsou ekvivalentní a .

### <a name="write-timespan-uri-or-char-values"></a>Zapsat hodnoty Timespan, Uri nebo char

`JsonTextWriter`poskytuje `WriteValue` metody pro [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)a [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) hodnoty. `Utf8JsonWriter`nemá ekvivalentní metody. Místo toho naformátujte tyto hodnoty `ToString()`jako řetězce (například voláním , a voláním <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.

### <a name="multi-targeting"></a>Vícenásobné cílení

Pokud potřebujete pokračovat v `Newtonsoft.Json` používání pro určité cílové architektury, můžete více cílají a mají dvě implementace. To však není triviální a `#ifdefs` bude vyžadovat některé a zdroj duplikace. Jedním ze způsobů, jak sdílet co nejvíce kódu, `Newtonsoft` `JsonTextWriter`je vytvořit obálku kolem `Utf8JsonWriter` a . Tento obal by sjednotit veřejné plochy při izolaci behaviorální rozdíly. To vám umožní izolovat změny především na konstrukci typu. [Knihovna Microsoft.Extensions.DependencyModel:](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Další zdroje

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.JsonPřehled](system-text-json-overview.md)
* [Jak používatSystem.Text.Json](system-text-json-how-to.md)
* [Postup zápisu vlastních převaděčů](system-text-json-converters-how-to.md)
* [Podpora DateTime a DateTimeOffset vSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonOdkaz na rozhraní API](xref:System.Text.Json)
* [System.Text.Json. Odkaz na rozhraní API serializace](xref:System.Text.Json.Serialization)
