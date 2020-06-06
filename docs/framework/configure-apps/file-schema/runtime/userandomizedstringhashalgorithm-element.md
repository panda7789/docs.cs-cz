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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153774"
---
# <a name="userandomizedstringhashalgorithm-element"></a>Element \<UseRandomizedStringHashAlgorithm>
Určuje, zda modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
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
  
|Hodnota|Description|  
|-----------|-----------------|  
|`0`|Modul CLR (Common Language Runtime) nepočítá kódy hash pro řetězce na základě domény aplikace. k výpočtu řetězcových kódů hash se používá jeden algoritmus. Toto nastavení je výchozí.|  
|`1`|Modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace. Identické řetězce v různých aplikačních doménách a v různých procesech budou mít různé kódy hash.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení <xref:System.StringComparer> Třída a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> Metoda používají jeden algoritmus hash, který vytváří konzistentní kód hash napříč doménami aplikace. To je ekvivalentní nastavení `enabled` atributu `<UseRandomizedStringHashAlgorithm>` elementu na `0` . Toto je algoritmus hash používaný v .NET Framework 4.  
  
 <xref:System.StringComparer>Třída a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> Metoda mohou také používat jiný algoritmus hash, který vypočítává kódy hash pro každou doménu aplikace. V důsledku toho se kódy hash pro ekvivalentní řetězce budou lišit napříč doménami aplikace. Toto je funkce výslovného souhlasu; Chcete-li jej využít, je nutné nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu na `1` .  
  
 Vyhledávání řetězců v zatřiďovací tabulce je obvykle operace O (1). Pokud ale dojde k velkému počtu kolizí, vyhledávání se může stát operací O (n<sup>2</sup>). Prvek konfigurace lze použít `<UseRandomizedStringHashAlgorithm>` k vygenerování náhodného algoritmu hash na doménu aplikace, který naopak omezuje počet potenciálních kolizí, zejména v případě, že klíče, ze kterých jsou počítány hodnoty hash, jsou založeny na vstupních datech uživatelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `DisplayString` třídu, která obsahuje soukromou řetězcovou konstantu, `s` , jejíž hodnota je "Toto je řetězec." Obsahuje také `ShowStringHashCode` metodu, která zobrazuje hodnotu řetězce a její kód hash spolu s názvem domény aplikace, ve které je metoda spuštěna.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Pokud spustíte příklad bez zadání konfiguračního souboru, zobrazí se výstup podobný následujícímu. Všimněte si, že kódy hash pro řetězec jsou identické ve dvou doménách aplikace.  
  
```console
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
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
