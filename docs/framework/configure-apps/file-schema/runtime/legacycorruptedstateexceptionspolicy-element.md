---
title: Element <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6191ee2169a85725f0367763874e60c0ceb1d7a4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489430"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy> Element
Určuje, zda modul common language runtime umožňuje spravovanému kódu zachytit narušení přístupu a ostatní výjimky v poškozeném stavu.  
  
 \<Konfigurace >  
\<modul runtime >  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že aplikace zachytí poškozující stav výjimky selhání, jako je například porušení přístupu.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Aplikace nezachytí poškozující stav výjimky selhání, jako je například porušení přístupu. Toto nastavení je výchozí.|  
|`true`|Aplikace zachytí poškozující stav výjimky selhání, jako je například porušení přístupu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5 a starších povolený modul common language runtime spravovanému kódu zachytit výjimky, které byly vyvolány poškozená procesu státy. Narušení přístupu je příkladem tohoto typu výjimky.  
  
 Od verze rozhraní .NET Framework 4, spravovaný kód už zachycuje tyto typy výjimek v `catch` bloky. Můžete však přepsat tuto změnu a Udržovat zpracování výjimek v poškozeném stavu dvěma způsoby:  
  
- Nastavte `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atribut `true`. Toto nastavení je použité processwide a ovlivňuje všechny metody.  
  
 -nebo-  
  
- Použít <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atributu v metodě, která obsahuje výjimky `catch` bloku.  
  
 Tento prvek konfigurace je k dispozici pouze v rozhraní .NET Framework 4 a novější.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že aplikace by měla vrátit k chování před rozhraní .NET Framework 4 a zachytit všechny poskozeny stav výjimky selhání.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
