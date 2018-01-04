---
title: "Třída MissingInteropDataException (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caf3882b8ba9c684d4751cafb5719606125dd983
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="missinginteropdataexception-class-net-native"></a>Třída MissingInteropDataException (.NET Native)
**Aplikace .NET pro Windows pro systém Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze**  
  
 Výjimka, která se vyvolá, když ruční zařazování metoda je volána, ale metadata pro typ nebyl nalezen statické analýzou nebo v souboru direktivy modulu runtime.  
  
 **Namespace:** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  `MissingInteropDataException` Třída je určený výhradně pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu. Rozhraní není určeno pro použití v kódu třetích stran, ani by měl zpracovat výjimku v kódu aplikace. Místo toho eliminovat výjimka přidáním položky do vaší [souboru direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicializuje novou instanci třídy `MissingInteropDataException` pomocí ID zprávy poskytnuté systémem, která popisuje chybu a typ, jejichž data chybí. Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy, které jsou přidružené k této výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, což je programové číselnou hodnotu, která je přiřazena k určité výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu, která popisuje aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Získá nebo nastaví typ, jejichž data nebyla nalezena.|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objekt, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžitou rámce zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metody, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Object>.)|  
|`protected void Finalize()`|Umožňuje objektu zkuste uvolnit prostředky a dělat další operace čištění předtím, než je uvolněn systémem uvolňování paměti. (Zděděno z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrátí výjimka, která je hlavní příčinu jednu nebo více následujících výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí hodnotu hash pro `MissingInteropDataException` instance.   (Zděděno z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuální objekt bez podstruktury. (Zděděno z <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, když je serializováno výjimku vytvořit objekt výjimky stavu, který obsahuje serializovat data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti o použití  
 `MissingInteropDataException` Při volání metody komponentu COM nebo prostředí Windows Runtime nelze úspěšně vytvořit, protože není k dispozici informace o typu, je vyvolána výjimka.  
  
 Metadata, která je k dispozici pro aplikaci v době běhu je definována pomocí souboru modulu runtime direktivy (konfigurační soubor XML), *. rd.xml. Chcete-li zabránit vyvolání výjimku vaší aplikace, musíte upravit tohoto souboru můžete definovat metadata, která musí být v době běhu. Nejčastěji vyřešit tuto chybu tak, že přidáte `MarshalObject`, `MarshalDelegate`, nebo `MarshalStructure` atribut program odpovídající element v souboru direktivy modulu runtime. Informace o formátu tohoto souboru najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Protože tato výjimka označuje, že metadata potřebná vaše aplikace není k dispozici v době běhu, by nemělo vyřizovat tato výjimka v `try` / `catch` bloku. Místo toho by měla určování příčin výjimky a eliminovat přidáním na příslušnou položku do souboru direktivy modulu runtime.  
  
 `MissingInteropDataException` Třída obsahuje jedinečný jednoho člena, `MissingType` vlastnost, která určuje typ jejichž metadat je potřeba pro volání metody úspěšné. Ze základní třídy dědí všechny zbývající členy <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Exception?displayProperty=nameWithType>  
 [Třída MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
