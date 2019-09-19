---
title: Třída MissingMetadataException (.NET Native)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 251d63fe8e025fe73b148c7deb368ab95ca3b1f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049471"
---
# <a name="missingmetadataexception-class-net-native"></a>Třída MissingMetadataException (.NET Native)

**.NET pro aplikace pro Windows pro Windows 10, .NET Native jenom**

Výjimka, která je vyvolána, když je použita reflexe k načtení metadat, která nejsou k dispozici.

**Hosting** System. Reflection

> [!IMPORTANT]
> `MissingMetadataException` Třída je určena výhradně pro vnitřní použití řetězcem nástroje .NET Native. Není určena pro použití v kódu třetí strany, ani byste neměli zpracovávat výjimku v kódu aplikace. Místo toho výjimku Eliminujte přidáním položek do [souboru direktiv modulu runtime](runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.

## <a name="syntax"></a>Syntaxe

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

Všimněte si, `MissingMetadataException` že třída je odvozena z. <xref:System.TypeAccessException>

`MissingMetadataException` Třída má následující členy:

## <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-----------------|-----------------|
|`public MissingMetadataException()`|Inicializuje novou instanci `MissingMetadataException` třídy pomocí zprávy zadané systémem, která popisuje chybu.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|
|`public MissingMetadataException(String message)`|Inicializuje novou instanci třídy `MissingMetadataException` třídy pomocí zadané chybové zprávy.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|

## <a name="properties"></a>Vlastnosti

|Vlastnost|Popis|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelsky definované informace o výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor s nápovědě spojený s touto výjimkou. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`kódovanou číselnou hodnotu, která je přiřazena k určité výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno <xref:System.TypeLoadException>od.)|
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objektu, který způsobil chybu. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public string StackTrace { get; }`|Načte řetězcovou reprezentaci okamžitých snímků v zásobníku volání. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public MethodBase TargetSite { get; }`|Získá metodu, která vyvolala aktuální výjimku. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public string TypeName { get; ]`|Získá plně kvalifikovaný název typu, jehož metadata chybí. (Zděděno <xref:System.TypeLoadException>od.)|

## <a name="methods"></a>Metody

|Metoda|Popis|
|------------|-----------------|
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`protected void Finalize()`|Umožňuje objektu uvolnit prostředky a provést jiné operace čištění před tím, než se uvolní uvolňováním paměti. (Zděděno <xref:System.Object>od.)|
|`public Exception GetBaseException()`|Vrátí výjimku, která je hlavní příčinou jedné nebo více následných výjimek. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`public int GetHashCode()`|Vrátí kód `MissingMetadataException` hodnoty hash instance.   (Zděděno <xref:System.Object>od.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo> Nastaví objekt s informacemi o výjimce.  (Zděděno <xref:System.TypeLoadException>od.)|
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuálního objektu bez podstruktury. (Zděděno <xref:System.Object>od.)|
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|

## <a name="events"></a>Události

|Událost|Popis|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializovaná výjimka pro vytvoření objektu stavu výjimky, který obsahuje Serializovaná data o výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|

## <a name="usage-details"></a>Podrobnosti o využití

Výjimka `MissingMetadataException` je vyvolána, když je použita reflexe k přístupu k metadatům, která nejsou k dispozici v sestavení.

Metadata, která jsou k dispozici pro aplikaci za běhu, jsou definována v souboru direktiv modulu runtime (konfigurace XML) \*,. Rd. XML. Chcete-li zabránit vaší aplikaci v vyvolání této výjimky, je \*nutné upravit soubor. Rd. XML, aby bylo možné definovat metadata, která musí být přítomna v době běhu. Informace o formátu \*souboru. Rd. XML naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že metadata potřebná vaší aplikací nejsou v době běhu k dispozici, neměli `try` byste tuto výjimku zpracovat v / `catch` bloku. Místo toho byste měli diagnostikovat příčinu výjimky a odstranit ji pomocí souboru direktiv modulu runtime. Chcete-li získat položku, kterou můžete přidat do souboru direktiv modulu runtime, který eliminuje výjimku, můžete použít jeden ze dvou poradců při potížích:
>
> - [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.
> - Metody [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .

Třída neobsahuje žádné jedinečné členy. všichni její členové jsou děděni z její základní třídy, <xref:System.TypeAccessException>. `MissingMetadataException`

## <a name="see-also"></a>Viz také:

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [Třída MissingInteropDataException](missinginteropdataexception-class-net-native.md)
- [Třída MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
