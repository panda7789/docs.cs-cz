---
title: Třída MissingRuntimeArtifactException (.NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 7a69add45202b3ad838de592fadc82a84fa0ba5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180973"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Třída MissingRuntimeArtifactException (.NET Native)
**Rozhraní .NET pro aplikace pro Windows pro Windows 10, pouze nativní .NET**  
  
 Výjimka, která je vyvolána, když metadata pro typ nebo člen typu je k dispozici, ale jeho implementace byla odebrána.  
  
 **Obor názvů:** System.reflection  
  
> [!IMPORTANT]
> Třída `MissingRuntimeArtifactException` je určena výhradně pro interní použití řetězce nástrojů .NET Native. Není určen pro použití v kódu jiného výrobce, ani byste měli zpracovávat výjimku v kódu aplikace. Místo toho můžete vyloučit výjimku přidáním položek do [souboru direktiv runtime](runtime-directives-rd-xml-configuration-file-reference.md). Další informace naleznete v části Poznámky.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Všimněte `MissingRuntimeArtifactException` si, že <xref:System.MemberAccessException>třída je odvozena od .  
  
 Třída `MissingRuntimeArtifactException` má následující členy:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicializuje novou instanci `MissingRuntimeArtifactException` třídy pomocí systémem zadané zprávy, která popisuje chybu.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcenástrojů .NET Native.|  
|`public MissingRuntimeArtifactException(String message)`|Inicializuje novou instanci `MissingRuntimeArtifactException` třídy se zadanou chybovou zprávou.<br /><br /> Tento konstruktor je určen pouze pro interní použití řetězcenástrojů .NET Native.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Získá kolekci párů klíč/hodnota, které poskytují další uživatelem definované informace o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Získá nebo nastaví odkaz na soubor nápovědy přidružený k této výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Získá nebo `HRESULT`nastaví , kódované číselné hodnoty, která je přiřazena k určité výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Získá výjimku, která způsobila aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Získá zprávu, která popisuje aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Získá nebo nastaví název aplikace nebo objektu, který způsobil chybu. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Získá řetězcovou reprezentaci okamžité rámce v zásobníku volání. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Získá metodu, která vyvolala aktuální výjimku. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Určí, zda se zadaný objekt rovná aktuálnímu objektu.  (Zděděno z <xref:System.Object>.)|  
|`protected void Finalize()`|Umožňuje objektu pokusit se uvolnit prostředky a provést další operace čištění před tím, než je uvolněn a uvolnění paměti. (Zděděno z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Vrátí výjimku, která je hlavní příčinou jedné nebo více následných výjimek. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Vrátí kód hash `MissingRuntimeArtifactException` pro instanci.   (Zděděno z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Nastaví <xref:System.Runtime.Serialization.SerializationInfo> objekt s informacemi o výjimce.  (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Získá typ runtime aktuální instance. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Vytvoří mělkou kopii aktuálního objektu. (Zděděno z <xref:System.Object>.)|  
|`public string ToString()`|Vrátí řetězcovou reprezentaci aktuální výjimky. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Akce  
  
|Událost|Popis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Vyvolá se při serializování výjimky, která vytvoří objekt stavu výjimky, který obsahuje serializovaná data o výjimce. (Zděděno z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Podrobnosti využití  
 Výjimka `MissingRuntimeArtifactException` je vyvolána při pokusu o vytvoření instance typu nebo vyvolání člena typu a přestože je k dispozici metadata typu nebo člena, jeho implementace byla odebrána.  
  
 To, zda jsou metadata a kód implementace pro dynamické spuštění metody k dispozici aplikaci za běhu, \*je definováno souborem direktiv runtime (konfigurace XML) .rd.xml. Chcete-li aplikaci zabránit ve vyvolání \*této výjimky, je nutné upravit soubor RD.xml, aby bylo zajištěno, že metadata potřebná pro člena typu nebo typu jsou k dispozici za běhu. Informace o formátu souboru \*RD.XML naleznete v [tématu Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že tato výjimka označuje, že kód implementace, který vaše `try` / `catch` aplikace není k dispozici za běhu, neměli byste tuto výjimku zpracovávat v bloku. Místo toho byste měli diagnostikovat příčinu výjimky a odstranit ji pomocí souboru direktiv runtime. Obvykle tuto výjimku odstraníte zadáním `Activate` `Dynamic` příslušného prvku nebo zásady pro prvek\*programu v souboru direktiv runtime directiveíků ( soubor rd.xml). Chcete-li získat položku, kterou můžete přidat do souboru direktiv runtime, která eliminuje výjimku, můžete použít jeden ze dvou poradců při potížích:  
>
> - Poradce [při potížích s výjimkou metadat](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
> - Poradce [při potížích s výjimkou metadat](https://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
 Třída `MissingRuntimeArtifactException` neobsahuje žádné jedinečné členy; všichni jeho členové jsou zděděni <xref:System.MemberAccessException>ze své základní třídy .  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
