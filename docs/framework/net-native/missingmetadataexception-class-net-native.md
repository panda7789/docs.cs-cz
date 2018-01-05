---
title: "Třída MissingMetadataException (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 168ff7743aa33ac05309e55b0284c23c8bd087a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="missingmetadataexception-class-net-native"></a>Třída MissingMetadataException (.NET Native)
**Aplikace .NET pro Windows pro systém Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze**  
  
 Výjimka, která se vyvolá, když reflexe se používá k načtení metadat, která není přítomen.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingMetadataException` Třída je určený výhradně pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu. Rozhraní není určeno pro použití v kódu třetích stran, ani by měl zpracovat výjimku v kódu aplikace. Místo toho eliminovat výjimka přidáním položky do vaší [souboru direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]  
  
 Všimněte si, že `MissingMetadataException` třída odvozená z <xref:System.TypeAccessException>.  
  
 `MissingMetadataException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingMetadataException()`|Inicializuje novou instanci třídy `MissingMetadataException` pomocí zprávy poskytnuté systémem, která popisuje danou chybu.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
|`public MissingMetadataException(String message)`|Inicializuje novou instanci třídy `MissingMetadataException` se zadanou chybovou zprávu.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze torol řetězu.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy, které jsou přidružené k této výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, programového číselnou hodnotu, která je přiřazena k určité výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu, která popisuje aktuální výjimku. (Zděděno z <xref:System.TypeLoadException>.)|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objekt, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžitou rámce zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metody, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string TypeName { get; ]`|Získá plně kvalifikovaný název typu, jejichž metadata nebyla nalezena. (Zděděno z <xref:System.TypeLoadException>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected void Finalize()`|Umožňuje objektu zkuste uvolnit prostředky a dělat další operace čištění předtím, než je uvolněn systémem uvolňování paměti. (Zděděno z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrátí výjimka, která je hlavní příčinu jednu nebo více následujících výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí hodnotu hash pro `MissingMetadataException` instance.   (Zděděno z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.TypeLoadException>.)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuální objekt bez podstruktury. (Zděděno z <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, když je serializováno výjimku vytvořit objekt výjimky stavu, který obsahuje serializovat data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti o použití  
 `MissingMetadataException` Při reflexe slouží k přístupu metadata, která není k dispozici v sestavení je vyvolána výjimka.  
  
 Metadata, která je k dispozici pro aplikaci v době běhu je definována pomocí souboru modulu runtime direktivy (konfigurační soubor XML), *. rd.xml. Chcete-li zabránit vyvolání výjimku vaší aplikace, je třeba upravit \*. rd.xml k definování metadata, která musí být v době běhu. Informace o formátu \*. rd.xml souboru, najdete v části [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Protože tato výjimka označuje, že metadata potřebná vaše aplikace není k dispozici v době běhu, by nemělo vyřizovat tato výjimka v `try` / `catch` bloku. Místo toho by měla určování příčin výjimky a vyloučení pomocí souboru direktivy modulu runtime. Potřebujete-li na položku, která přidáte do souboru direktivy modulu runtime, který eliminuje výjimku, můžete provádět mezi dvěma Poradce při potížích:  
>   
>  -   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
> -   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
 `MissingMetadataException` Třída neobsahuje žádné členy jedinečný; všechny její členy se dědí z její základní třída <xref:System.TypeAccessException>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Exception?displayProperty=nameWithType>  
 <xref:System.TypeAccessException>  
 [Třída MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [Třída MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
