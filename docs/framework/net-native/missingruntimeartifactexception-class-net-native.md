---
title: Třída MissingRuntimeArtifactException (.NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7b138aec8a64683ca4b42cbbc8bd3584c06cc90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397046"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Třída MissingRuntimeArtifactException (.NET Native)
**Aplikace .NET pro Windows pro systém Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] pouze**  
  
 Výjimka, která se vyvolá, když je k dispozici metadata pro typ nebo člen typu, ale jeho implementace byl odebrán.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException` Třída je určený výhradně pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu. Rozhraní není určeno pro použití v kódu třetích stran, ani by měl zpracovat výjimku v kódu aplikace. Místo toho eliminovat výjimka přidáním položky do vaší [souboru direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Všimněte si, že `MissingRuntimeArtifactException` třída odvozená z <xref:System.MemberAccessException>.  
  
 `MissingRuntimeArtifactException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicializuje novou instanci třídy `MissingRuntimeArtifactException` pomocí zprávy poskytnuté systémem, která popisuje danou chybu.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
|`public MissingRuntimeArtifactException(String message)`|Inicializuje novou instanci třídy `MissingRuntimeArtifactException` se zadanou chybovou zprávu.<br /><br /> Tento konstruktor je pro interní použití rozhraním [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy, které jsou přidružené k této výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`, programového číselnou hodnotu, která je přiřazena k určité výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu, která popisuje aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objekt, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžitou rámce zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metody, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Object>.)|  
|`protected void Finalize()`|Umožňuje objektu zkuste uvolnit prostředky a dělat další operace čištění předtím, než je uvolněn systémem uvolňování paměti. (Zděděno z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrátí výjimka, která je hlavní příčinu jednu nebo více následujících výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí hodnotu hash pro `MissingRuntimeArtifactException` instance.   (Zděděno z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuální objekt bez podstruktury. (Zděděno z <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, když je serializováno výjimku vytvořit objekt výjimky stavu, který obsahuje serializovat data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti o použití  
 `MissingRuntimeArtifactException` Je vyvolána výjimka, když je proveden pokus o instanci typu nebo volají člena typu a, i když je typ nebo metadata člena je k dispozici, jeho implementace byla odebrána.  
  
 Jestli metadata a kód implementace dynamicky spuštění metody jsou k dispozici pro aplikaci v době běhu je definována pomocí souboru modulu runtime direktivy (konfigurační soubor XML), *. rd.xml. Chcete-li zabránit vyvolání výjimku vaší aplikace, je třeba upravit \*. rd.xml zajistit, že metadata potřebná podle typu nebo typ člen nachází v době běhu. Informace o formátu \*. rd.xml souboru, najdete v části [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Protože tato výjimka označuje, že kód implementace vyžaduje vaše aplikace není k dispozici v době běhu, by nemělo vyřizovat tato výjimka v `try` / `catch` bloku. Místo toho by měla určování příčin výjimky a vyloučení pomocí souboru direktivy modulu runtime. Obvykle odstranění této výjimky tak, že zadáte odpovídající `Activate` nebo `Dynamic` zásady pro program element v souboru direktivy modulu runtime (*. soubor rd.xml). Potřebujete-li na položku, která přidáte do souboru direktivy modulu runtime, který eliminuje výjimku, můžete provádět mezi dvěma Poradce při potížích:  
>   
>  -   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
> -   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
 `MissingRuntimeArtifactException` Třída neobsahuje žádné členy jedinečný; všechny její členy se dědí z její základní třída <xref:System.MemberAccessException>.  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
