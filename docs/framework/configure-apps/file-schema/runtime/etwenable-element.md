---
title: "&lt;etwenable –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b36c52338754df0f4fd3c963848e36afeb140501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwenablegt-element"></a>&lt;etwenable –&gt; – Element
Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro běžné události modulu runtime jazyka.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<etwEnabled >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, zda se má povolit trasování událostí pro Windows.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|true|Povolte trasování událostí pro Windows. Toto je výchozí hodnota pro verze systému Windows od verze operačních systémů Windows Vista a Windows Server 2008.|  
|false|Zakážete trasování událostí pro Windows. Toto je výchozí hodnota u starších verzí systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje Windows Vista, je ve výchozím nastavení povolené trasování událostí pro Windows. Pomocí tohoto elementu zakázat trasování pro aplikaci. V dřívějších verzích systému Windows tento prvek slouží k povolení trasování pro aplikaci.  
  
> [!NOTE]
>  Trasování událostí pro Windows můžete povolit nebo zakázat globálně na serveru pomocí nastavení registru. V tématu [řízení přihlašování rozhraní .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit trasování událostí pro Windows pro aplikaci.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Řízení přihlašování rozhraní .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
