---
title: "&lt;Userandomizedstringhashalgorithm –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7cd561cf0e0a9e080b150bdaa412686126423c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;Userandomizedstringhashalgorithm –&gt; – Element
Určuje, zda modul common language runtime vypočítá na kódů hash pro řetězce na základě domény aplikace.  
  
 \<Konfigurace >  
\<modul runtime >  
\<Userandomizedstringhashalgorithm – >  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda jsou na vypočteny kódů hash pro řetězce na základě domény aplikace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`0`|Modul common language runtime nepočítá na kódů hash pro řetězce na základě domény aplikace; jeden algoritmus se používá k výpočtu kódů hash řetězec. Toto nastavení je výchozí.|  
|`1`|Modul common language runtime vypočítá kódů hash pro řetězce na na základě domény aplikace. Identické řetězce v různých doménách aplikace a v různých procesů bude mít jiné hash – kódy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení <xref:System.StringComparer> třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda používat jeden algoritmus hash, která vytvoří hodnotu hash konzistentní napříč doménami aplikací. Jde o ekvivalent nastavení `enabled` atribut `<UseRandomizedStringHashAlgorithm>` element `0`. Toto je algoritmus hash, které jsou používány [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 <xref:System.StringComparer> Třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda můžete také použít jiný algoritmus hash, která vypočítá kódů hash na na základě domény aplikace. Hash – kódy pro ekvivalentní řetězce v důsledku toho budou lišit napříč doménami aplikací. Toto je funkce přihlášení; Chcete-li jej využít, musíte nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` element `1`.  
  
 Operace o(1), která je obvykle vyhledávací řetězec v zatřiďovací tabulku. Pokud dojde k velký počet kolizí, však může vyhledávání stát O (n<sup>2</sup>) operaci. Můžete použít `<UseRandomizedStringHashAlgorithm>` konfigurace element nevygeneruje náhodných algoritmu hash pro doménu aplikace, která zase omezuje počet potenciální kolize, zejména v případě, že jsou klíče, z nichž jsou vypočítávány kódů hash založené na vstupní data uživatelé.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje `DisplayString` třídu, která zahrnuje privátní řetězcová konstanta, `s`, jehož hodnota je "Toto je řetězec". Zahrnuje také `ShowStringHashCode` metoda, která zobrazuje hodnotu řetězce a jeho hodnota hash společně s název domény aplikace, ve kterém metoda provádí.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Když spustíte příklad bez zadávání konfiguračního souboru, zobrazí se výstup podobný následujícímu. Upozorňujeme, že kódů hash pro řetězec jsou identické v doménách dvě aplikace.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Ale pokud přidáte následující konfigurační soubor do adresáře v příkladu a spusťte v příkladu, kódů hash pro stejný řetězec budou lišit podle domény aplikace.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Pokud konfigurační soubor, v příkladu se zobrazí následující výstup:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
