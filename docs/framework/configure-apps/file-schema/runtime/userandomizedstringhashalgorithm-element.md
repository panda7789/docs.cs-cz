---
title: Element <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153774"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm> Element
Určuje, zda běžný jazyk runtime vypočítá kódy hash pro řetězce na základě domény aplikace.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Použít RandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda jsou kódy hash pro řetězce vypočteny na základě domény aplikace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`0`|Běžný jazyk runtime nevypočítává hash kódy pro řetězce na základě domény aplikace; jeden algoritmus se používá k výpočtu kódů hash řetězce. Toto nastavení je výchozí.|  
|`1`|Běžný jazyk runtime vypočítá hash kódy pro řetězce na základě domény aplikace. Identické řetězce v různých aplikačních doménách a v různých procesech budou mít různé hash kódy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím <xref:System.StringComparer> nastavení třída <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> a metoda používají jeden algoritmus hash, který vytváří konzistentní kód hash napříč aplikačními doménami. To je ekvivalentní `enabled` nastavení atributu `<UseRandomizedStringHashAlgorithm>` `0`prvku . Toto je algoritmus hash používaný v rozhraní .NET Framework 4.  
  
 Třída <xref:System.StringComparer> a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda můžete také použít jiný algoritmus hash, který vypočítá hash kódy na základě domény aplikace. V důsledku toho hash kódy pro ekvivalentní řetězce se budou lišit v rámci aplikačních domén. Jedná se o funkci opt-in; chcete-li jej využít, je `enabled` nutné `<UseRandomizedStringHashAlgorithm>` nastavit `1`atribut prvku na .  
  
 Vyhledávání řetězců v tabulce hash je obvykle operace O(1). Pokud však dojde k velkému počtu kolizí, může se vyhledávání stát operací O(n<sup>2).</sup> `<UseRandomizedStringHashAlgorithm>` Konfigurační prvek můžete použít ke generování algoritmu náhodného hash pro každý doméně aplikace, což zase omezuje počet potenciálních kolizí, zejména pokud jsou klíče, ze kterých jsou vypočteny hash kódy, založeny na vstupu dat uživateli.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `DisplayString` třídu, která obsahuje `s`konstantu soukromého řetězce , jejíž hodnota je "Toto je řetězec." Obsahuje také `ShowStringHashCode` metodu, která zobrazuje hodnotu řetězce a jeho kód hash spolu s názvem domény aplikace, ve které je metoda spuštěna.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Při spuštění příkladu bez zadání konfiguračního souboru se zobrazí výstup podobný následujícímu. Všimněte si, že hash kódy pro řetězec jsou identické ve dvou doménách aplikace.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Pokud však do adresáře příkladu přidáte následující konfigurační soubor a potom spusťte příklad, kódy hash pro stejný řetězec se budou lišit podle domény aplikace.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Pokud je konfigurační soubor k dispozici, v příkladu se zobrazí následující výstup:  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
