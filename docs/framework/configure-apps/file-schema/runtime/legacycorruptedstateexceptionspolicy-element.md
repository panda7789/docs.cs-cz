---
title: Element <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116461"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<element > legacyCorruptedStateExceptionsPolicy
Určuje, zda modul CLR (Common Language Runtime) umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy >**  
  
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
  
|Hodnota|Popis|  
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
  
 Počínaje .NET Framework 4 spravovaný kód již nezachycuje tyto typy výjimek v blocích `catch`. Tuto změnu však můžete přepsat a spravovat zpracování poškozených výjimek stavu dvěma způsoby:  
  
- Nastavte atribut `enabled` elementu `<legacyCorruptedStateExceptionsPolicy>` na hodnotu `true`. Toto nastavení konfigurace se používá processwide a má vliv na všechny metody.  
  
 -nebo-  
  
- Použijte atribut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> pro metodu, která obsahuje blok `catch` Exceptions.  
  
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
