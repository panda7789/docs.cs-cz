---
title: Migrace z Newtonsoft.Json na System.Text.Json rozhraní – .NET
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
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Postup migrace z Newtonsoft. JSON na System. text. JSON

V tomto článku se dozvíte, jak migrovat z [Newtonsoft. JSON](https://www.newtonsoft.com/json) na <xref:System.Text.Json>.

`System.Text.Json` Obor názvů poskytuje funkce pro serializaci a deserializaci z JavaScript Object Notation (JSON). `System.Text.Json` Knihovna je obsažena v rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) Shared Framework. Pro jiná cílová rozhraní nainstalujte balíček NuGet [System. text. JSON](https://www.nuget.org/packages/System.Text.Json) . Balíček podporuje:

* .NET Standard 2,0 a novější verze
* .NET Framework 4.7.2 a novější verze
* .NET Core 2,0, 2,1 a 2,2

`System.Text.Json`zaměřuje se především na dodržování standardů pro výkon, zabezpečení a standardy. Má několik klíčových rozdílů ve výchozím chování a nezaměřuje se na to, aby `Newtonsoft.Json`byla funkce parita. V některých scénářích `System.Text.Json` nemá žádná integrovaná funkčnost, existují však doporučená řešení. Pro jiné scénáře jsou alternativní řešení nepraktická. Pokud vaše aplikace závisí na chybějící funkci, zvažte možnost nahlásit [problém](https://github.com/dotnet/runtime/issues/new) , abyste zjistili, jestli je možné přidat podporu pro váš scénář.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Většina tohoto článku je o tom, jak <xref:System.Text.Json.JsonSerializer> používat rozhraní API, ale obsahuje také pokyny k použití funkce <xref:System.Text.Json.JsonDocument> (která představuje model DOM (Document Object Model) nebo DOM), <xref:System.Text.Json.Utf8JsonReader>a <xref:System.Text.Json.Utf8JsonWriter> typů.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Tabulka rozdílů mezi Newtonsoft. JSON a System. text. JSON

V následující tabulce jsou `Newtonsoft.Json` uvedeny funkce `System.Text.Json` a jejich ekvivalenty. Ekvivalenty spadají do následujících kategorií:

* Podporováno integrovanou funkcí. Získání podobného chování `System.Text.Json` může vyžadovat použití atributu nebo globální možnosti.
* Nepodporováno, alternativní řešení je možné. Alternativní řešení jsou [vlastními převaděči](system-text-json-converters-how-to.md), které nemusí poskytnout kompletní paritu `Newtonsoft.Json` funkcí. Pro některé z nich vzorový kód je k dispozici jako příklad. Pokud spoléháte na tyto `Newtonsoft.Json` funkce, migrace bude vyžadovat úpravy pro vaše modely objektů .NET nebo jiné změny kódu.
* Nepodporováno, alternativní řešení není praktické nebo možné. Pokud spoléháte na tyto `Newtonsoft.Json` funkce, migrace nebude možná bez významných změn.

| Newtonsoft. JSON – funkce                               | Ekvivalent System. text. JSON |
|-------------------------------------------------------|-----------------------------|
| Deserializace bez rozlišování velkých a malých písmen ve výchozím nastavení           | [globální nastavení ✔️ PropertyNameCaseInsensitive](#case-insensitive-deserialization) |
| Ve stylu CamelCase – názvy vlastností případu                             | [globální nastavení ✔️ PropertyNamingPolicy](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Minimální znaková řídicí znaky                            | ✔️ [striktní znakové uvozovací znaky, konfigurovatelné](#minimal-character-escaping) |
| `NullValueHandling.Ignore`globální nastavení             | ✔️ – [globální možnost IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Povoluje komentáře                                        | [globální nastavení ✔️ ReadCommentHandling](#comments) |
| Povolená koncová čárka                                 | [globální nastavení ✔️ AllowTrailingCommas](#trailing-commas) |
| Registrace vlastního převaděče                         | ✔️ [pořadí priorit se liší](#converter-registration-precedence) . |
| Žádná maximální hloubka ve výchozím nastavení                           | ✔️ [výchozí maximální hloubka 64, konfigurovatelný](#maximum-depth) |
| Podpora pro širokou škálu typů                    | ⚠️[Některé typy vyžadují vlastní převaděče](#types-without-built-in-support) . |
| Deserializovat řetězce jako čísla                        | ⚠️[Nepodporováno, alternativní řešení, ukázka](#quoted-numbers) |
| Deserializovat `Dictionary` pomocí klíče bez řetězce          | ⚠️[Nepodporováno, alternativní řešení, ukázka](#dictionary-with-non-string-key) |
| Polymorfní serializace                             | ⚠️[Nepodporováno, alternativní řešení, ukázka](#polymorphic-serialization) |
| Polymorfní deserializace                           | ⚠️[Nepodporováno, alternativní řešení, ukázka](#polymorphic-deserialization) |
| Deserializovat odvozený typ k `object` vlastnostem      | ⚠️[Nepodporováno, alternativní řešení, ukázka](#deserialization-of-object-properties) |
| Deserializovat literál `null` JSON na typy hodnot, které nejsou null | ⚠️[Nepodporováno, alternativní řešení, ukázka](#deserialize-null-to-non-nullable-type) |
| Deserializace pro neměnné třídy a struktury          | ⚠️[Nepodporováno, alternativní řešení, ukázka](#deserialize-to-immutable-classes-and-structs) |
| Atribut `[JsonConstructor]`                         | ⚠️[Nepodporováno, alternativní řešení, ukázka](#specify-constructor-to-use) |
| `Required`nastavení `[JsonProperty]` atributu        | ⚠️[Nepodporováno, alternativní řešení, ukázka](#required-properties) |
| `NullValueHandling`nastavení `[JsonProperty]` atributu | ⚠️[Nepodporováno, alternativní řešení, ukázka](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`nastavení `[JsonProperty]` atributu | ⚠️[Nepodporováno, alternativní řešení, ukázka](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`globální nastavení                 | ⚠️[Nepodporováno, alternativní řešení, ukázka](#conditionally-ignore-a-property) |
| `DefaultContractResolver`vyloučení vlastností       | ⚠️[Nepodporováno, alternativní řešení, ukázka](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` nastavení   | ⚠️[Nepodporováno, alternativní řešení, ukázka](#specify-date-format) |
| Zpětná volání                                             | ⚠️[Nepodporováno, alternativní řešení, ukázka](#callbacks) |
| Podpora veřejných a neveřejných polí              | ⚠️[Nepodporováno, alternativní řešení](#public-and-non-public-fields) |
| Podpora pro vlastnosti a metody nastavení vnitřních a privátních vlastností | ⚠️[Nepodporováno, alternativní řešení](#internal-and-private-property-setters-and-getters) |
| Metoda `JsonConvert.PopulateObject`                   | ⚠️[Nepodporováno, alternativní řešení](#populate-existing-objects) |
| `ObjectCreationHandling`globální nastavení               | ⚠️[Nepodporováno, alternativní řešení](#reuse-rather-than-replace-properties) |
| Přidat do kolekcí bez setter                    | ⚠️[Nepodporováno, alternativní řešení](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`globální nastavení           | ❌[Nepodporováno](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`globální nastavení                | ❌[Nepodporováno](#preserve-object-references-and-handle-loops) |
| Podpora `System.Runtime.Serialization` atributů | ❌[Nepodporováno](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`globální nastavení                | ❌[Nepodporováno](#missingmemberhandling) |
| Povolení názvů vlastností bez uvozovek                   | ❌[Nepodporováno](#json-strings-property-names-and-string-values) |
| Povolení jednoduchých uvozovek kolem řetězcových hodnot              | ❌[Nepodporováno](#json-strings-property-names-and-string-values) |
| Povoluje neřetězcové hodnoty JSON pro vlastnosti řetězce.    | ❌[Nepodporováno](#non-string-values-for-string-properties) |

Nejedná se o vyčerpávající seznam `Newtonsoft.Json` funkcí. Seznam obsahuje mnoho scénářů, které byly vyžádány v rámci [problémů GitHubu](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) nebo [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) příspěvky. Pokud implementujete alternativní řešení pro jeden z uvedených scénářů, který aktuálně neobsahuje vzorový kód, a pokud chcete své řešení sdílet, vyberte **tuto stránku** v části **Zpětná vazba** v dolní části této stránky. Tím se vytvoří problém v úložišti GitHub v této dokumentaci a seznam je uvedený v části **názory** na této stránce.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Rozdíly ve výchozím chování JsonSerializer ve srovnání s Newtonsoft. JSON

<xref:System.Text.Json>ve výchozím nastavení je striktní a zabrání jakémukoli odhadu nebo výkladu jménem volajícího a zdůraznění deterministické chování. Knihovna je záměrně navržena tak, aby způsobila výkon a zabezpečení. `Newtonsoft.Json`je flexibilní ve výchozím nastavení. Tento základní rozdíl v návrhu je za mnoho z následujících specifických rozdílů ve výchozím chování.

### <a name="case-insensitive-deserialization"></a>Deserializace bez rozlišování velkých a malých písmen

Během deserializace se `Newtonsoft.Json` ve výchozím nastavení nerozlišuje velká a malá písmena. Ve <xref:System.Text.Json> výchozím nastavení se rozlišují velká a malá písmena, což dává lepší výkon, protože se jedná o přesnou shodu. Informace o tom, jak rozlišovat velká a malá písmena, naleznete v tématu [porovnávání vlastností](system-text-json-how-to.md#case-insensitive-property-matching)bez rozlišování velkých a malých písmen.

Pokud nepoužíváte `System.Text.Json` nepřímo pomocí ASP.NET Core, nemusíte nic dělat, abyste získali chování jako `Newtonsoft.Json`. ASP.NET Core určuje nastavení pro [názvy vlastností ve stylu CamelCase-střev](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) a porovnávání bez rozlišení velkých a malých písmen při použití `System.Text.Json`.

### <a name="minimal-character-escaping"></a>Minimální znaková řídicí znaky

Během serializace `Newtonsoft.Json` je poměrně umožněno zadávat znaky bez uvozovacích znaků. To znamená, že je nenahrazuje, `\uxxxx` kde `xxxx` je bod kódu znaku. Tam, kde je řídí, je to tak, že vygenerují `\` znak před znakem (například `"` se stalo `\"`). <xref:System.Text.Json>ve výchozím nastavení zařídí více znaků, aby poskytovala důkladné ochrany proti skriptování mezi weby (XSS) nebo útokům prostřednictvím odhalení informací a pomocí sekvence šesti znaků. `System.Text.Json`ve výchozím nastavení zařídí všechny znaky jiné než ASCII, takže pokud používáte v `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json`nástroji, nemusíte dělat nic. `System.Text.Json`ve výchozím nastavení také řídí znaky citlivé na kód HTML. Informace o tom, jak přepsat výchozí `System.Text.Json` chování, najdete v tématu [přizpůsobení kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Komentáře

Během deserializace `Newtonsoft.Json` ignoruje ve výchozím nastavení komentáře ve formátu JSON. Ve <xref:System.Text.Json> výchozím nastavení je pro komentáře vyvolána výjimka, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je neobsahuje. Informace o povolení komentářů najdete v tématu [Povolení komentářů a koncových čárek](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Čárky na konci

Během deserializace `Newtonsoft.Json` ignoruje koncové čárky ve výchozím nastavení. Ignoruje také více koncových čárek (například `[{"Color":"Red"},{"Color":"Green"},,]`). Ve <xref:System.Text.Json> výchozím nastavení je vyvolána výjimka pro koncové čárky, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je nepovoluje. Informace o tom, jak je `System.Text.Json` přijmout, najdete v tématu [Povolení komentářů a koncových čárek](system-text-json-how-to.md#allow-comments-and-trailing-commas). Neexistuje žádný způsob, jak povoluje více koncových čárek.

### <a name="converter-registration-precedence"></a>Priorita registrace převaděče

Priorita `Newtonsoft.Json` registrace pro vlastní převaděče je následující:

* Atribut u vlastnosti
* Atribut u typu
* Kolekce [převaděčů](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Toto pořadí znamená, že vlastní převaděč v `Converters` kolekci je přepsán převaděčem, který je zaregistrován použitím atributu na úrovni typu. Oba tyto registrace jsou přepsány atributem na úrovni vlastnosti.

Priorita <xref:System.Text.Json> registrace pro vlastní převaděče se liší:

* Atribut u vlastnosti
* <xref:System.Text.Json.JsonSerializerOptions.Converters>kolekce
* Atribut u typu

Rozdíl je v tom, že vlastní převaděč v `Converters` kolekci Přepisuje atribut na úrovni typu. Záměrem na základě tohoto pořadí priorit je provést změny v době návrhu v době běhu. Neexistuje žádný způsob, jak změnit prioritu.

Další informace o registraci vlastního převaděče najdete v tématu [registrace vlastního převaděče](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>Maximální hloubka

`Newtonsoft.Json`ve výchozím nastavení nemá maximální limit hloubky. Pro <xref:System.Text.Json> výchozí omezení 64 a je možné ho nakonfigurovat nastavením <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>.

### <a name="json-strings-property-names-and-string-values"></a>Řetězce JSON (názvy vlastností a řetězcové hodnoty)

Během deserializace `Newtonsoft.Json` akceptuje názvy vlastností, které jsou obklopeny dvojitými uvozovkami, jednoduchými uvozovkami nebo bez uvozovek. Přijímá řetězcové hodnoty obklopené dvojitými uvozovkami nebo jednoduchými uvozovkami. Například `Newtonsoft.Json` akceptuje následující kód JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`v dvojitých uvozovkách akceptuje pouze názvy vlastností a řetězcové hodnoty, protože tento formát je vyžadován specifikací [RFC 8259](https://tools.ietf.org/html/rfc8259) a je jediným formátem, který se považuje za platný kód JSON.

Hodnota uzavřená v jednoduchých uvozovkách má za následek [JsonException](xref:System.Text.Json.JsonException) s následující zprávou:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Hodnoty nepatřící do řetězce pro vlastnosti řetězce

`Newtonsoft.Json`přijímá hodnoty nesouvisející s řetězcem, jako je číslo nebo literály `true` a `false`, pro deserializaci vlastností typu String. Tady je příklad JSON, který `Newtonsoft.Json` úspěšně deserializace do následující třídy:

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

`System.Text.Json`neprovádí deserializaci hodnot neřetězcových hodnot do vlastností řetězce. Neřetězcová hodnota přijatá pro pole typu String má za následek [JsonException](xref:System.Text.Json.JsonException) s následující zprávou:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scénáře využívající JsonSerializer, které vyžadují alternativní řešení

V těchto scénářích nejsou integrované funkce podporované, ale alternativní řešení jsou možná. Alternativní řešení jsou [vlastními převaděči](system-text-json-converters-how-to.md), které nemusí poskytnout kompletní paritu `Newtonsoft.Json` funkcí. Pro některé z nich vzorový kód je k dispozici jako příklad. Pokud spoléháte na tyto `Newtonsoft.Json` funkce, migrace bude vyžadovat úpravy pro vaše modely objektů .NET nebo jiné změny kódu.

### <a name="types-without-built-in-support"></a>Typy bez integrované podpory

<xref:System.Text.Json>neposkytuje integrovanou podporu pro následující typy:

* <xref:System.Data.DataTable>a související typy
* Typy F #, například [rozlišené sjednocení](../../fsharp/language-reference/discriminated-unions.md), [typy záznamů](../../fsharp/language-reference/records.md)a [anonymní typy záznamů](../../fsharp/language-reference/anonymous-records.md).
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>a přidružené obecné typy

Vlastní převaděče lze implementovat pro typy, které nemají vestavěnou podporu.

### <a name="quoted-numbers"></a>Čísla v uvozovkách

`Newtonsoft.Json`může serializovat nebo deserializovat čísla reprezentovaná řetězci JSON (obklopenými uvozovkami). Může například přijmout: `{"DegreesCelsius":"23"}` namísto. `{"DegreesCelsius":23}` Chcete-li toto chování <xref:System.Text.Json>povolit v, implementujte vlastní převaděč podobný následujícímu příkladu. Převaděč zpracovává vlastnosti definované jako `long`:

* Jejich serializace jako řetězce JSON.
* Při deserializaci přijímá čísla a čísla JSON v rámci uvozovek.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) u jednotlivých `long` vlastností nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

### <a name="dictionary-with-non-string-key"></a>Slovník s jiným než řetězcovým klíčem

`Newtonsoft.Json`podporuje kolekce typu `Dictionary<TKey, TValue>`. Integrovaná podpora kolekcí slovníků v <xref:System.Text.Json> nástroji je omezená na. `Dictionary<string, TValue>` To znamená, že klíč musí být řetězec.

Pro podporu slovníku s celým číslem nebo jiným typem jako klíč vytvořte konvertor jako příklad v tématu [jak psát vlastní převaděče](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Polymorfní serializace

`Newtonsoft.Json`automaticky provede polymorfní serializaci. Informace o možnostech <xref:System.Text.Json>omezené polymorfní serializace pro naleznete v tématu [serializovat vlastnosti odvozených tříd](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Alternativní řešení je popsáno pro definování vlastností, které mohou obsahovat odvozené třídy jako typ `object`. Pokud to není možné, je další možností vytvoření převaděče s `Write` metodou pro celou hierarchii typu dědičnosti, jako je například příklad [psaní vlastních převaděčů](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Polymorfní deserializace

`Newtonsoft.Json`má `TypeNameHandling` nastavení, které při serializaci přidá do formátu JSON metadata typu. Používá metadata při deserializaci k provedení polymorfního deserializace. <xref:System.Text.Json>může provádět omezený rozsah [polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale ne polymorfní deserializace.

Pro podporu polymorfního deserializace vytvořte jako příklad v [postupu psaní vlastních převaděčů](system-text-json-converters-how-to.md#support-polymorphic-deserialization)převaděč.

### <a name="deserialization-of-object-properties"></a>Deserializace vlastností objektu

Při `Newtonsoft.Json` deserializaci na <xref:System.Object>:

* Odvodí typ primitivních hodnot v datové části JSON (jiné `null`než) a vrátí uložené `string`, `long`, `double` `boolean`, nebo `DateTime` jako zabalený objekt. *Primitivní hodnoty* jsou jednoduché hodnoty JSON, jako je číslo JSON, řetězec, `true` `false`, nebo `null`.
* Vrátí `JObject` nebo `JArray` pro komplexní hodnoty v datové části JSON. *Komplexní hodnoty* jsou kolekce párů klíč-hodnota JSON do složených závorek (`{}`) nebo seznamů hodnot v závorkách (`[]`). Vlastnosti a hodnoty v závorkách nebo závorkách mohou mít další vlastnosti nebo hodnoty.
* Vrátí odkaz s hodnotou null, pokud má datová `null` část literál JSON.

<xref:System.Text.Json>ukládá zabalené `JsonElement` pro primitivní i komplexní hodnoty při každém deserializaci do <xref:System.Object>, například:

* `object` Vlastnost.
* Hodnota `object` slovníku.
* Hodnota `object` pole
* Kořenová `object`složka.

Nicméně `System.Text.Json` zpracovává `null` stejnou hodnotu jako `Newtonsoft.Json` a vrátí odkaz s hodnotou null v případě, že datová část `null` obsahuje literál JSON.

Chcete-li implementovat odvození `object` typu pro vlastnosti, vytvořte převaděč jako příklad v tématu [jak psát vlastní převaděče](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="deserialize-null-to-non-nullable-type"></a>Deserializovat hodnotu null na typ, který není možnou hodnotou null

`Newtonsoft.Json`nevyvolá výjimku v následujícím scénáři:

* `NullValueHandling`je nastaven na `Ignore`, a
* Při deserializaci obsahuje JSON hodnotu null pro typ hodnoty, která není null.

Ve stejném scénáři <xref:System.Text.Json> vyvolá výjimku. (Odpovídající nastavení zpracování hodnoty null je <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)

Pokud vlastníte cílový typ, nejlepším řešením je učinit vlastnost dotazovat se na hodnotu null (například změnit `int` na `int?`).

Dalším řešením je vytvořit převaděč pro typ, například následující příklad, který zpracovává hodnoty null pro `DateTimeOffset` typy:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu vlastnosti](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

**Poznámka:** Předchozí převaděč **zpracovává hodnoty null jinak** než `Newtonsoft.Json` u POCOs, které určují výchozí hodnoty. Předpokládejme například, že následující kód představuje cílový objekt:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

A Předpokládejme, že následující JSON je deserializovat pomocí předchozího převaděče:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializaci má `Date` vlastnost hodnotu 1/1/0001 (`default(DateTimeOffset)`), to znamená, že hodnota nastavená v konstruktoru je přepsána. Vzhledem ke stejným POCO a JSON `Newtonsoft.Json` by deserializace ponechala 1/1/2001 ve `Date` vlastnosti.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Deserializace pro neměnné třídy a struktury

`Newtonsoft.Json`může deserializovat na neměnné třídy a struktury, protože může používat konstruktory s parametry. <xref:System.Text.Json>podporuje pouze veřejné konstruktory bez parametrů. Jako alternativní řešení můžete volat konstruktor s parametry ve vlastním převaděči.

Tady je neproměnlivá struktura s více parametry konstruktoru:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

A zde je převaděč, který serializace a deserializace této struktury:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Zaregistrujte tento vlastní převaděč [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Příklad podobného převaděče, který zpracovává otevřené generické vlastnosti, naleznete v [integrovaném převaděči pro páry klíč-hodnota](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Zadejte konstruktor, který se má použít.

`Newtonsoft.Json` Atribut umožňuje určit, který konstruktor má být volán při deserializaci do `[JsonConstructor]` POCO. <xref:System.Text.Json>podporuje pouze konstruktory bez parametrů. Jako alternativní řešení můžete zavolat libovolný konstruktor, který potřebujete, ve vlastním převaděči. Podívejte se na příklad pro [deserializaci pro neměnné třídy a struktury](#deserialize-to-immutable-classes-and-structs).

### <a name="required-properties"></a>Požadované vlastnosti

V `Newtonsoft.Json`nástroji můžete určit, že vlastnost je vyžadována nastavením `Required` `[JsonProperty]` atributu. `Newtonsoft.Json`vyvolá výjimku, pokud není ve formátu JSON přijata žádná hodnota pro vlastnost označenou jako Required.

<xref:System.Text.Json>nevyvolá výjimku, pokud není přijata žádná hodnota pro jednu z vlastností cílového typu. Například pokud máte `WeatherForecast` třídu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Následující kód JSON je deserializovaný bez chyby:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Aby deserializace selhala, pokud `Date` ve formátu JSON není žádná vlastnost, implementujte vlastní převaděč. Následující ukázkový kód převaděče vyvolá výjimku, `Date` Pokud vlastnost není nastavena po dokončení deserializace:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu ve třídě POCO](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Pokud budete postupovat podle tohoto vzoru, při rekurzivním volání <xref:System.Text.Json.JsonSerializer.Serialize%2A> nebo <xref:System.Text.Json.JsonSerializer.Deserialize%2A>zadávejte do objektu Options. Objekt Options obsahuje <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> kolekci. Pokud ho předáte do `Serialize` nebo `Deserialize`, vlastní převaděč zavolá sám sebe a vytvoří nekonečnou smyčku, která způsobí výjimku přetečení zásobníku. Pokud výchozí možnosti nejsou proveditelné, vytvořte novou instanci možností s nastavením, které potřebujete. Tento přístup bude pomalý, protože každá nová instance mezipamětí nezávisle.

Předchozí kód převaděče je zjednodušený příklad. Pokud potřebujete zpracovat atributy (například [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) nebo jiné možnosti (například vlastní kodéry), bude nutné další logiku. Kromě toho ukázkový kód nezpracovává vlastnosti, pro které je v konstruktoru nastavena výchozí hodnota. A tento přístup nerozlišuje mezi následujícími scénáři:

* Ve formátu JSON chybí vlastnost.
* Vlastnost pro typ, který nepovoluje hodnotu null, je přítomna ve formátu JSON, ale hodnota je výchozím typem pro typ, například nula pro `int`.
* Vlastnost pro typ hodnoty s možnou hodnotou null je k dispozici ve formátu JSON, ale hodnota je null.

### <a name="conditionally-ignore-a-property"></a>Podmíněně ignorovat vlastnost

`Newtonsoft.Json`má několik způsobů, jak podmíněně ignorovat vlastnost při serializaci nebo deserializaci:

* `DefaultContractResolver`umožňuje vybrat vlastnosti, které se mají zahrnout nebo vyloučit, na základě libovolného kritéria.
* Nastavení `NullValueHandling` a `DefaultValueHandling` `JsonSerializerSettings` umožňují určit, že všechny vlastnosti null-Value nebo Default-value by měly být ignorovány.
* Nastavení `NullValueHandling` a `DefaultValueHandling` u `[JsonProperty]` atributu umožňují zadat jednotlivé vlastnosti, které by měly být ignorovány, pokud je nastavena hodnota null nebo výchozí hodnota.

<xref:System.Text.Json>poskytuje následující způsoby, jak vynechat vlastnosti při serializaci:

* Atribut [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) u vlastnosti způsobí, že vlastnost bude při serializaci vynechána ve formátu JSON.
* Globální možnost [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) umožňuje vyloučit všechny vlastnosti s hodnotou null.
* Globální možnost [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) umožňuje vyloučit všechny vlastnosti jen pro čtení.

Tyto možnosti **vám** neumožňují:

* Ignorovat všechny vlastnosti, které mají výchozí hodnotu pro typ.
* Ignoruje vybrané vlastnosti, které mají výchozí hodnotu pro daný typ.
* Ignoruje vybrané vlastnosti, pokud jejich hodnota je null.
* Ignorovat vybrané vlastnosti na základě libovolných kritérií vyhodnocených v době běhu.

Pro tuto funkci můžete napsat vlastní převaděč. Tady je ukázkový POCO a vlastní převaděč, který ilustruje tento přístup:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Převaděč způsobí, že `Summary` vlastnost bude vynechána z serializace, pokud má hodnotu null, prázdný řetězec nebo "N/a".

Zaregistrujte tento vlastní převaděč [pomocí atributu ve třídě](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Tento přístup vyžaduje další logiku v těchto případech:

* POCO obsahuje komplexní vlastnosti.
* Je potřeba zpracovat atributy `[JsonIgnore]` , jako jsou například vlastní kodéry.

### <a name="specify-date-format"></a>Zadat formát data

`Newtonsoft.Json`poskytuje několik způsobů, jak řídit, jak `DateTime` vlastnosti `DateTimeOffset` a typy jsou serializovány a deserializovány:

* `DateTimeZoneHandling` Nastavení lze použít k serializaci všech `DateTime` hodnot jako data UTC.
* `DateFormatString` Nastavení a `DateTime` převaděče lze použít k přizpůsobení formátu řetězce data.

V <xref:System.Text.Json>nástroji je jediným formátem, který má integrovanou podporu, ISO 8601-1:2019, protože je široce přijatý, jednoznačně nejednoznačný a způsobuje přesné odezvy. Pokud chcete použít jiný formát, vytvořte vlastní převaděč. Další informace najdete v tématu [Podpora DateTime a DateTimeOffset v System. text. JSON](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Zpětná volání

`Newtonsoft.Json`umožňuje spustit vlastní kód v několika bodech v procesu serializace nebo deserializace:

* OnDeserializing (při zahájení deserializace objektu)
* OnDeserialized (po dokončení deserializace objektu)
* Probíhá serializace (při zahájení serializace objektu)
* V-deserializovat (po dokončení serializace objektu)

V <xref:System.Text.Json>nástroji můžete simulovat zpětná volání vytvořením vlastního převaděče. Následující příklad ukazuje vlastní převaděč pro POCO. Převaděč obsahuje kód, který zobrazí zprávu v každém bodě, který odpovídá `Newtonsoft.Json` zpětnému volání.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu ve třídě](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do <xref:System.Text.Json.JsonSerializerOptions.Converters> kolekce.

Pokud používáte vlastní převaděč, který odpovídá předchozí ukázce:

* `OnDeserializing` Kód nemá přístup k nové instanci POCO. Chcete-li pracovat s novou instancí POCO na začátku deserializace, vložte tento kód do konstruktoru POCO.
* Při rekurzivním volání `Serialize` nebo `Deserialize`není předávat do objektu Options. Objekt Options obsahuje `Converters` kolekci. Pokud jej předáte do `Serialize` nebo `Deserialize`, bude použit převaděč, což vede k nekonečnou smyčku, která způsobí výjimku přetečení zásobníku.

### <a name="public-and-non-public-fields"></a>Veřejná a neveřejná pole

`Newtonsoft.Json`může serializovat a deserializovat pole a také vlastnosti. <xref:System.Text.Json>funguje pouze s veřejnými vlastnostmi. Tato funkce může poskytnout vlastní převaděče.

### <a name="internal-and-private-property-setters-and-getters"></a>Interní a privátní vlastnosti setter a getter

`Newtonsoft.Json`může použít nastavení privátních a vnitřních vlastností a metody getter prostřednictvím `JsonProperty` atributu. <xref:System.Text.Json>podporuje pouze veřejné metody setter. Tato funkce může poskytnout vlastní převaděče.

### <a name="populate-existing-objects"></a>Naplnit existující objekty

`JsonConvert.PopulateObject` Metoda v `Newtonsoft.Json` deserializaci dokumentu JSON na existující instanci třídy místo vytvoření nové instance. <xref:System.Text.Json>vždy vytvoří novou instanci cílového typu pomocí výchozího veřejného konstruktoru bez parametrů. Vlastní převaděče mohou být deserializovány na existující instanci.

### <a name="reuse-rather-than-replace-properties"></a>Znovu použít místo nahrazení vlastností

Toto `Newtonsoft.Json` `ObjectCreationHandling` nastavení umožňuje určit, že objekty ve vlastnostech by měly být znovu použity místo nahrazení během deserializace. <xref:System.Text.Json>vždy nahrazuje objekty ve vlastnostech.  Tato funkce může poskytnout vlastní převaděče.

### <a name="add-to-collections-without-setters"></a>Přidat do kolekcí bez setter

Během deserializace přidává `Newtonsoft.Json` objekty do kolekce i v případě, že vlastnost nemá metodu setter. <xref:System.Text.Json>ignoruje vlastnosti, které nemají setter. Tato funkce může poskytnout vlastní převaděče.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Scénáře, které JsonSerializer aktuálně nepodporuje

V následujících případech nejsou alternativní řešení praktická nebo možná. Pokud spoléháte na tyto `Newtonsoft.Json` funkce, migrace nebude možná bez významných změn.

### <a name="preserve-object-references-and-handle-loops"></a>Zachovat odkazy na objekty a zpracovávat smyčky

Ve výchozím nastavení `Newtonsoft.Json` serializace podle hodnoty. Například pokud objekt obsahuje dvě vlastnosti, které obsahují odkaz na stejný `Person` objekt, hodnoty vlastností tohoto `Person` objektu jsou duplikovány ve formátu JSON.

`Newtonsoft.Json`má `PreserveReferencesHandling` nastavení `JsonSerializerSettings` , které umožňuje serializaci odkazem:

* Metadata identifikátoru jsou přidána do formátu JSON vytvořeného pro první `Person` objekt.
* KÓD JSON, který je vytvořen pro druhý `Person` objekt, obsahuje odkaz na tento identifikátor namísto hodnot vlastností.

`Newtonsoft.Json`má také `ReferenceLoopHandling` nastavení, které umožňuje ignorovat cyklické odkazy namísto vyvolání výjimky.

<xref:System.Text.Json>podporuje pouze serializaci podle hodnoty a vyvolá výjimku pro cyklické odkazy.

### <a name="systemruntimeserialization-attributes"></a>Atributy System. Runtime. Serialization

<xref:System.Text.Json>nepodporuje atributy z `System.Runtime.Serialization` oboru názvů, jako jsou `DataMemberAttribute` a. `IgnoreDataMemberAttribute`

### <a name="octal-numbers"></a>Osmičková čísla

`Newtonsoft.Json`zpracovává čísla s úvodní nulou jako osmičková čísla. <xref:System.Text.Json>nepovoluje počáteční nuly, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je nepovoluje.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json`dá se nakonfigurovat tak, aby vyvolal výjimky během deserializace, pokud JSON obsahuje vlastnosti, které chybí v cílovém typu. <xref:System.Text.Json>ignoruje další vlastnosti ve formátu JSON, s výjimkou použití [atributu [JsonExtensionData]](system-text-json-how-to.md#handle-overflow-json). Pro chybějící funkci člena není k dispozici žádné alternativní řešení.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`umožňuje ladění pomocí a `TraceWriter` k zobrazení protokolů, které jsou generovány pomocí serializace nebo deserializace. <xref:System.Text.Json>neprovádí protokolování.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument a JsonElement v porovnání s JToken (jako JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>poskytuje možnost analyzovat a sestavit model DOM (Document Object Model) (DOM) **jen pro čtení** z existujících datových částí JSON. Model DOM poskytuje náhodný přístup k datům v datové části JSON. K prvkům JSON, které tvoří datovou část, lze <xref:System.Text.Json.JsonElement> přistupovat prostřednictvím typu. `JsonElement` Typ poskytuje rozhraní API pro převod textu JSON na běžné typy .NET. `JsonDocument`zpřístupňuje <xref:System.Text.Json.JsonDocument.RootElement> vlastnost.

### <a name="jsondocument-is-idisposable"></a>JsonDocument je IDisposable

`JsonDocument`Vytvoří zobrazení dat v paměti do fondu vyrovnávací paměti. Proto `JObject` , na `JArray` `Newtonsoft.Json` `JsonDocument` rozdíl od nebo z, typ implementuje `IDisposable` a musí být použit uvnitř bloku using.

Jenom `JsonDocument` z rozhraní API vraťte, pokud chcete přenést vlastnictví životnosti a zařadit odpovědnost volajícímu. Ve většině scénářů to není nutné. Pokud volající potřebuje pracovat s celý dokument JSON, vraťte <xref:System.Text.Json.JsonElement.Clone%2A> z <xref:System.Text.Json.JsonDocument.RootElement%2A>, což je. <xref:System.Text.Json.JsonElement> Pokud volající potřebuje pracovat s konkrétním prvkem v dokumentu JSON, vraťte <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonElement>. Pokud vrátíte `RootElement` dílčí prvek přímo bez provedení `Clone`, volající nebude moci získat přístup k vráceným `JsonElement` poté, co `JsonDocument` jeho vlastníkem je zrušeno.

Tady je příklad, který vyžaduje, abyste provedli `Clone`:

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

Předchozí kód očekává `JsonElement` , že obsahuje `fileName` vlastnost. Otevře soubor JSON a vytvoří `JsonDocument`. Metoda předpokládá, že volající chce pracovat s celým dokumentem, takže vrátí `Clone` z. `RootElement`

Pokud obdržíte `JsonElement` a vrátíte dílčí prvek, není nutné vracet `Clone` dílčí element. Volající je zodpovědný za udržování Alive `JsonDocument` , ke kterému `JsonElement` patří předané. Příklad:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument je jen pro čtení.

<xref:System.Text.Json> Model DOM nemůže přidávat, odebírat ani upravovat elementy JSON. Je navržený tak, aby se snížil výkon a omezila se alokace při analýze běžných velikostí datových částí JSON (tj. < 1 MB). Pokud váš scénář aktuálně používá upravitelný model DOM, může být možné provést jedno z následujících řešení:

* Chcete-li `JsonDocument` vytvořit úplně od začátku (to znamená bez předání existující datové části JSON do `Parse` metody), zapište text JSON pomocí `Utf8JsonWriter` a analyzujte výstup z tohoto a proveďte nový. `JsonDocument`
* Pokud chcete upravit existující `JsonDocument`, použijte ho k zápisu textu JSON, provádění změn při psaní a analýzou výstupu z něj vytvořte nový `JsonDocument`.
* K sloučení `JObject.Merge` existujících dokumentů JSON, které odpovídají rozhraním `JContainer.Merge` API nebo `Newtonsoft.Json`, se podívejte na [Tento problém GitHubu](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement je struktura sjednocení.

`JsonDocument`zpřístupňuje `RootElement` jako vlastnost typu <xref:System.Text.Json.JsonElement>, což je sjednocení typu struktury, které zahrnuje jakýkoli element JSON. `Newtonsoft.Json`používá vyhrazené hierarchické typy jako `JObject`,`JArray`, `JToken`a tak dále. `JsonElement`je to, co můžete hledat a vyčíslit, a můžete použít `JsonElement` k VYHODNOTIT prvků JSON do typů .NET.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Jak vyhledávat JsonDocument a JsonElement pro dílčí prvky

Vyhledává tokeny JSON `JObject` pomocí `JArray` nebo `Newtonsoft.Json` z tohoto důvodu relativně rychlé vzhledem k tomu, že jsou vyhledávání v některém slovníku. Porovnáním, hledání `JsonElement` vyžaduje sekvenční hledání vlastností, a proto je poměrně pomalé (například při použití `TryGetProperty`). <xref:System.Text.Json>je navržena tak, aby minimalizovala čas počáteční analýzy, nikoli čas vyhledávání. Proto pomocí následujících přístupů Optimalizujte výkon při hledání `JsonDocument` objektu:

* Místo vlastního indexování nebo smyček použijte předdefinované<xref:System.Text.Json.JsonElement.EnumerateArray%2A> enumerátory <xref:System.Text.Json.JsonElement.EnumerateObject%2A>(a).
* Neprovádějte sekvenční hledání celého `JsonDocument` přes každou vlastnost pomocí. `RootElement` Místo toho hledejte ve vnořených objektech JSON na základě známé struktury dat JSON. Například `Grade` Pokud hledáte vlastnost v `Student` objektu Objects, procházejte `Student` objekty a získejte hodnotu pro každou místo hledání ve všech `Grade` `JsonElement` objektech, které hledají `Grade` vlastnosti. V takovém případě by to vedlo k zbytečnému průchodu se stejnými daty.

Příklad kódu naleznete v tématu [použití JsonDocument pro přístup k datům](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader ve srovnání s JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>je pro text JSON s kódováním UTF-8 s vysokým výkonem vysokého výkonu, který je určený jen pro čtení, načtený z [ReadOnlySpan\<bajtu>](xref:System.ReadOnlySpan%601) nebo [\<ReadOnlySequence Byte>](xref:System.Buffers.ReadOnlySequence%601). `Utf8JsonReader` Je typ nižší úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace.

Následující části vysvětlují Doporučené programovací vzory pro `Utf8JsonReader`použití.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader je struktura ref.

Vzhledem k `Utf8JsonReader` tomu, že typ je *Struktura ref*, má [určitá omezení](../../csharp/language-reference/builtin-types/struct.md#ref-struct). Například nemůže být uložen jako pole ve třídě nebo struktuře jiné než struktura ref. Aby se dosáhlo vysokého výkonu, musí být `ref struct` tento typ, protože potřebuje ukládat do mezipaměti vstupní [\<ReadOnlySpan bajt>](xref:System.ReadOnlySpan%601), který je sám strukturou ref. Tento typ je navíc proměnlivý, protože obsahuje stav. Proto **jej předejte pomocí ref** , nikoli podle hodnoty. Předání podle hodnoty by vedlo k kopírování struktury a změny stavu by pro volajícího neměly být viditelné. To se liší od `Newtonsoft.Json` , `Newtonsoft.Json` `JsonTextReader` protože je třídou. Další informace o použití struktur ref najdete v tématu [Zápis bezpečného a efektivního kódu v jazyce C#](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Číst text v kódování UTF-8

Abyste dosáhli nejlepšího možného výkonu při `Utf8JsonReader`používání rozhraní, číst datová část JSON, která jsou už kódovaná jako text UTF-8, a ne jako řetězce UTF-16. Příklad kódu naleznete v tématu [Filter data using Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Čtení s datovým proudem nebo PipeReader

Podporuje čtení z [ReadOnlySpan\<bajtů](xref:System.ReadOnlySpan%601) kódovaných v kódování UTF-8>[nebo\<ReadOnlySequence>bajtů](xref:System.Buffers.ReadOnlySequence%601) (což je výsledek čtení z <xref:System.IO.Pipelines.PipeReader>). `Utf8JsonReader`

Pro synchronní čtení můžete načíst datovou část JSON až do konce datového proudu do pole bajtů a předat je do čtecího zařízení. Pro čtení z řetězce (který je kódován jako UTF-16) volejte <xref:System.Text.Encoding.UTF8>.<xref:System.Text.Encoding.GetBytes%2A> pro první překódování řetězce do kódovaného bajtového pole UTF-8. Pak předejte do `Utf8JsonReader`.

Vzhledem k `Utf8JsonReader` tomu, že se považuje za vstup do formátu JSON, znamená to, že znak pořadí bajtů UTF-8 (BOM) se považuje za neplatný JSON. Volající musí tuto funkci před předáním dat do čtecího modulu filtrovat.

Příklady kódu naleznete v tématu [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Čtení s více segmenty ReadOnlySequence

Pokud je vaším vstupním kódem [json\<>ReadOnlySpan bajt ](xref:System.ReadOnlySpan%601), ke každému prvku JSON se dá získat `ValueSpan` přístup z vlastnosti čtecího zařízení, když projdete smyčkou pro čtení. Pokud je však vstup [\<ReadOnlySequence bajt>](xref:System.Buffers.ReadOnlySequence%601) (což je výsledek čtení z <xref:System.IO.Pipelines.PipeReader>), některé elementy JSON mohou přetažný více segmentů `ReadOnlySequence<byte>` objektu. Tyto prvky nebudou přístupné z <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> v souvislém bloku paměti. Místo toho, když máte jako vstup více segmentů `ReadOnlySequence<byte>` , proveďte dotaz na <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> vlastnost čtecího zařízení a zjistěte, jak získat přístup k aktuálnímu elementu JSON. Tady je doporučený vzor:

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

### <a name="use-valuetextequals-for-property-name-lookups"></a>Pro vyhledávání názvů vlastností použijte ValueTextEquals

Nepoužívejte <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> k provádění porovnání po bajtech voláním <xref:System.MemoryExtensions.SequenceEqual%2A> pro vyhledávání názvů vlastností. Místo <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> toho zavolejte, protože tato metoda odvolá všechny znaky, které jsou ve formátu JSON uvozené řídicím znakem. Tady je příklad, který ukazuje, jak vyhledat vlastnost s názvem "Name":

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Čtení hodnot null na typy hodnot s možnou hodnotou null

`Newtonsoft.Json`poskytuje rozhraní API, <xref:System.Nullable%601>která vrací, `ReadAsBoolean`například, který zpracovává `Null` `TokenType` za vás vrácením `bool?`. Vestavěná `System.Text.Json` rozhraní API vracejí pouze typy hodnot, které neumožňují hodnotu null. Například <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> vrátí `bool`. Vyvolá výjimku, pokud nalezne `Null` ve formátu JSON. Následující příklady znázorňují dva způsoby, jak zpracovat hodnoty null, jednu vrácením typu hodnoty s možnou hodnotou null a jedním vrácením výchozí hodnoty:

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

### <a name="multi-targeting"></a>Cílení na více platforem

Pokud potřebujete i nadále používat `Newtonsoft.Json` pro určité cílové architektury, můžete mít více cílů a mít dvě implementace. Nejedná se ale o triviální příkaz a by vyžadovala nějaké `#ifdefs` duplicity a zdroje. Jedním ze `ref struct` způsobů, jak sdílet co nejvíc kódů, je vytvořit obálku kolem `Utf8JsonReader` a `Newtonsoft.Json` `JsonTextReader`. Tato obálka sjednotí oblast veřejného povrchu a současně izoluje rozdíly v chování. To vám umožní izolovat změny hlavně pro konstrukci typu, spolu s předáním nového typu kolem odkazu. Toto je vzor, který následuje knihovna [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) :

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter ve srovnání s JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET `String`, `Int32`jako jsou `DateTime`, a. Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů.

Následující části vysvětlují Doporučené programovací vzory pro `Utf8JsonWriter`použití.

### <a name="write-with-utf-8-text"></a>Zápis s textem v kódování UTF-8

Abyste dosáhli nejlepšího možného výkonu při `Utf8JsonWriter`používání rozhraní, zapisovat datové části JSON, které jsou už kódované jako text UTF-8, a ne jako řetězce UTF-16. Slouží <xref:System.Text.Json.JsonEncodedText> k ukládání názvů a hodnot a předkódování známých řetězcových vlastností a hodnot jako statických a jejich předání do zapisovače namísto použití řetězcových literálů ve formátu UTF-16. Je to rychlejší než ukládání do mezipaměti a používání bajtových polí UTF-8.

Tento přístup funguje také v případě, že potřebujete vlastní uvozovací znaky. `System.Text.Json`neumožňuje zakázat uvozovací znaky při zápisu řetězce. Můžete však předat vlastní možnost zapisovači, nebo <xref:System.Text.Encodings.Web.JavaScriptEncoder> vytvořit vlastní `JsonEncodedText` , který používá vaše `JavascriptEncoder` k označení řídicího panelu, a pak zapsat `JsonEncodedText` místo řetězce. Další informace najdete v tématu [přizpůsobení kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Zapsat nezpracované hodnoty

`Newtonsoft.Json` Metoda zapisuje nezpracovaný kód JSON, kde je očekávána `WriteRawValue` hodnota. <xref:System.Text.Json>nemá žádný přímý ekvivalent, ale tady je alternativní řešení, které zajišťuje, že se zapíše jenom platný kód JSON:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Přizpůsobení znakové uvozovací znaky

Nastavení [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) v `JsonTextWriter` nabídce nabízí možnosti pro únik všech znaků, které nejsou ASCII, **nebo** znaků HTML. Ve výchozím nastavení `Utf8JsonWriter` zařídí všechny znaky jiné než ASCII **a** HTML. Tyto uvozovací znaky se provádějí z důvodů zabezpečení s důkladnou ochranou. Chcete-li zadat jinou zásadu uvozovacích znaků, <xref:System.Text.Encodings.Web.JavaScriptEncoder> vytvořte a <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>nastavte. Další informace najdete v tématu [přizpůsobení kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Přizpůsobení formátu JSON

`JsonTextWriter`obsahuje následující nastavení, pro která `Utf8JsonWriter` nemá žádný ekvivalent:

* [Odsazení](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) – určuje, kolik znaků se má odsadit. `Utf8JsonWriter`vždy má 2 – odsazení znaku.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) – určuje znak, který se má použít pro odsazení.  `Utf8JsonWriter`vždy používá prázdné znaky.
* [QuoteChar současně](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) – určuje znak, který se má použít k obložení řetězcových hodnot.  `Utf8JsonWriter`Vždycky používá dvojité uvozovky.
* [Quote](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) – určuje, jestli se mají kolem názvů vlastností dokončit uvozovky.  `Utf8JsonWriter`vždy je ohraničuje pomocí uvozovek.

Neexistují žádná alternativní řešení, která by vám mohla umožnit přizpůsobení formátu JSON `Utf8JsonWriter` vytvořeného těmito způsoby.

### <a name="write-null-values"></a>Zapsat hodnoty null

Chcete-li zapsat hodnoty null `Utf8JsonWriter`pomocí, zavolejte:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>pro zápis páru klíč-hodnota s hodnotou null jako hodnoty.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>pro zápis null jako prvku pole JSON.

Pro řetězcovou vlastnost, pokud je řetězec <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> null a <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> je ekvivalentní `WriteNull` a. `WriteNullValue`

### <a name="write-timespan-uri-or-char-values"></a>Zápis hodnot TimeSpan, URI nebo char

`JsonTextWriter`poskytuje `WriteValue` metody pro hodnoty [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [URI](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)a [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) . `Utf8JsonWriter`nemá ekvivalentní metody. Místo toho naformátujte tyto hodnoty jako řetězce ( `ToString()`například voláním) a volání <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.

### <a name="multi-targeting"></a>Cílení na více platforem

Pokud potřebujete i nadále používat `Newtonsoft.Json` pro určité cílové architektury, můžete mít více cílů a mít dvě implementace. Nejedná se ale o triviální příkaz a by vyžadovala nějaké `#ifdefs` duplicity a zdroje. Jedním ze způsobů, jak sdílet co nejvíc kódů, je vytvořit obálku kolem `Utf8JsonWriter` a `Newtonsoft` `JsonTextWriter`. Tato obálka sjednotí oblast veřejného povrchu a současně izoluje rozdíly v chování. To umožňuje izolovat změny hlavně pro konstrukci typu. Následující knihovna [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) :

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Další materiály a zdroje informací

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.JsonPřehled](system-text-json-overview.md)
* [Jak používatSystem.Text.Json](system-text-json-how-to.md)
* [Postup zápisu vlastních převaděčů](system-text-json-converters-how-to.md)
* [Podpora DateTime a DateTimeOffset vSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonReference k rozhraní API](xref:System.Text.Json)
* [System.Text.Json. Reference k rozhraní API serializace](xref:System.Text.Json.Serialization)
