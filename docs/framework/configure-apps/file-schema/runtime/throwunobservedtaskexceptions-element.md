---
title: Element <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bc2bffa11c3205c265ca21a9d4c4caa9b31d4e9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281499"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Element
Určuje, zda úloh neošetřené výjimky by měla ukončit spuštěnému procesu.  
  
 \<Konfigurace >  
\<modul runtime >  
\<ThrowUnobservedTaskExceptions>  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda úloh neošetřené výjimky by měla ukončit spuštěný proces.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Spuštěný proces pro nezpracovaná výjimka úlohy nebyl ukončen. Toto nastavení je výchozí.|  
|`true`|Ukončí běžící proces pro nezpracovaná výjimka úlohy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Pokud výjimka, která je přidružena <xref:System.Threading.Tasks.Task> nebyla dodržena, neexistuje žádné <xref:System.Threading.Tasks.Task.Wait%2A> operace nadřazeného objektu není připojen a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nebyla načtena vlastnost výjimka úlohy se považuje za asynchronního nepozorovaného.  
  
 V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], pokud výchozí <xref:System.Threading.Tasks.Task> , který má asynchronního nepozorovaného výjimka je uvolněna, finalizační metoda vyvolá výjimku a ukončí proces. Ukončení procesu se určuje podle načasování uvolňování paměti a finalizace.  
  
 Aby bylo snazší pro vývojářům umožňuje psát asynchronní kód založený na úkolech, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] změní toto výchozí chování pro asynchronního nepozorovaného výjimky. Nepozorované výjimky způsobí <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> událost, ale ve výchozím nastavení, se proces neukončí. Místo toho výjimka bude ignorována, jakmile se vyvolá událost, bez ohledu na to, zda obslužná rutina události dodržuje výjimku.  
  
 V [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], můžete použít [ \<throwunobservedtaskexceptions – > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace umožňuje [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] chování vyvolání výjimky.  
  
 Můžete také určit chování výjimky v jednom z následujících způsobů:  
  
-   Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
-   Nastavením registru typu DWORD hodnota throwunobservedtaskexceptions – = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit vyvolání výjimek v úlohách pomocí konfiguračního souboru aplikace.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak je vyvolána nepozorovanou výjimku z úkolu. Kód musí běžet jako vydané program fungovat správně.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
