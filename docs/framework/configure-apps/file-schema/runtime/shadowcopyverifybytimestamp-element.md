---
title: "&lt;shadowCopyVerifyByTimestamp&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bae98c91c8a9b68ec7c21b142bc9f004c7bc1394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt; – Element
Určuje, jestli stínové kopírování sestavení používá výchozí chování při spouštění počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], nebo se vrátí do chování při spouštění starší verze rozhraní .NET Framework.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<shadowCopyVerifyByTimestamp > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, zda porovnat aplikační domény, které používají stínové kopírování sestavení časová razítka při zahájení, chcete-li zjistit, zda byly aktualizovány sestavení před stínové kopírování sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|true|Při spuštění zkopíruje pouze sestavení, které byly aktualizovány od posledního byly zkopírovány do adresáře stínové kopie. Toto je výchozí nastavení pro [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|Vrátí chování při spuštění z předchozí verze rozhraní .NET Framework, která byla kopírování všech souborů při spuštění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], sestavení jsou zkopírována jenom v případě jejich časová razítka naznačují, že se změnily od posledního byly zkopírovány do adresáře stínové kopie. To zlepší doba spuštění pro mnoho aplikací, které používají stínové kopírování sestavení, jak je popsáno v [stínové kopírování sestavení](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Aplikace, které mají vysoké procento a četnost aktualizací sestavení nemusí těžit z tuto změnu v chování. V takovém případě můžete tento prvek obnovit chování z předchozích verzí rozhraní .NET Framework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínové kopírování v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]a vrátit se k chování při spuštění z předchozí verze rozhraní .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Stínové kopírování sestavení](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
