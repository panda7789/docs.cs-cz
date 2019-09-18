---
title: Třída MissingInteropDataException (.NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d916aa5e19b8ce583984d9a8e9708d34cf0adfb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049542"
---
# <a name="missinginteropdataexception-class-net-native"></a>Třída MissingInteropDataException (.NET Native)
**.NET pro aplikace pro Windows pro Windows 10, .NET Native jenom**  
  
 Výjimka, která je vyvolána při volání metody ručního zařazování, ale metadata pro typ nejsou nalezena statickou analýzou nebo v souboru direktiv modulu runtime.  
  
 **Hosting** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
> `MissingInteropDataException` Třída je určena výhradně pro vnitřní použití řetězcem nástroje .NET Native. Není určena pro použití v kódu třetí strany, ani byste neměli zpracovávat výjimku v kódu aplikace. Místo toho výjimku Eliminujte přidáním položek do [souboru direktiv modulu runtime](runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicializuje novou instanci `MissingInteropDataException` třídy pomocí ID zprávy zadané systémem, která popisuje chybu a typ, jehož data chybí. Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelsky definované informace o výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor s nápovědě spojený s touto výjimkou. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, což je kódovaná číselná hodnota, která je přiřazena k určité výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public Type MissingType { get; private set; }`|Získá nebo nastaví typ, jehož data chybí.|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objektu, který způsobil chybu. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string StackTrace { get; }`|Načte řetězcovou reprezentaci okamžitých snímků v zásobníku volání. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public MethodBase TargetSite { get; }`|Získá metodu, která vyvolala aktuální výjimku. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno <xref:System.Object>od.)|  
|`protected void Finalize()`|Umožňuje objektu uvolnit prostředky a provést jiné operace čištění před tím, než se uvolní uvolňováním paměti. (Zděděno <xref:System.Object>od.)|  
|`public Exception GetBaseException()`|Vrátí výjimku, která je hlavní příčinou jedné nebo více následných výjimek. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public int GetHashCode()`|Vrátí kód `MissingInteropDataException` hodnoty hash instance.   (Zděděno <xref:System.Object>od.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo> Nastaví objekt s informacemi o výjimce.  (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuálního objektu bez podstruktury. (Zděděno <xref:System.Object>od.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializovaná výjimka pro vytvoření objektu stavu výjimky, který obsahuje Serializovaná data o výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
  
## <a name="usage-details"></a>Podrobnosti o využití  
 Výjimka `MissingInteropDataException` je vyvolána, pokud volání metody modelu COM nebo prostředí Windows Runtime nelze úspěšně provést, protože informace o typu nejsou k dispozici.  
  
 Metadata, která jsou k dispozici pro aplikaci za běhu, jsou definována v souboru direktiv modulu runtime (konfigurace XML) \*,. Rd. XML. Chcete-li zabránit vaší aplikaci v vyvolání této výjimky, je nutné upravit tento soubor, aby definoval metadata, která musí být přítomna v době běhu. Nejčastěji tuto chybu řešíte tak, že přidáte `MarshalObject`atribut, `MarshalDelegate`nebo `MarshalStructure` do vhodného prvku programu v souboru direktiv modulu runtime. Informace o formátu tohoto souboru naleznete v tématu reference ke [konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že metadata potřebná vaší aplikací nejsou v době běhu k dispozici, neměli `try` byste tuto výjimku zpracovat v / `catch` bloku. Místo toho byste měli diagnostikovat příčinu výjimky a odstranit ji přidáním příslušné položky do souboru direktiv modulu runtime.  
  
 Třída obsahuje jediného jedinečného člena `MissingType` , vlastnost, která označuje typ, jehož metadata jsou zapotřebí pro úspěšné volání metody. `MissingInteropDataException` Všichni zbývající členové jsou děděni ze základní třídy <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Exception?displayProperty=nameWithType>
- [Třída MissingMetadataException](missingmetadataexception-class-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
