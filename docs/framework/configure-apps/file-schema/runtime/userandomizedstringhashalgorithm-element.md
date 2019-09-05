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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b53dcd4db7e0ac1e9079e763b8ed76c1088e0e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252202"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm – element >
Určuje, zda modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm>**  
  
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
  
|Value|Popis|  
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
 Ve výchozím nastavení <xref:System.StringComparer> třída <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> a metoda používají jeden algoritmus hash, který vytváří konzistentní kód hash napříč doménami aplikace. To je ekvivalentní nastavení `enabled` atributu `<UseRandomizedStringHashAlgorithm>` elementu na `0`. Toto je algoritmus hash používaný v .NET Framework 4.  
  
 <xref:System.StringComparer> Třída<xref:System.String.GetHashCode%2A?displayProperty=nameWithType> a metoda mohou také používat jiný algoritmus hash, který vypočítává kódy hash pro každou doménu aplikace. V důsledku toho se kódy hash pro ekvivalentní řetězce budou lišit napříč doménami aplikace. Toto je funkce výslovného souhlasu; Chcete-li jej využít, je nutné nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu na `1`.  
  
 Vyhledávání řetězců v zatřiďovací tabulce je obvykle operace O (1). Pokud ale dojde k velkému počtu kolizí, vyhledávání se může stát operací O (n<sup>2</sup>). Prvek `<UseRandomizedStringHashAlgorithm>` konfigurace lze použít k vygenerování náhodného algoritmu hash pro každou doménu aplikace, což zase omezuje počet potenciálních kolizí, zejména v případě, že klíče, ze kterých jsou počítány hodnoty hash, jsou založeny na vstupu dat podle uživatelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `DisplayString` třídu, která obsahuje soukromou řetězcovou `s`konstantu,, jejíž hodnota je "Toto je řetězec." Obsahuje `ShowStringHashCode` také metodu, která zobrazuje hodnotu řetězce a její kód hash spolu s názvem domény aplikace, ve které je metoda spuštěna.  
  
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
