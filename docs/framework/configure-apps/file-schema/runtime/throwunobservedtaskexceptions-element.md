---
title: "&lt;Throwunobservedtaskexceptions –&gt; – Element"
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
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d171c2058a79476d99c5952cc6a697f126af81c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;Throwunobservedtaskexceptions –&gt; – Element
Určuje, zda úloha neošetřené výjimky by měl ukončit spuštěných procesů.  
  
 \<Konfigurace >  
\<modul runtime >  
\<Throwunobservedtaskexceptions – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda úloha neošetřené výjimky by měl ukončit běžící proces.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nezavře běžící proces pro úloh neošetřené výjimce. Toto nastavení je výchozí.|  
|`true`|Ukončí běžící proces pro úloh neošetřené výjimce.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Pokud výjimka, která je přidružena <xref:System.Threading.Tasks.Task> nebyla dodržena, není žádné <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený není připojený a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nebyla načtena vlastnost výjimku úlohy se považuje za zmeškané.  
  
 V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], pomocí výchozí, pokud <xref:System.Threading.Tasks.Task> má zmeškané výjimkou je uvolnění z paměti, finalizační metodu vyvolá výjimku a ukončit proces. Ukončení procesu je určen podle načasování uvolňování paměti a dokončení.  
  
 Aby bylo snazší pro vývojáře k zápisu asynchronní kódu založené na úlohy, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] změní toto výchozí chování pro zmeškané výjimky. Nepozorovaná výjimky způsobí <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> událost, která má být vyvolána, ale ve výchozím nastavení, není ukončit proces. Místo toho se výjimka ignoruje po událost se vyvolá, bez ohledu na to, jestli obslužná rutina události dodržuje výjimku.  
  
 V [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], můžete použít [ \<throwunobservedtaskexceptions – > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace, aby [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] chování došlo k výjimce.  
  
 Můžete také určit chování výjimka v jednom z následujících způsobů:  
  
-   Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
-   Nastavením registru DWORD hodnota throwunobservedtaskexceptions – = 1 v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit vyvolání výjimky v úlohách pomocí konfiguračního souboru aplikace.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak je vyvolána zmeškané výjimka z úlohy. Kód musí běžet jako vydaná program pracovat správně.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
