---
title: Element <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2715548a40579375cebbdd5fb9003738a42ff714
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663654"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy> Element
Určuje, zda modul CLR (Common Language Runtime) umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.  
  
 \<> Konfigurace  
\<> modulu runtime  
\<legacyCorruptedStateExceptionsPolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že aplikace bude zachytávat chyby při výjimkách poškozených stavů, jako je například porušení přístupu.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Aplikace nebude zachytit nepoškozená selhání výjimek stavu, jako je například porušení přístupu. Toto nastavení je výchozí.|  
|`true`|Aplikace zachytí chyby výjimek nepoškozených stavů, jako je například porušení přístupu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 3,5 a starší používá modul common language runtime povolený spravovaný kód pro zachycení výjimek, které byly vyvolány poškozenými stavy procesu. Příkladem tohoto typu výjimky je porušení přístupu.  
  
 Počínaje .NET Framework 4 spravovaný kód již nezachycuje tyto typy výjimek v `catch` blocích. Tuto změnu však můžete přepsat a spravovat zpracování poškozených výjimek stavu dvěma způsoby:  
  
- `<legacyCorruptedStateExceptionsPolicy>` Nastavte atribut`enabled` elementu na `true`. Toto nastavení konfigurace se používá processwide a má vliv na všechny metody.  
  
 -nebo-  
  
- Použijte atribut na metodu, která obsahuje blok výjimek `catch`. <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>  
  
 Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že by se aplikace měla vrátit k chování před .NET Framework 4 a zachytit chyby výjimek všech poškozených stavů.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
