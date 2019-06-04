---
title: Element <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4187d266d82783ebb72073c1da92faff95352884
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489378"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<shadowCopyVerifyByTimestamp> Element
Určuje, zda stínové kopírování sestavení použije výchozí chování při spuštění zavedené v rozhraní .NET Framework 4 nebo se vrátí do chování při spuštění z dřívějších verzích rozhraní .NET Framework.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<shadowCopyVerifyByTimestamp> Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Požadovaný atribut.<br /><br /> Určuje, zda porovnání aplikační domény, které používají stínové kopírování sestavení časová razítka při spuštění, chcete-li zjistit, zda sestavení byl aktualizován před stínové kopírování sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|true|Při spuštění zkopíruje pouze sestavení, které byly aktualizovány od posledního byly zkopírovány do adresáře stínové kopie. Toto je výchozí nastavení pro rozhraní .NET Framework 4.|  
|false|Vrátí chování při spuštění z předchozích verzí rozhraní .NET Framework, která byla zkopírujte všechny soubory při spuštění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework 4, sestavení jsou stínové kopie pouze v případě, že jejich časová razítka znamenat, že se změnily od posledního byly zkopírovány do adresáře stínové kopie. Tím se zlepšuje dobu spuštění pro mnoho aplikací, které používají stínové kopírování sestavení, jak je popsáno v [stínové kopírování sestavení](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Aplikace, které mají vysoké procento a četnosti aktualizací sestavení nemusí využívat tuto změnu v chování. V takovém případě můžete tento element obnovit chování z předchozích verzí rozhraní .NET Framework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínové kopírování v rozhraní .NET Framework 4 a vrátit se na chování při spuštění z předchozích verzí rozhraní .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Stínové kopírování sestavení](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
