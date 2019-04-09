---
title: Třída MissingInteropDataException (.NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31208a63caaf9158f12742f1547b0e1e2781de4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137953"
---
# <a name="missinginteropdataexception-class-net-native"></a>Třída MissingInteropDataException (.NET Native)
**.NET pro aplikace pro Windows pro Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze**  
  
 Výjimka, která je vyvolána při zařazování metoda ruční nazývá, ale metadata pro typ nebyl nalezen ve statické analýzy nebo do souboru direktiv modulu runtime.  
  
 **Namespace:** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  `MissingInteropDataException` Třídy je určený výhradně pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce. Není určena pro použití v kódu třetí strany ani by měl zpracování výjimek v kódu aplikace. Místo toho odstranit výjimky tak, že přidáte položky do vašich [soubor direktiv modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicializuje novou instanci třídy `MissingInteropDataException` pomocí ID zprávy poskytnuté systémem, která popisuje chybu a typ, jejichž data se nenašel. Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci dvojic klíč/hodnota, která poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy spojený s touto výjimkou. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, což je programový číselnou hodnotu, která je přiřazena určité výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Získá nebo nastaví typ, jejichž data se nenašel.|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objekt, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžité rámce v zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metody, která vyvolala aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Object>.)|  
|`protected void Finalize()`|Umožňuje objektu pro pokus o uvolnění prostředků a provádět jiné operace čištění před je uvolněn systémem uvolňování paměti. (Zděděno z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrací výjimku, která je hlavní příčinou jednu nebo více následujících výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí hodnotu hash pro `MissingInteropDataException` instance.   (Zděděno z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Získá typ runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří Mělkou kopii aktuálního objektu. (Zděděno z <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializována výjimku pro vytvoření objektu výjimky stavu, který obsahuje serializovaná data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti o použití  
 `MissingInteropDataException` Je vyvolána výjimka při volání metody na komponentu COM nebo prostředí Windows Runtime není úspěšně provést, protože není k dispozici informace o typu.  
  
 Metadata, která je k dispozici pro aplikace v době běhu je definován pomocí souboru modulu runtime direktivy (konfiguraci XML), *. rd.xml. Aby vaše aplikace na vyvolání této výjimky, je třeba upravit tento soubor k definování metadata, která musí být k dispozici v době běhu. Nejčastěji, tuto chybu vyřešíte tak, že přidáte `MarshalObject`, `MarshalDelegate`, nebo `MarshalStructure` atribut pro příslušnou aplikaci prvku v souboru direktivy modulu runtime. Informace o formátu tohoto souboru najdete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že tato výjimka označuje, že metadata aplikace není k dispozici v době běhu, by nemělo vyřizovat této výjimky v `try` / `catch` bloku. Místo toho by měl diagnostikovat příčinu chyby a eliminovat tak, že přidáte na příslušnou položku do souboru direktiv modulu runtime.  
  
 `MissingInteropDataException` Třída obsahuje jeden člen jedinečné, `MissingType` vlastnost, která určuje typ, jehož metadat je potřebná pro volání metody úspěšné. Všechny zbývající členy se dědí ze základní třídy <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Exception?displayProperty=nameWithType>
- [Třída MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
