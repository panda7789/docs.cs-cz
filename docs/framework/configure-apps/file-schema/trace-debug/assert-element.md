---
title: "&lt;Assert –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 520dfec180157c9a05c5fc3beb51b5fc17f9088b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltassertgt-element"></a>&lt;Assert –&gt; – Element
Určuje, jestli se má zobrazit okno se zprávou při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zprávy.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<Assert – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`assertuienabled`|Nepovinný atribut.<br /><br /> Určuje, zda Pokud chcete zobrazit zprávu pole při **Debug.Assert –** vyhodnocen jako metoda **false**.|  
|`logfilename`|Nepovinný atribut.<br /><br /> Určuje název souboru pro zápis zprávy, když se **Debug.Assert –** vyhodnotí jako **false**.|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`true`|Zobrazí okno se zprávou. Toto nastavení je výchozí.|  
|`false`|Do pole zpráva nezobrazí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Oba atributy v  **\<assert >** element jsou volitelné. Okna zpráv můžete zakázat bez zadání souboru pro zápis zprávy, které mají, nebo můžete zadat soubor k zápisu zprávy do při opuštění zprávy polí povoleno.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat zobrazování okna zpráv při volání **Debug.Assert –** a zápis zpráv do `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Debug>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
