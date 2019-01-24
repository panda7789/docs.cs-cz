---
title: '&lt;UseRandomizedStringHashAlgorithm&gt; Element'
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
ms.openlocfilehash: 3bb4286ea6055d2df9111b2222b137f2668bfdfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681037"
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;UseRandomizedStringHashAlgorithm&gt; Element
Určuje, zda modul common language runtime vypočítá hash kódy pro řetězce na základě domény aplikace.  
  
 \<Konfigurace >  
\<modul runtime >  
\<UseRandomizedStringHashAlgorithm >  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda kódy hash pro řetězce jsou vypočítány na základě domény aplikace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`0`|Modul common language runtime nepočítá kódy hash pro řetězce na základě domény aplikace; jeden algoritmus se používá k výpočtu řetězce kódů hash. Toto nastavení je výchozí.|  
|`1`|Modul common language runtime vypočítá hash kódy pro řetězce na základě domény aplikace. Shodné řetězce v různých aplikačních doménách a různých procesech budou mít různé hash kódy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení <xref:System.StringComparer> třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda používat jeden algoritmus hash, který generuje kód hash konzistentně napříč doménami aplikace. Jedná se o ekvivalent k nastavení `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu `0`. To je algoritmus hash, který je používán [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 <xref:System.StringComparer> Třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metodu můžete použít také jiný algoritmu hash, který vypočítává hash kódy na základě domény aplikace. V důsledku toho se kódy hash pro odpovídající řetězce budou lišit napříč doménami aplikace. To je přihlašovaná funkce; využívat jejich výhod, musíte nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu `1`.  
  
 Vyhledání řetězce v hashovací tabulce je obvykle operace O(1). Ale při výskytu velkého počtu kolizí vyhledávání může stát O (n<sup>2</sup>) operace. Můžete použít `<UseRandomizedStringHashAlgorithm>` element konfigurace ke generování náhodného algoritmu hash pro doménu aplikace, která zase omezuje počet potenciálních kolizí, zejména pokud klíče, z nichž se počítají hodnoty hash kódů jsou založeny na vstup dat uživatelé.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `DisplayString` třídu, která zahrnuje soukromou konstantu řetězce, `s`, jehož hodnota je "Toto je řetězec". Zahrnuje také `ShowStringHashCode` metodu, která zobrazí hodnotu řetězce a jeho kód hash spolu s názvem domény aplikace, ve kterém se metoda provádí.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Při spuštění příkladu bez poskytnutí konfiguračního souboru se zobrazí výstup podobný následujícímu. Všimněte si, že kódy hash pro řetězec jsou v obou aplikačních doménách identické.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Ale pokud přidáte následující konfigurační soubor do vzorového adresáře a spusťte příklad, hash kódy pro stejný řetězec budou lišit podle domény aplikace.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Pokud konfigurační soubor je k dispozici, příkladu se zobrazí následující výstup:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
