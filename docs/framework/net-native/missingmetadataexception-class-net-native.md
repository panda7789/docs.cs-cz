---
title: Třída MissingMetadataException (.NET Native)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2961a4c02d8ffe17055307094f56a03680d1a59a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357128"
---
# <a name="missingmetadataexception-class-net-native"></a>Třída MissingMetadataException (.NET Native)

**.NET pro aplikace pro Windows pro Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze**

Výjimka, která je vyvolána při reflexi slouží k načtení metadat, která není k dispozici.

**Namespace:** System.Reflection

> [!IMPORTANT]
> `MissingMetadataException` Třídy je určený výhradně pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce. Není určena pro použití v kódu třetí strany ani by měl zpracování výjimek v kódu aplikace. Místo toho odstranit výjimky tak, že přidáte položky do vašich [soubor direktiv modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.

## <a name="syntax"></a>Syntaxe

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

Všimněte si, že `MissingMetadataException` třída odvozena z <xref:System.TypeAccessException>.

`MissingMetadataException` Třída má následující členy:

## <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-----------------|-----------------|
|`public MissingMetadataException()`|Inicializuje novou instanci třídy `MissingMetadataException` pomocí zprávy poskytnuté systémem, popisující chybu.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|
|`public MissingMetadataException(String message)`|Inicializuje novou instanci třídy `MissingMetadataException` třídy pomocí zadané chybové zprávy.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|

## <a name="properties"></a>Vlastnosti

|Vlastnost|Popis|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Získá kolekci dvojic klíč/hodnota, která poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy spojený s touto výjimkou. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, programové číselnou hodnotu, která je přiřazena určité výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno z <xref:System.TypeLoadException>.)|
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objekt, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžité rámce v zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public MethodBase TargetSite { get; }`|Získá metody, která vyvolala aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string TypeName { get; ]`|Získá plně kvalifikovaný název typu, jehož metadat se nenašel. (Zděděno z <xref:System.TypeLoadException>.)|

## <a name="methods"></a>Metody

|Metoda|Popis|
|------------|-----------------|
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected void Finalize()`|Umožňuje objektu pro pokus o uvolnění prostředků a provádět jiné operace čištění před je uvolněn systémem uvolňování paměti. (Zděděno z <xref:System.Object>.)|
|`public Exception GetBaseException()`|Vrací výjimku, která je hlavní příčinou jednu nebo více následujících výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int GetHashCode()`|Vrátí hodnotu hash pro `MissingMetadataException` instance.   (Zděděno z <xref:System.Object>.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.TypeLoadException>.)|
|`public Type GetType()`|Získá typ runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected Object MemberwiseClone()`|Vytvoří Mělkou kopii aktuálního objektu. (Zděděno z <xref:System.Object>.)|
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="events"></a>Události

|Událost|Popis|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializována výjimku pro vytvoření objektu výjimky stavu, který obsahuje serializovaná data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="usage-details"></a>Podrobnosti o použití

`MissingMetadataException` Při reflexi slouží k přístupu k metadatům, která není k dispozici v sestavení, je vyvolána výjimka.

Metadata, která je k dispozici pro aplikace v době běhu je definován pomocí souboru modulu runtime direktivy (konfiguraci XML), *. rd.xml. Chcete-li zabránit aplikaci v vyvolání této výjimky, je třeba upravit \*. RD.XML, které definují metadata, která musí existovat v době běhu. Informace o formátu \*. soubor rd.xml, naleznete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že metadata aplikace není k dispozici v době běhu, by nemělo vyřizovat této výjimky v `try` / `catch` bloku. Místo toho by měl diagnostikovat příčinu chyby a eliminovat pomocí souboru direktiv modulu runtime. Chcete-li získat položku, která přidáte do souboru direktiv modulu runtime, které předchází výjimku, můžete použít jednu z dvou Poradce při potížích:
>
> - [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.
> - [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pro metody.

`MissingMetadataException` Třída neobsahuje žádné členy jedinečných; všichni její členové jsou zděděny ze své základní třídy <xref:System.TypeAccessException>.

## <a name="see-also"></a>Viz také:

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [Třída MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [Třída MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
