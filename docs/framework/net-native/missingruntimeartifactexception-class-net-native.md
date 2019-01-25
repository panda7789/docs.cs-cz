---
title: Třída MissingRuntimeArtifactException (.NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4dd7ef41cb935bf2b9808f730c288c29198720b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687268"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Třída MissingRuntimeArtifactException (.NET Native)
**.NET pro aplikace pro Windows pro Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze**  
  
 Výjimka, která je vyvolána, když je k dispozici metadat pro typ nebo člen typu, ale byla odebrána jeho implementace.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException` Třídy je určený výhradně pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce. Není určena pro použití v kódu třetí strany ani by měl zpracování výjimek v kódu aplikace. Místo toho odstranit výjimky tak, že přidáte položky do vašich [soubor direktiv modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Všimněte si, že `MissingRuntimeArtifactException` třída odvozena z <xref:System.MemberAccessException>.  
  
 `MissingRuntimeArtifactException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicializuje novou instanci třídy `MissingRuntimeArtifactException` pomocí zprávy poskytnuté systémem, popisující chybu.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
|`public MissingRuntimeArtifactException(String message)`|Inicializuje novou instanci třídy `MissingRuntimeArtifactException` třídy pomocí zadané chybové zprávy.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci dvojic klíč/hodnota, která poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy spojený s touto výjimkou. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, programové číselnou hodnotu, která je přiřazena určité výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objekt, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžité rámce v zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metody, která vyvolala aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Object>.)|  
|`protected void Finalize()`|Umožňuje objektu pro pokus o uvolnění prostředků a provádět jiné operace čištění před je uvolněn systémem uvolňování paměti. (Zděděno z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrací výjimku, která je hlavní příčinou jednu nebo více následujících výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí hodnotu hash pro `MissingRuntimeArtifactException` instance.   (Zděděno z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Získá typ runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří Mělkou kopii aktuálního objektu. (Zděděno z <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializována výjimku pro vytvoření objektu výjimky stavu, který obsahuje serializovaná data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti o použití  
 `MissingRuntimeArtifactException` Je vyvolána výjimka, když je proveden pokus o vytvoření instance typu nebo vyvolat člena typu, i když typ nebo člena metadat je k dispozici, byla odebrána jeho implementace.  
  
 Určuje, zda metadat a implementace kódu dynamicky spuštění metody jsou k dispozici pro aplikace v době běhu je definovaný souborem direktivy (konfiguraci XML) modulu runtime, \*. rd.xml. Chcete-li zabránit aplikaci v vyvolání této výjimky, je třeba upravit \*. RD.XML, které k zajištění, že je k dispozici v době běhu metadat vyžaduje typ nebo člen typu. Informace o formátu \*. soubor rd.xml, naleznete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že tato výjimka označuje, že implementace kódu, které vaše aplikace vyžaduje není k dispozici v době běhu, by nemělo vyřizovat této výjimky v `try` / `catch` bloku. Místo toho by měl diagnostikovat příčinu chyby a eliminovat pomocí souboru direktiv modulu runtime. Obvykle odstranění této výjimky tak, že zadáte odpovídající `Activate` nebo `Dynamic` zásady program elementu v souboru direktiv modulu runtime (\*. soubor rd.xml). Chcete-li získat položku, která přidáte do souboru direktiv modulu runtime, které předchází výjimku, můžete použít jednu z dvou Poradce při potížích:  
>   
> - [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
> - [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
 `MissingRuntimeArtifactException` Třída neobsahuje žádné členy jedinečných; všichni její členové jsou zděděny ze své základní třídy <xref:System.MemberAccessException>.  
  
## <a name="see-also"></a>Viz také:
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
