---
title: Třída MissingRuntimeArtifactException (.NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 7a69add45202b3ad838de592fadc82a84fa0ba5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180973"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Třída MissingRuntimeArtifactException (.NET Native)
**.NET pro aplikace pro Windows pro Windows 10, .NET Native jenom**  
  
 Výjimka, která je vyvolána, když jsou k dispozici metadata pro typ nebo člen typu, ale jeho implementace byla odebrána.  
  
 **Obor názvů:** System. Reflection  
  
> [!IMPORTANT]
> `MissingRuntimeArtifactException`Třída je určena výhradně pro vnitřní použití řetězcem nástroje .NET Native. Není určena pro použití v kódu třetí strany, ani byste neměli zpracovávat výjimku v kódu aplikace. Místo toho výjimku Eliminujte přidáním položek do [souboru direktiv modulu runtime](runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Všimněte si, že `MissingRuntimeArtifactException` Třída je odvozena z <xref:System.MemberAccessException> .  
  
 `MissingRuntimeArtifactException`Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Description|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicializuje novou instanci `MissingRuntimeArtifactException` třídy pomocí zprávy zadané systémem, která popisuje chybu.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|  
|`public MissingRuntimeArtifactException(String message)`|Inicializuje novou instanci `MissingRuntimeArtifactException` třídy se zadanou chybovou zprávou.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelsky definované informace o výjimce. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor s nápovědě spojený s touto výjimkou. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT` kódovanou číselnou hodnotu, která je přiřazena k určité výjimce. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objektu, který způsobil chybu. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string StackTrace { get; }`|Načte řetězcovou reprezentaci okamžitých snímků v zásobníku volání. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public MethodBase TargetSite { get; }`|Získá metodu, která vyvolala aktuální výjimku. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určí, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno od <xref:System.Object> .)|  
|`protected void Finalize()`|Umožňuje objektu uvolnit prostředky a provést jiné operace čištění před tím, než se uvolní uvolňováním paměti. (Zděděno od <xref:System.Object> .)|  
|`public Exception GetBaseException()`|Vrátí výjimku, která je hlavní příčinou jedné nebo více následných výjimek. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int GetHashCode()`|Vrátí kód hodnoty hash `MissingRuntimeArtifactException` instance.   (Zděděno od <xref:System.Object> .)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuálního objektu bez podstruktury. (Zděděno od <xref:System.Object> .)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="events"></a>Události  
  
|Událost|Description|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializovaná výjimka pro vytvoření objektu stavu výjimky, který obsahuje Serializovaná data o výjimce. (Zděděno od <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="usage-details"></a>Podrobnosti využití  
 `MissingRuntimeArtifactException`Výjimka je vyvolána, když dojde k pokusu o vytvoření instance typu nebo vyvolat člen typu a, i když je přítomna metadata typu nebo člena, jeho implementace byla odebrána.  
  
 Zda jsou metadata a implementační kód dynamicky spouštěny metodou k dispozici pro aplikaci v době běhu, je definována v souboru direktiv modulu runtime (konfigurace XML), \* . Rd. XML. Chcete-li zabránit vaší aplikaci v vyvolání této výjimky, je nutné upravit \* soubor. Rd. XML, aby bylo zajištěno, že metadata potřebná pro typ nebo člen typu jsou přítomna v době běhu. Informace o formátu \* souboru. Rd. XML naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že implementační kód požadovaný vaší aplikací není v době běhu k dispozici, neměli byste tuto výjimku zpracovat v `try` / `catch` bloku. Místo toho byste měli diagnostikovat příčinu výjimky a odstranit ji pomocí souboru direktiv modulu runtime. Obvykle Eliminujte tuto výjimku zadáním vhodného `Activate` nebo `Dynamic` zásad pro element programu v souboru direktiv modulu runtime ( \* soubor. Rd. XML). Chcete-li získat položku, kterou můžete přidat do souboru direktiv modulu runtime, který eliminuje výjimku, můžete použít jeden ze dvou poradců při potížích:  
>
> - [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
> - Metody [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
 `MissingRuntimeArtifactException`Třída neobsahuje žádné jedinečné členy. všichni její členové jsou děděni z její základní třídy, <xref:System.MemberAccessException> .  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
