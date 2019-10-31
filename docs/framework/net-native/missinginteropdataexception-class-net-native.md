---
title: Třída MissingInteropDataException (.NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
ms.openlocfilehash: faf14245cd9dd7aa4bf8e89d5a05901279956509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128271"
---
# <a name="missinginteropdataexception-class-net-native"></a>Třída MissingInteropDataException (.NET Native)
**.NET pro aplikace pro Windows pro Windows 10, .NET Native jenom**  
  
 Výjimka, která je vyvolána při volání metody ručního zařazování, ale metadata pro typ nejsou nalezena statickou analýzou nebo v souboru direktiv modulu runtime.  
  
 **Obor názvů:** System. Runtime. CompilerServices  
  
> [!IMPORTANT]
> Třída `MissingInteropDataException` je určena výhradně pro vnitřní použití řetězcem nástroje .NET Native. Není určena pro použití v kódu třetí strany, ani byste neměli zpracovávat výjimku v kódu aplikace. Místo toho výjimku Eliminujte přidáním položek do [souboru direktiv modulu runtime](runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 Třída `MissingInteropDataException` má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicializuje novou instanci třídy `MissingInteropDataException` pomocí ID zprávy zadané systémem, která popisuje chybu a typ, jehož data chybí. Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelsky definované informace o výjimce. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor s nápovědě spojený s touto výjimkou. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, což je kódovaná číselná hodnota, která je přiřazena ke konkrétní výjimce. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Získá nebo nastaví typ, jehož data chybí.|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objektu, který způsobil chybu. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Načte řetězcovou reprezentaci okamžitých snímků v zásobníku volání. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metodu, která vyvolala aktuální výjimku. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno od <xref:System.Object>.)|  
|`protected void Finalize()`|Umožňuje objektu uvolnit prostředky a provést jiné operace čištění před tím, než se uvolní uvolňováním paměti. (Zděděno od <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrátí výjimku, která je hlavní příčinou jedné nebo více následných výjimek. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí kód hodnoty hash pro instanci `MissingInteropDataException`.   (Zděděno od <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví objekt <xref:System.Runtime.Serialization.SerializationInfo> o informace o výjimce.  (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuálního objektu bez podstruktury. (Zděděno od <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializovaná výjimka pro vytvoření objektu stavu výjimky, který obsahuje Serializovaná data o výjimce. (Zděděno od <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti o využití  
 Výjimka `MissingInteropDataException` je vyvolána, pokud volání metody do modelu COM nebo prostředí Windows Runtime nelze úspěšně provést, protože informace o typu nejsou k dispozici.  
  
 Metadata, která jsou k dispozici pro aplikaci za běhu, jsou definována v souboru direktiv modulu runtime (konfigurace XML) \*. Rd. XML. Chcete-li zabránit vaší aplikaci v vyvolání této výjimky, je nutné upravit tento soubor, aby definoval metadata, která musí být přítomna v době běhu. Nejčastěji tuto chybu řešíte přidáním atributu `MarshalObject`, `MarshalDelegate`nebo `MarshalStructure` do vhodného prvku programu v souboru direktiv modulu runtime. Informace o formátu tohoto souboru naleznete v tématu reference ke [konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že metadata potřebná vaší aplikací nejsou v době běhu k dispozici, neměli byste tuto výjimku zpracovat v `try`/`catch` bloku. Místo toho byste měli diagnostikovat příčinu výjimky a odstranit ji přidáním příslušné položky do souboru direktiv modulu runtime.  
  
 Třída `MissingInteropDataException` obsahuje jediného jedinečného člena, vlastnost `MissingType`, která označuje typ, jehož metadata jsou zapotřebí pro úspěšné volání metody. Všichni zbývající členové jsou děděni ze základní třídy <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Exception?displayProperty=nameWithType>
- [Třída MissingMetadataException](missingmetadataexception-class-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
