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
ms.openlocfilehash: cc9708b8cca6520932fbf0e1975a05cad5fad485
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115044"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<element > UseRandomizedStringHashAlgorithm
Určuje, zda modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm >**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda jsou kódy hash pro řetězce počítány na základě domény aplikace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`0`|Modul CLR (Common Language Runtime) nepočítá kódy hash pro řetězce na základě domény aplikace. k výpočtu řetězcových kódů hash se používá jeden algoritmus. Toto nastavení je výchozí.|  
|`1`|Modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace. Identické řetězce v různých aplikačních doménách a v různých procesech budou mít různé kódy hash.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení používá třída <xref:System.StringComparer> a metoda <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> jeden algoritmus hash, který vytváří konzistentní kód hash napříč doménami aplikace. To je ekvivalentní nastavení atributu `enabled` `<UseRandomizedStringHashAlgorithm>` elementu na `0`. Toto je algoritmus hash používaný v .NET Framework 4.  
  
 Třída <xref:System.StringComparer> a metoda <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> mohou také použít jiný algoritmus hash, který vypočítává kódy hash pro každou doménu aplikace. V důsledku toho se kódy hash pro ekvivalentní řetězce budou lišit napříč doménami aplikace. Toto je funkce výslovného souhlasu; abyste ho mohli využít, musíte nastavit atribut `enabled` `<UseRandomizedStringHashAlgorithm>` elementu na `1`.  
  
 Vyhledávání řetězců v zatřiďovací tabulce je obvykle operace O (1). Pokud ale dojde k velkému počtu kolizí, vyhledávání se může stát operací O (n<sup>2</sup>). Můžete použít prvek konfigurace `<UseRandomizedStringHashAlgorithm>` k vygenerování náhodného algoritmu hash pro každou doménu aplikace, která zase omezuje počet potenciálních kolizí, zejména v případě, že klíče, ze kterých jsou vypočítány hodnoty hash, jsou založeny na vstupu dat mohou.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje třídu `DisplayString`, která obsahuje soukromou řetězcovou konstantu, `s`, jejíž hodnota je "Toto je řetězec." Obsahuje také metodu `ShowStringHashCode`, která zobrazuje hodnotu řetězce a jeho hashový kód spolu s názvem domény aplikace, ve které je metoda prováděna.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Pokud spustíte příklad bez zadání konfiguračního souboru, zobrazí se výstup podobný následujícímu. Všimněte si, že kódy hash pro řetězec jsou identické ve dvou doménách aplikace.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Pokud však do adresáře příkladu přidáte následující konfigurační soubor a poté spustíte příklad, kódy hash stejného řetězce se budou lišit podle aplikační domény.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Když je konfigurační soubor přítomen, v příkladu se zobrazí následující výstup:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
