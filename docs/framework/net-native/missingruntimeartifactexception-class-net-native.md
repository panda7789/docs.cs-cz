---
title: Třída MissingRuntimeArtifactException (.NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa882762479995448a99d9cb63fbdea941a253d4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049494"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Třída MissingRuntimeArtifactException (.NET Native)
**.NET pro aplikace pro Windows pro Windows 10, .NET Native jenom**  
  
 Výjimka, která je vyvolána, když jsou k dispozici metadata pro typ nebo člen typu, ale jeho implementace byla odebrána.  
  
 **Hosting** System. Reflection  
  
> [!IMPORTANT]
> `MissingRuntimeArtifactException` Třída je určena výhradně pro vnitřní použití řetězcem nástroje .NET Native. Není určena pro použití v kódu třetí strany, ani byste neměli zpracovávat výjimku v kódu aplikace. Místo toho výjimku Eliminujte přidáním položek do [souboru direktiv modulu runtime](runtime-directives-rd-xml-configuration-file-reference.md). Další informace najdete v části poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Všimněte si, `MissingRuntimeArtifactException` že třída je odvozena z. <xref:System.MemberAccessException>  
  
 `MissingRuntimeArtifactException` Třída má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicializuje novou instanci `MissingRuntimeArtifactException` třídy pomocí zprávy zadané systémem, která popisuje chybu.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|  
|`public MissingRuntimeArtifactException(String message)`|Inicializuje novou instanci třídy `MissingRuntimeArtifactException` třídy pomocí zadané chybové zprávy.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcem nástroje .NET Native.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelsky definované informace o výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor s nápovědě spojený s touto výjimkou. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public int HResult { get; protected set; }`|Získá nebo nastaví `HRESULT`kódovanou číselnou hodnotu, která je přiřazena k určité výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string Message { get; }`|Získá zprávu s popisem aktuální výjimky. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objektu, který způsobil chybu. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public string StackTrace { get; }`|Načte řetězcovou reprezentaci okamžitých snímků v zásobníku volání. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public MethodBase TargetSite { get; }`|Získá metodu, která vyvolala aktuální výjimku. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno <xref:System.Object>od.)|  
|`protected void Finalize()`|Umožňuje objektu uvolnit prostředky a provést jiné operace čištění před tím, než se uvolní uvolňováním paměti. (Zděděno <xref:System.Object>od.)|  
|`public Exception GetBaseException()`|Vrátí výjimku, která je hlavní příčinou jedné nebo více následných výjimek. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public int GetHashCode()`|Vrátí kód `MissingRuntimeArtifactException` hodnoty hash instance.   (Zděděno <xref:System.Object>od.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo> Nastaví objekt s informacemi o výjimce.  (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`public Type GetType()`|Získá typ modulu runtime aktuální instance. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
|`protected Object MemberwiseClone()`|Vytvoří kopii aktuálního objektu bez podstruktury. (Zděděno <xref:System.Object>od.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
  
## <a name="events"></a>Události  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Nastane, pokud je serializovaná výjimka pro vytvoření objektu stavu výjimky, který obsahuje Serializovaná data o výjimce. (Zděděno <xref:System.Exception?displayProperty=nameWithType>od.)|  
  
## <a name="usage-details"></a>Podrobnosti o využití  
 Výjimka `MissingRuntimeArtifactException` je vyvolána, když dojde k pokusu o vytvoření instance typu nebo vyvolat člen typu a, i když je přítomna metadata typu nebo člena, jeho implementace byla odebrána.  
  
 Zda jsou metadata a implementační kód dynamicky spouštěny metodou k dispozici pro aplikaci v době běhu, je definována v souboru direktiv modulu runtime (konfigurace XML), \*. Rd. XML. Chcete-li zabránit vaší aplikaci v vyvolání této výjimky, je \*nutné upravit soubor. Rd. XML, aby bylo zajištěno, že metadata potřebná pro typ nebo člen typu jsou přítomna v době běhu. Informace o formátu \*souboru. Rd. XML naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že implementační kód požadovaný vaší aplikací není v době běhu k dispozici, neměli byste `try` tuto výjimku zpracovat v / `catch` bloku. Místo toho byste měli diagnostikovat příčinu výjimky a odstranit ji pomocí souboru direktiv modulu runtime. Obvykle Eliminujte tuto výjimku zadáním vhodného `Activate` nebo `Dynamic` zásad pro element programu v souboru direktiv modulu runtime (\*soubor. Rd. XML). Chcete-li získat položku, kterou můžete přidat do souboru direktiv modulu runtime, který eliminuje výjimku, můžete použít jeden ze dvou poradců při potížích:  
>   
> - [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
> - Metody [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
 Třída neobsahuje žádné jedinečné členy. všichni její členové jsou děděni z její základní třídy, <xref:System.MemberAccessException>. `MissingRuntimeArtifactException`  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
